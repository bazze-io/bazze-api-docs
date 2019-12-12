---
layout: default
title: stats/counts
parent: Endpoints
grand_parent: v1
nav_order: 11
permalink: /v1/endpoints/stats_counts
---

### /stats/counts - Get a count of unique objects
This endpoint allows you to get exact or approximate counts of unique objects.

- Set the `approx` parameter to `true` for fast results, or `false`, for exact results.  If set to approimate, the results will have a 2% error tolerance.
- Set the `to_date` and `from_date`
- Optionally include any filter paratmers.
- Click the **Execute** button and you should get results similar to the following:

```json
{
  "advertising_ids": 1205555,
  "ip_addresses": 2163332,
  "wifi_bssids": 1107993,
  "wifi_ssids": 665445
}
```