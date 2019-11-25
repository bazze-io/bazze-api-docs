---
layout: default
title: users/surveyall
parent: Endpoints
nav_order: 5
permalink: /endpoints/surveyall/
---

### /users/surveyall - Tracking all users by geofence
This endpoint will return a survey of all the users that show up in at least N polygons.  For example, if N = 2, it will return a csv of advertising_ids, how many polygons they show up in, and which polygons they show up in.  The name for the polygon is pulled from the `short_name` field in the geoJSON object.

- Click the **POST /users/track** endpoint and click **Try it Out**
- Set the `limit` parameter.
- Set the `polygons` parameter for deciding how many polygons the user has to show up in to be considered a match.
- You can try out query by using the sample geoJSON or you can add your own polygons by going to https://geojson.io and drawing them.  See the section "Drawing polygons on geojson.io" for instructions on how to use geojson.io.
- After you have drawn the polygons you want, copy and paste the "FeatureCollection" into the Request Body and hit **Execute**.
- Download the results as described in the "Downloading the results" section.