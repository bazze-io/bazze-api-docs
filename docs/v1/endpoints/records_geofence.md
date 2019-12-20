---
layout: default
title: records/geofence
parent: Endpoints
grand_parent: v1
nav_order: 3
permalink: /v1/endpoints/records_geofence
---


### /records/geofence - Getting location records by geofence
This endpoint allows you to retreive location data records by drawing polygons on a map.  This endpoint does an OR query, grabbing all location records that fall inside ANY of the polygons.

- Click the **POST /records/geofence** endpoint and click **Try it Out**.
- Set the `limit`, `from_date`, and `to_date` appropriately.  Note that the larger the date range the longer the query will take.
- If you would like to "wait" for the quert to finish and get a JSON response, set the `wait` paramter to **true**.  The results will look similar to the response of the /scrollResults endpoint.
- Scroll down to the request body and you should see a geoJSON object that contains coordinates, as well as other fields under **properties** such as `filters`, `from_date`, `to_date`, and `short_name`.
- You can try out query by using the sample geoJSON or you can add your own polygons by going to http://geojson.io and drawing them.  See the section "Drawing polygons on geojson.io" for instructions on how to use geojson.io.
- After you have drawn the polygons you want, copy and paste the "FeatureCollection" into the Request Body and hit **Execute**.
- Download the results as described in the "Downloading the results" section.