---
layout: default
title: subscribe
parent: Endpoints
grand_parent: v1
nav_order: 12
permalink: /v1/endpoints/subscribe
---

### Enabling and confirming a subscription

This endpoint allows you to receive notifications via a https webhook when a query has completed.  Before receiving notifications to the webhook, you will need to verify that the webhook.

To enable a webhook:

- Submit a POST request to /v1/subscribe with the `callbackUrl` as the only key in the body.
- Once the API receives this, it will send out a POST request to the `callbackUrl` with information about the subscription.
- Your Application needs to listen for this and respond appropriately.  Look for this header: `x-amz-sns-message-type: SubscriptionConfirmation`.  If you see that header, the body will contain the `Token` key in the JSON object.
- Your application should then respond back to the same /v1/subscribe endpoint with a POST request containing the token.  For example if your token was "123456", then respond with  `{"token": "123456"}`.

The following python code could be used to request and then confirm a subscription to https://example.com/callback

```python
import json
import requests

# Headers and URLs
headers = {'x-api-key': 'secret', 'Content-Type': 'application/json'}
callback_url = 'https://example.com/callback'
subscribe_url = 'https://api.bazze.io/v1/subscribe'

# Send the request for subscription
requests.post(subscribe_url, json={'callbackUrl': callback_url}, headers=headers)

# At some later point, confirm the subscription
# The 'request' object here is the request coming from api.bazze.io.  You Application needs to listen for this.
# The content-type is text/plain.  But its JSON under the hood.
obj = json.loads(request.raw_body.decode('utf-8'))
# Check the header
if request.headers.get('x-amz-sns-message-type') == 'SubscriptionConfirmation':
    # Respond with a POST containing just the {'token': Token} from the received message
    requests.post(subscribe_url, json={'token': obj['Token']}, headers=headers)
```

For more information about the headers and the body response, check out the [AWS documentation](https://docs.aws.amazon.com/sns/latest/dg/sns-message-and-json-formats.html#http-header)


### Subscription webhook notifications
The webhook only receives notifications from endpoints that involve running a query.  For example, the /records or /survey endpoints.  Using other endpoints such as /results do not generate any webhook notifications.  For example, if you use the /records endpoint using `wait=false`, you will get a response back within a few seconds like:

```
{"QueryExecutionId": "694e7d20-076a-404a-8adf-d5c58a194a09"}
```

When the query is complete, there will be a POST request sent to your webhook that looks similar to this:

```
{
  "status": "SUCCEEDED",
  "QueryExecutionId": "694e7d20-076a-404a-8adf-d5c58a194a09",
  "time_completed": "2020-01-17 22:04:24.089113"
}
```

When you receive this message, you can then hit the /results endpoint or /scrollResults to pull the data.


### Failed queries
At this time, the subscriptions only notify you when a query has succeeded.  If a query fails after it has started execution, there will not be a notification.  However you can check the status of queries using the /queries endpoint or by using the /results endpoint.
