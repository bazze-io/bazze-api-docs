---
layout: default
title: records/users
parent: Endpoints
grand_parent: v1
nav_order: 4
permalink: /v1/endpoints/records_users
---

### /records/users - Getting location records by users (advertising_id's)
This endpoint allows you to pull records by providing an array of advertising_ids.  This is especially useful when combined with the /users/survey and /users/surveyall endpoints.

- Click on the **GET /records/users** endpoint and then on the **Try it out** button. 
- Add a list of advertising_id's that you would like to grab records for.  For example:

```json
[
  {
    "advertising_id": "496DC9DB-0E91-4C7B-9A40-9A454E759D76"
  },
  {
    "advertising_id": "B144E657-D730-43D6-9276-B8DDEA98F94E"
  }
]
```

- Set the `limit` and the `to_date`, `from_date` parameters.
- If you would like to "wait" for the quert to finish and get a JSON response, set the `wait` paramter to **true**.  The results will look similar to the response of the /scrollResults endpoint.
- Click the **Execute** button and scroll down to the section labeled **Response Body**.  You should see something similar to the following below.  Note that your `QueryExecutionId` will be different since every query execution is unique.

```json
{
  "QueryExecutionId": "ca75faf4-a545-4417-9bf2-65a913c0ecf4"
}
```

This `QueryExecutionId` is what you will need to retrieve the results of the query.  Depending on the query, it can take 30 seconds or many minutes.