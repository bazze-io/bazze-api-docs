---
layout: default
title: users/surveyall
parent: Endpoints
grand_parent: v1
nav_order: 6
permalink: /v1/endpoints/users_surveyall
---

### /users/surveyall - Tracking all users by geofence
This endpoint will return a survey of all the users that show up in at least N polygons.  For example, if N = 2, it will return a csv of advertising_ids, how many polygons they show up in, and which polygons they show up in.  The name for the polygon is pulled from the `short_name` field in the geoJSON object.

- Click the **POST /users/track** endpoint and click **Try it Out**
- Set the `limit` parameter.
- If you would like to "wait" for the quert to finish and get a JSON response, set the `wait` paramter to **true**.  The results will look similar to the response of the /scrollResults endpoint.
- Set the `polygons` parameter for deciding how many polygons the user has to show up in to be considered a match.
- You can try out query by using the sample geoJSON or you can add your own polygons by going to https://geojson.io and drawing them.  See the section "Drawing polygons on geojson.io" for instructions on how to use geojson.io.
- As of version 1.1.0, you can use an MGRS coordinate instead of a polygon.  In the geoJSON object, change the `"type": "polygon"` to `"type": "MGRS"` and add a `"coordinate": "mgrs_coordinate_goes_here"` to the object.  The `"coordinate"` field is not required for MGRS.  Also - if you have both a "polygon" and an "MGRS" type, the MGRS coordinate will take presendence.  
- After you have drawn the polygons you want, copy and paste the "FeatureCollection" into the Request Body and hit **Execute**.
- Download the results as described in the "Downloading the results" section.