<!-- ---
layout: default
title: Data availability
nav_order: 3
parent: v1
permalink: /v1/data_availability/
---

## A note about data availability

**Data Availability can be found at the /stats/daterange endpoint**


Every endpoint that queries data has 3 parameters that limit the data that is scanned and the data that is returned in the form of csv or json.  The reason that the `from_date` and `to_date` are required is so that we only scan for the data that we need.  Otherwise, every query would take very long and get costly. The parameters are:

- `limit`:   This limits how many lines are returned in the csv or json file.  This does NOT affect how much data is scanned on the back-end.  If you want all matching records, fill in **ALL** for this parameter.
- `from_date`: The left bound of the date to search for data.  Accepts a ISO date or ISO date-time.  2019-11-12, 2019-11-12 14:44:33 are valid examples.
- `to_date`:  The right bound of the date to search for data.  Accepts a ISO date or ISO date-time.  2019-11-12, 2019-11-12 14:44:33 are valid examples. -->