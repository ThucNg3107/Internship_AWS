---
title: "Blog 1: Improving Order History Search"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Improving Order History Search with Semantic Search using Amazon OpenSearch Service

If you've ever shopped on Amazon, you're likely familiar with the **Your Orders** page. This feature stores the complete shopping history of customers dating back to 1995, allowing you to track, search, and manage every past transaction. The order history search tool makes it easy to find previously purchased items by typing keywords. Beyond search, it also provides a quick way to reorder past products, saving customers significant time and effort.

Many of Amazon's core features in the shopping experience (such as the AI shopping assistant Rufus and the voice assistant Alexa) rely on the order history search tool to help users locate past transactions. As a result, ensuring the accuracy, intuitiveness, and speed of this search system is critically important.

This article details how the **Your Orders** development team at Amazon improved the customer experience by incorporating semantic search capabilities into the existing lexical search system, using **Amazon OpenSearch Service** and **Amazon SageMaker**.

---

## Limitations of Lexical Search

Previously, order history search relied primarily on **lexical matching** (keyword matching). This mechanism returns items containing at least one of the search keywords. For example, when a customer searches for *"orange juice"*, the system retrieves all orange juice, fresh oranges, or other fruit drinks the customer has previously ordered.

While keyword search is highly effective for exact text matches, it reveals significant limitations:

- **No understanding of synonyms & semantics:** The system cannot handle conceptual or descriptive keywords. For example, a query like *"healthy drinks"* will not return results for *"kombucha"*, *"green tea"*, or *"protein milk"* if those specific keywords don't appear in the product title or description.
- **Conversational queries:** With the launch of Rufus – Amazon's integrated AI shopping assistant – users tend to search more naturally, such as *"Show me healthy drinks I bought last year"*. To handle this, the underlying system must understand the deeper meaning of queries rather than just matching text literally.

---

## Technical Challenges When Deploying at Scale

Deploying semantic search for a system at Amazon's scale comes with enormous technical barriers:

1. **Massive Scale:** The system must support semantic search across billions of order history records from customers worldwide.
2. **Zero Downtime:** The system must maintain 100% availability and meet strict service level agreement (SLA) commitments throughout database upgrades and migrations.
3. **Avoiding Search Quality Degradation:** Semantic search aims to improve result quality, but in some cases it can backfire. For example:
   - When a customer remembers the exact product name and wants to find that specific item, semantic search will surface similar or related products, diluting the results and frustrating the user.
   - Semantic search is completely ineffective for identifier-based searches (such as searching by **Order ID**), as there is no semantic meaning involved. In these situations, the system must fall back to regular keyword search.

---

## Solution Architecture Overview

