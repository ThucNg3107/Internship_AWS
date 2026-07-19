---
title : "Verify public magazine and article reader"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.4.3 </b> "
---

Open production site:

[https://d3u5pkyxnd3uus.cloudfront.net/](https://d3u5pkyxnd3uus.cloudfront.net/)

#### Public behavior

- Magazine can be read without an account.
- Article card uses processed CloudFront WebP URL returned by API.
- Reader can open full cleaned article text, generated summary, source attribution, and original publisher link.
- Only like and comment require login.
- Operations page uses dedicated admin session and does not embed admin API key.

![Article Reader](/images/5-Workshop/5.4-S3-onprem/article-reader.png)

#### Real article evidence

Browser test opened a real Hacker News article, displaying cleaned full text, summary, source URL, processed cover image, and reader discussion controls. Checked on desktop and mobile without horizontal overflow.

#### Frontend/API boundary

Frontend does not download or convert publisher images. Frontend receives only the final `imageUrl` from the API. File validation, resize, conversion, S3 upload, and CDN URL are backend worker responsibilities.
