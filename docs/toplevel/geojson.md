---
layout: default
title: Using geoJSON
nav_order: 10
permalink: /getjson/
---

## Drawing polygons on geojson.io
Navigate to [http://geojson.io](http://geojson.io).

You should see a map and in the top right should see an icon for a polygon and square.  Choose either the polygon or square and draw as many shapes as you like.  Each shape that you draw will add to the "FeatureCollection" geoJSON object on the right hand size of the page.

You can also delete objects by clicking on the shape in the map and clicking **Delete feature**.  Additional fields can also be added to each shape by clicking the **+ Add row** button and adding key/value fields.

For example, you may want to name the area and add date restrictions to the query.  You might want to add something similar to this:

| key        | value            |
|------------|------------------|
| short_name | eiffel_tower     |
| from_date  | 2019-11-01       |
| to_date    | 2019-11-03       |

The `short_name` is important if you want to identify the polygon in the data after it is queried.

If you don't fill these fields out the query will fill in a number such as **feature_1** for the name, and will search for all dates. 