---
layout: default
title: unsubscribe
parent: Endpoints
grand_parent: v1
nav_order: 13
permalink: /v1/endpoints/unsubscribe
---

### Unsubscribing from an https url

This endpoint allows you to unsubscribe from a previously confirmed https endpoint.  Note that if you try to unsubscribe from a url that has NOT been confirmed you will get an error message.  If you need to re-send the SubscriptionConfirmation just submit the `callbackUrl` again to the /subscribe endpoint.

To disable a webhook subscription:

- Submit a POST request to /v1/unsubscribe with the `callbackUrl` as the only key in the body.
- If it is successful, you receive a 200 response code.