## Getting started with the Bazze API

https://api.bazze.io

There are many different ways to use the API.  Most of the time, API's are used by developers as an "integration point" for an application.  API's can also be used on their own for testing and to see what the raw responses look like without the larger application.

There are a few different ways to test out the API.  For example, you can use:

- Command line utilities such as `curl`
- Programming languages such as _Python_ or _Javascript_
- Graphical interfaces such as _Insomnia_ or _Postman_
- The built in Swagger Web Page.

The **Swagger Web Page** is the easiest way to get started since it requires no additional software or programming skills.  Once comfortable with the web page, we recommend switching to a more powerful graphical tool such as _Insomnia_.  

This guide focuses on getting started using the **Swagger Web Page**.

### Getting Authorized

- Click the "Authorize" button in the top right corner of the page and enter our API Key in the pop-up, then click **Authorize**.  At this point the lock symbols on the page should be closed letting you know you are authorized for access.

Each of the lines with GET, POST, PUT, or DELETE in front of it is an _endpoint_.  Each _endpoint_ performs a specific action on the API.

For example, the first endpoint on the page is `/hello`.  This is a simple test endpoint just to check that the API is working and that you are authorized.

### The /hello endpoint

- Click on the GET /hello endpoint and then on the **Try it out** button.  Then click the blue button that says **Execute**.  It will load for a second or two and then complete.  Scroll down to the section labeled **Response Body** and you should see the response from the API:

```json
{
  "Hello": "Swagger!"
}
```

- Click the top of the GET /hello drop down to minimize it after you are done.

### A note about querying data

#### Sample data is only available for July (07) and October (10) through November (11) 5th.


Every endpoint that queries data has 3 parameters that limit the data that is scanned and the data that is returned in the form of csv or json.  The reason that the `from_date` and `to_date` are required is so that we only scan for the data that we need.  Otherwise, every query would take very long and get costly. The parameters are:

- `limit`:   This limits how many lines are returned in the csv or json file.  This does NOT affect how much data is scanned on the back-end.  If you want all matching records, fill in **ALL** for this parameter.
- `from_date`: The left bound of the date to search for data.  Must be in the format YYYY-MM-DD.
- `to_date`:  The right bound of the date to search for data.  Must be in the format YYYY-MM-DD.

### /records - Getting location records by query parameters
The most simple query to perform is the `/records` endpoint.  This will run a query of the mobile location data.

- Click on the **GET /records** endpoint and then on the **Try it out** button.  
- Set the `limit` parameter.
- Set the filter parameters. Be aware that the filter is an AND query meaning that the data will have to match everything in these parameters for a result to be returned.
- Click the **Execute** button and scroll down to the section labeled **Response Body**.  You should see something similar to the following below.  Note that your `QueryExecutionId` will be different since every query execution is unique.

```json
{
  "QueryExecutionId": "ca75faf4-a545-4417-9bf2-65a913c0ecf4"
}
```

This `QueryExecutionId` is what you will need to retrieve the results of the query.  Depending on the query, it can take 30 seconds or many minutes.

### Downloading the results

- Copy the full JSON object containing the `QueryExecutionId`.
- Scroll down to the bottom of the page and open up the **GET /results** endpoint.
- Click the **Try it out** button and paste your QueryExecution blob in there and click **Execute**.

If the query is complete, you will get a response similar to:

```json
{
  "csv": "https://bazze.link/7856",
  "json": "https://bazze.link/1352",
  "kepler": "https://bazze.link/1c8d"
}
```

Each one of the links is the same data just in a different format.

- Click or copy-paste the csv link into a new tab in your browser to download the data.  The csv file can be opened with a text editor or Excel/Numbers.  The link is private but anyone you share the URL with will be able to download the data.


### /records/geofence - Getting location records by geofence
This endpoint allows you to retreive location data records by drawing polygons on a map.  This endpoint does an OR query, grabbing all location records that fall inside ANY of the polygons.

- Click the **POST /records/geofence** endpoint and click **Try it Out**.
- Set the `limit`, `from_date`, and `to_date` appropriately.  Note that the larger the date range the longer the query will take.
- Scroll down to the request body and you should see a geoJSON object that contains coordinates, as well as other fields under **properties** such as `filters`, `from_date`, `to_date`, and `short_name`.
- You can try out query by using the sample geoJSON or you can add your own polygons by going to http://geojson.io and drawing them.  See the section "Drawing polygons on geojson.io" for instructions on how to use geojson.io.
- After you have drawn the polygons you want, copy and paste the "FeatureCollection" into the Request Body and hit **Execute**.
- Download the results as described in the "Downloading the results" section.

### /users/survey - Tracking user overlap by geofence
This endpoint will return users that show up in ALL of the polygons (with dates) that you add to the geoJSON object.  Note that the more polygons you add to this the less likely you will get many results, because the user has to show up in EVERY polygon to be considered a result.

- Click the **POST /users/track** endpoint and click **Try it Out**
- Set the `limit` paramter.
- You can try out query by using the sample geoJSON or you can add your own polygons by going to https://geojson.io and drawing them.  See the section "Drawing polygons on geojson.io" for instructions on how to use geojson.io.
- After you have drawn the polygons you want, copy and paste the "FeatureCollection" into the Request Body and hit **Execute**.
- Download the results as described in the "Downloading the results" section.

### /users/surveyall - Tracking all users by geofence
This endpoint will return a survey of all the users that show up in at least N polygons.  For example, if N = 2, it will return a csv of advertising_ids, how many polygons they show up in, and which polygons they show up in.  The name for the polygon is pulled from the `short_name` field in the geoJSON object.

- Click the **POST /users/track** endpoint and click **Try it Out**
- Set the `limit` parameter.
- Set the `polygons` parameter for deciding how many polygons the user has to show up in to be considered a match.
- You can try out query by using the sample geoJSON or you can add your own polygons by going to https://geojson.io and drawing them.  See the section "Drawing polygons on geojson.io" for instructions on how to use geojson.io.
- After you have drawn the polygons you want, copy and paste the "FeatureCollection" into the Request Body and hit **Execute**.
- Download the results as described in the "Downloading the results" section.

### /queries - Check your query history
This endpoint allows you to check your query history and filter by status.

- Set the `state` parameter, options are available in the dropdown.
- The results will be available in the **Response body** below.


### Drawing polygons on geojson.io
Navigate to http://geojson.io.

You should see a map and in the top right should see an icon for a polygon and square.  Choose either the polygon or square and draw as many shapes as you like.  Each shape that you draw will add to the "FeatureCollection" geoJSON object on the right hand size of the page.

You can also delete objects by clicking on the shape in the map and clicking **Delete feature**.  Additional fields can also be added to each shape by clicking the **+ Add row** button and adding key/value fields.

For example, you may want to name the area and add date restrictions to the query.  You might want to add something similar to this:

| key        | value            |
|------------|------------------|
| short_name | kgb_headquarters |
| from_date  | 2019-11-01       |
| to_date    | 2019-11-03       |

The `short_name` is important if you want to identify the polygon in the data after it is queried.

If you don't fill these fields out the query will fill in a number such as **feature_1** for the name, and will search for all dates. 

