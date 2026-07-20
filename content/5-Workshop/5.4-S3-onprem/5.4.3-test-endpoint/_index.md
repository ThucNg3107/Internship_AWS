---
title : "Verify the public magazine and article reader"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.4.3 </b> "
---

Open the production site:

[https://d3u5pkyxnd3uus.cloudfront.net/](https://d3u5pkyxnd3uus.cloudfront.net/)

#### Public behavior

- **The magazine is readable without an account.**
- **Article cards use the processed CloudFront WebP URL returned by the API.**
- **A reader can open full cleaned article text, the generated summary, source attribution, and the original publisher link.**
- **Login is required only for likes and comments.**
- **The operations page uses a separate admin session and never embeds the admin API key.**

![article-reader](/images/5-Workshop/5.4-S3-onprem/article-reader.png)

#### Real article evidence

Browser test opened a real Hacker News article, displaying cleaned full text, summary, source URL, processed cover image, and reader discussion controls. Checked on desktop and mobile without horizontal overflow.

#### Frontend/API boundary

Frontend does not download or convert publisher images. Frontend receives only the final `imageUrl` from the API. File validation, resize, conversion, S3 upload, and CDN URL are backend worker responsibilities.
