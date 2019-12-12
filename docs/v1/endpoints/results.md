---
layout: default
title: results
parent: Endpoints
grand_parent: v1
nav_order: 7
permalink: /v1/endpoints/results
---


### Downloading the results

- Copy the full JSON object containing the `QueryExecutionId`.
- Scroll down to the bottom of the page and open up the **GET /results** endpoint.
- Click the **Try it out** button and paste your QueryExecution blob in there and click **Execute**.

If the query is complete, you will get a response similar to:

```json
{
  "csv": "https://bazze.link/7856",
  "json": "https://bazze.link/1352",
  "kepler": "https://bazze.link/1c8d"
}
```

Each one of the links is the same data just in a different format.

- Click or copy-paste the csv link into a new tab in your browser to download the data.  The csv file can be opened with a text editor or Excel/Numbers.  The link is private but anyone you share the URL with will be able to download the data.