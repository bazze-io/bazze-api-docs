---
layout: default
title: records
parent: Endpoints
grand_parent: v1
nav_order: 2
permalink: /v1/endpoints/records
---

### /records - Getting location records by query parameters
The most simple query to perform is the `/records` endpoint.  This will run a query of the mobile location data.

- Click on the **GET /records** endpoint and then on the **Try it out** button.  
- Set the `limit` parameter.
- Set the filter parameters. Be aware that the filter is an AND query meaning that the data will have to match everything in these parameters for a result to be returned.
- Click the **Execute** button and scroll down to the section labeled **Response Body**.  You should see something similar to the following below.  Note that your `QueryExecutionId` will be different since every query execution is unique.

```json
{
  "QueryExecutionId": "ca75faf4-a545-4417-9bf2-65a913c0ecf4"
}
```

This `QueryExecutionId` is what you will need to retrieve the results of the query.  Depending on the query, it can take 30 seconds or many minutes.