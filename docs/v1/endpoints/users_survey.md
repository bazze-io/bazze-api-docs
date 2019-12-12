---
layout: default
title: users/survey
parent: Endpoints
grand_parent: v1
nav_order: 5
permalink: /v1/endpoints/users_survey
---


### /users/survey - Tracking user overlap by geofence
This endpoint will return users that show up in ALL of the polygons (with dates) that you add to the geoJSON object.  Note that the more polygons you add to this the less likely you will get many results, because the user has to show up in EVERY polygon to be considered a result.

- Click the **POST /users/track** endpoint and click **Try it Out**
- Set the `limit` paramter.
- You can try out query by using the sample geoJSON or you can add your own polygons by going to https://geojson.io and drawing them.  See the section "Drawing polygons on geojson.io" for instructions on how to use geojson.io.
- As of version 1.1.0, you can use an MGRS coordinate instead of a polygon.  In the geoJSON object, change the `"type": "polygon"` to `"type": "MGRS"` and add a `"coordinate": "mgrs_coordinate_goes_here"` to the object.  The `"coordinate"` field is not required for MGRS.  Also - if you have both a "polygon" and an "MGRS" type, the MGRS coordinate will take presendence.  
- After you have drawn the polygons you want, copy and paste the "FeatureCollection" into the Request Body and hit **Execute**.
- Download the results as described in the "Downloading the results" section.