Semantic search is powered by **Large Language Models (LLMs)**. These models can take a piece of text (such as a customer's search phrase or a product description) and convert it into a fixed-length sequence of numbers called an **embedding vector**. These vectors encode the semantic meaning of the text; two texts with similar content will have a very high cosine similarity score between their corresponding vectors.

Amazon's solution is divided into two major architectural components:

1. **System Scalability:** Transitioning to a cell-based architecture to optimize the processing of resource-intensive vector workloads.
2. **Semantic Pipeline:** Building a pipeline for generating, storing, and retrieving embedding vectors.

![Figure 1. Cell-based architecture diagram showing how customer requests are routed to Amazon OpenSearch Service domains via hash-based partitioning](/images/3-BlogsTranslated/Cell-based-arch-blog.png)

*Figure 1. Cell-based architecture diagram showing how customer requests are routed to Amazon OpenSearch Service domains via hash-based partitioning*

---

## Scalability and Load Handling: Cell-Based Architecture



To handle the increasing computational load from vector comparisons, the development team adopted a **cell-based architecture** design pattern. This architecture breaks down the entire system into independent, identical blocks called **cells**, where each cell is responsible for processing only a portion of the traffic.

- **Customer partitioning:** Each cell serves a specific group of customers. Cells operate completely independently and do not need to communicate with each other when processing requests.
- **Routing mechanism:** Customer requests are routed to their corresponding cell at runtime. Cell assignment information can be computed dynamically or retrieved from a cache/data store such as **Amazon DynamoDB**. This makes redistributing data across cells extremely flexible when there is local overload.
- **High durability:** If one cell fails, the system's serving capacity is only reduced by $1/N$ (where $N$ is the number of cells) rather than a complete system failure. Partition keys can also be mapped to two or more cells for data replication, eliminating the risk of data loss.


---

## Semantic Search Deployment

The process of integrating semantic search requires important decisions about infrastructure and model selection:

![Figure 2. Read-flow and write-flow for semantic search using Amazon OpenSearch Service and embedding vectors from Amazon SageMaker](/images/3-BlogsTranslated/SageMakerFlow.png)

*Figure 2. Read-flow and write-flow for semantic search using Amazon OpenSearch Service and embedding vectors from Amazon SageMaker*

### 1. Model Evaluation & Selection

The development team used an embedding model trained specifically on Amazon's e-commerce data. Domain-specific training helps the model deeply understand product terminology and business context.

To find the best model, they used the **LLM-as-a-judge** approach with Anthropic's Claude on **Amazon Bedrock**. Claude received prompts containing ordered product content and real customer search queries, then ranked and classified them against a ground truth relevance dataset. Candidate models were evaluated using standard ranking metrics:

- **Normalized Discounted Cumulative Gain (NDCG):** Measures ranking quality.
- **Mean Reciprocal Rank (MRR):** Considers the position of the first relevant result.
- **Precision & Recall:** Evaluates accuracy and coverage of results.

### 2. Infrastructure Deployment

The selected embedding model was then containerized, registered in **Amazon Elastic Container Registry (Amazon ECR)**, and deployed via **Amazon SageMaker Inference Endpoints** to handle large-scale vector computation with low latency.

### 3. Vector Storage & Search with OpenSearch Service

The system leverages two powerful features of **Amazon OpenSearch Service**:

- **`knn_vector` data type:** Supports direct storage of embedding vectors. Since the number of orders per customer is relatively small, the team chose **exact k-NN search** over approximate k-NN. This allows the system to achieve maximum accuracy while still maintaining performance.
- **Scripted Scoring:** Uses Painless scripts to compute vector similarity directly on the OpenSearch server, minimizing client-side complexity and maintaining extremely low latency.

---

## Hybrid Search: Combining Keyword & Semantic Search

To optimize search results, Amazon deployed a **Hybrid Search** model. OpenSearch Service's hybrid query feature runs both keyword (BM25) and semantic (vector) queries in parallel.

```
graph TD
  Query[Customer search query] --> Lexical[BM25 Keyword Search]
  Query --> Semantic[Semantic Vector Search]
  Lexical --> Merge[Merge & normalize scores]
  Semantic --> Merge
  Merge --> Sort[Sort by relevance]
  Sort --> Results[Top K final results]
```

- **Parallel execution:** Both query types run simultaneously.
- **Score normalization:** OpenSearch automatically merges and normalizes scores from both search streams.
- **Fallback mechanism:** For queries without semantic meaning (such as searching by `Order ID`), the system automatically skips semantic search and uses only keyword matching.
- **Reliability:** If the semantic search stream encounters an error, the system automatically falls back to keyword search results, ensuring results are always returned instead of a blank error page.

---

## Backfilling: Processing Historical Order Data

For semantic search to be truly useful, billions of historical order records need to be supplemented with their corresponding embedding vectors.

The team designed a large-scale data processing pipeline using:

- **AWS Step Functions** to orchestrate the entire backfill workflow across batches of data.
- **AWS Lambda** to process data batches and call SageMaker endpoints to generate embedding vectors.
- This pipeline successfully processed billions of records at speeds far exceeding normal data ingestion rates, demonstrating OpenSearch Service's ability to scale under heavy load.

---

## Real-world Impact and Customer Experience

Deploying semantic search delivered significant improvements in both user experience and business metrics:

- **More intuitive shopping experience:** Customers can now search for *"sustainable watch"* to find relevant products, or type *"charger"* to surface adapters and cables, even if the product title doesn't contain that exact word.
- **10% improvement in Query Recall:** Significantly increased the rate at which searches surface the products customers actually want.
- **20% increase in search success rate:** More customer searches now return at least one relevant product.
- **49% expansion in Result Coverage:** Semantic search continuously discovers and surfaces products that traditional keyword search would miss.
- **Powerful support for Rufus and Alexa:** Helps AI assistants easily retrieve order history information to answer complex questions from users.

---

## Conclusion

By incorporating semantic search into Amazon's order history, the development team successfully combined cutting-edge AI technology with large-scale traditional infrastructure. With **Amazon OpenSearch Service** and **Amazon SageMaker**, this solution not only maintains excellent availability but also opens new directions for personalization features and multi-modal search in the future.

To start building your own semantic search application, you can refer to:

- [Exact k-NN search in OpenSearch](https://docs.opensearch.org/latest/vector-search/vector-search-techniques/knn-score-script/)
- [Amazon OpenSearch Service Developer Guide](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/gsg.html)
