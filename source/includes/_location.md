#Location

## URLs

|URL | Supported HTTP verbs| Action
|:----------|:-------|:-------------|
|/api/location| GET | Get Root Location|
|/api/location/{*parentLocationId*} |POST| Create new location under a given parent location|
|/api/location/{*locationId*} | GET, PUT, DELETE| Create, read, update, delete a location respectively|
|/api/location/{*locationId*}/gateways| GET| Get all gateways at a location|
|/api/location/{*locationId*}/devices| GET| Get all devices at a location|

### Location Resource Description
| Name | Type | Description | Required | Default|
|:----------|:-----|:------------|:-----|:-------|
|_id|String| Unique ID of location| Auto-Generated|-|
|name|String| Name of location| Yes|-|
|type|Enum {BUILDING, INDOOR}| If the location is a building or an indoor location inside a building. If this location is a building, then geoLoc should be set| No | -|
|test | Boolean| If set to true, then the location is not visible in tree| No | False|
|geo_loc.type | String| Type of geo-location : Point, Line etc| No| Point|
|geo_loc.coordinates|Number| Coordinates are in format [longitude, latitude]| No| -| 
|children| Array | Pointer to child locations is maintained by database and returned in GET request|No | -|


## Create new Location 

```http
POST /api/location/582e2b2c065b2545ded3aabd HTTP/1.1
{
  "name":"CIC",
  "type":"BUILDING",
    "geoLoc": {
      "coordinates": [
        40.4509146,
        -79.9024777
      ]     
    }    
}
```

> The above command returns JSON structured like this:

```json
{
    "_id": "5833479babdafd7b34858958",
    "name": "CIC",
    "test": false,
    "type":"BUILDING"
    "children": [
     {}
    ],
    "geoLoc": {
      "coordinates": [
        40.4509146,
        -79.9024777
      ],
      "type": "Point"
    }
}
```
### HTTP Request

`POST /api/location/<parentLocationId>`

### URL Parameters

Parameter | Description
--------- | -----------
 parentLocationId | ID of parent location

### Request body

| Name | Type | Description | Required | Default|
|:----------|:-----|:------------|:-----|:-------|
|name|String| Name of location| Yes|-|
|type|Enum {BUILDING, INDOOR}| If the location is a building or an indoor location inside a building. If this location is a building, then geoLoc should be set| No | -|
|test | Boolean| If set to true, then the location is not visible in tree| No | False|
|geo_loc.type | String| Type of geo-location : Point, Line etc| No| Point|
|geo_loc.coordinates|Number| Coordinates are in format [longitude, latitude]| No| -|



## Get details of a location

`GET /api/location/<locationID>`

### URL Parameters
	* locationId (string) - ID of location to get.

```http
GET /api/location/582e2b2c065b2545ded3aabd HTTP/1.1

```
> The above command returns JSON structured like this:

```json
{
    "_id": "582e2b2c065b2545ded3aabd",
    "name": "CMU",
    "test": false,
    "children": [
     	"5833479babdafd7b34858958"
    ]
}
```

## Update Location
'`'PUT /api/location/<locationId>`

### URL Parameters

	* locationId (string) - ID of location to update

### Request Body

	* name 
	* test
  * type
  * geoLoc


```http
PUT /api/location/582e2b2c065b2545ded3aabd HTTP/1.1

{
	"name" : "CMU Campus"
}
```


```json
{
    "_id": "582e2b2c065b2545ded3aabd",
    "name": "CMU Campus",
    "test": false,
    "children": [
     	"5833479babdafd7b34858958"
    ]
}
```

## Delete a location
`DELETE /api/location/<locationId>`

### URL Parameters
 locationId (string) - ID of location to delete


```http
DELETE /api/location/582e2b2c065b2545ded3aabd HTTP/1.1
```

```http
HTTP/1.1 200 OK
```

## Find gateways at a location 
`GET /api/location/<locationId>/gateways`

- **Request parameters**

    * id (string) - Location ID


```http
GET /api/location/582e2b2c065b2545ded3aabd/gateways HTTP/1.1
```


```json
TODO
```

## Find devices at a location

`GET /api/location/<locationId>/devices`

### URL Parameters

    * id (string) - Location ID


```http
GET /api/location/582e2b2c065b2545ded3aabd/devices HTTP/1.1
```

```http
TODO
```
