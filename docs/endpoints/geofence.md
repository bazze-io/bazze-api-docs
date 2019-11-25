---
layout: default
title: records/geofence
parent: Endpoints
nav_order: 3
permalink: /endpoints/geofence/
---


### /records/geofence - Getting location records by geofence
This endpoint allows you to retreive location data records by drawing polygons on a map.  This endpoint does an OR query, grabbing all location records that fall inside ANY of the polygons.

- Click the **POST /records/geofence** endpoint and click **Try it Out**.
- Set the `limit`, `from_date`, and `to_date` appropriately.  Note that the larger the date range the longer the query will take.
- Scroll down to the request body and you should see a geoJSON object that contains coordinates, as well as other fields under **properties** such as `filters`, `from_date`, `to_date`, and `short_name`.
- You can try out query by using the sample geoJSON or you can add your own polygons by going to http://geojson.io and drawing them.  See the section "Drawing polygons on geojson.io" for instructions on how to use geojson.io.
- After you have drawn the polygons you want, copy and paste the "FeatureCollection" into the Request Body and hit **Execute**.
- Download the results as described in the "Downloading the results" section.