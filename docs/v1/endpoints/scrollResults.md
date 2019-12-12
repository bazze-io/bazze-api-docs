---
layout: default
title: scrollResults
parent: Endpoints
grand_parent: v1
nav_order: 8
permalink: /v1/endpoints/scrollresults
---


### Scrolling the results
This endpoint lets you paginate the data as JSON objects rather than downloading the results like the /results endpoint.


- Copy the full JSON object containing the `QueryExecutionId`.
- Scroll down to the bottom of the page and open up the **GET /scrollResults** endpoint.
- Add the `QueryExecutionId`.
- Set the `MaxResuts` field if you wish.
- Set the `NextToken` only if you are paginating the results.  You don't need this on your initial query.

- Click the **Try it out** button and paste your QueryExecution blob in there and click **Execute**.

If the query is complete, you will get a response similar to:

```json
{
  "NextToken": "AUB1qOPL1oO2n7lcC3CiANqHsPRIcPwUhK5yFlcVs+Sq20SUJ7DJqbvbF3N9TikGKCLWqRn4IrwZSmVc6K7MCvB/9ooRt5bDnw==",
  "results": [
    {}
  ]
}
```

Note that there will only be a `NextToken` object if the results don't fit into that particular result.  You can "scroll results" by setting up a loop and continue calling this endpoint until all of the results are retrieved.