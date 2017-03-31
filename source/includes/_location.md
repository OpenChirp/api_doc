#Location

## Create new Location 

> Example Request:

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

> Example Response:

```json
{
    "_id": "58d2ce918113446f5c8c28b8",
    "updated_at": "2017-03-29T21:18:42.684Z",
    "created_at": "2017-03-22T19:20:49.271Z",
    "owner": "58d2ce808113446f5c8c28b7",
    "name": "CIC",
    "__v": 0,
    "test": false,
    "type":"BUILDING",
    "geo_loc": {
      "coordinates": [
        40.4509146,
        -79.9024777
      ],     
      "type": "Point"
    },
    "id": "58d2ce918113446f5c8c28b8"
  }
```

### HTTP Request

`POST /api/location/<parentLocationId>`

### Request Parameters

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

> Example Request :

```http
GET /api/location/582e2b2c065b2545ded3aabd HTTP/1.1

```
> Example Response :

```json
{
    "_id": "58d2ce918113446f5c8c28b8",
    "updated_at": "2017-03-29T21:18:42.684Z",
    "created_at": "2017-03-22T19:20:49.271Z",
    "owner": "58d2ce808113446f5c8c28b7",
    "name": "CMU",
    "__v": 0,
    "test": false,
    "children": [
      "58d2cef38113446f5c8c28b9",
      "58d2cf008113446f5c8c28ba",
      "58dc24b2e235562ddbc9f22c"
    ],
    "geo_loc": {
      "coordinates": [],
      "type": "Point"
    },
    "id": "58d2ce918113446f5c8c28b8"
  }

```
### HTTP Request
`GET /api/location/<locationID>`

### Request Parameters
Parameter | Description
--------- | -----------
locationId | ID of location

## Update a Location

> Example Request:

```http
PUT /api/location/582e2b2c065b2545ded3aabd HTTP/1.1

{
	"name" : "CMU Campus"
}
```
> Example Response:

```json
{
    "_id": "58d2ce918113446f5c8c28b8",
    "updated_at": "2017-03-29T21:18:42.684Z",
    "created_at": "2017-03-22T19:20:49.271Z",
    "owner": "58d2ce808113446f5c8c28b7",
    "name": "CMU Campus",
    "__v": 0,
    "test": false,
    "children": [
      "58d2cef38113446f5c8c28b9",
      "58d2cf008113446f5c8c28ba",
      "58dc24b2e235562ddbc9f22c"
    ],
    "geo_loc": {
      "coordinates": [],
      "type": "Point"
    },
    "id": "58d2ce918113446f5c8c28b8"
  }
```

### HTTP Request
`PUT /api/location/<locationId>`

### Request Parameters

Parameter | Description
--------- | -----------
locationId | ID of location to update

### Request body
The request body can include one or more of the fields below that need to be updated.

| Name | Type | 
|:----------|:-----|
|name|String|
|type|Enum {BUILDING, INDOOR}|
|test | Boolean| 
|geo_loc.type | String| 
|geo_loc.coordinates|Number|

## Delete a location

> Example Request:

```http
DELETE /api/location/582e2b2c065b2545ded3aabd HTTP/1.1
```

> Example Response :

```http
HTTP/1.1 200 OK
```
### HTTP Request
`DELETE /api/location/<locationId>`

### Request Parameters
Parameter | Description
--------- | -----------
locationId | ID of location to delete

<aside class="notice"> If a location has child locations, devices or gateways, then it cannot be deleted. </aside>

## Get gateways at a location 

> Example Request:

```http
GET /api/location/58d2cf268113446f5c8c28bc/gateways HTTP/1.1
```

> Example Response: 

```json
[
  {
    "_id": "58dc5e8ee235562ddbc9f22e",
    "updated_at": "2017-03-30T01:25:34.907Z",
    "created_at": "2017-03-30T01:25:34.907Z",
    "owner": "58d2ce808113446f5c8c28b7",
    "name": "Lora Gateway",
    "type": "LORA",
    "location_id": "58d2cf268113446f5c8c28bc",
    "__v": 0,
    "enabled": true,
    "pubsub": {
      "protocol": "MQTT"
    },
    "id": "58dc5e8ee235562ddbc9f22e"
  }
]
```

### HTTP Request
`GET /api/location/<locationId>/gateways`


### Request Parameters
Parameter | Description
--------- | -----------
locationId | ID of location


## Get devices at a location

> Example Request:

```http
GET /api/location/58d2cf268113446f5c8c28bc/devices HTTP/1.1
```

> Example Response: 

```json
[
  {
    "_id": "58d2d3078113446f5c8c28c0",
    "updated_at": "2017-03-22T19:46:01.186Z",
    "created_at": "2017-03-22T19:39:51.961Z",
    "owner": "58d2ce808113446f5c8c28b7",
    "name": "Lab Door",
    "location_id": "58d2cf268113446f5c8c28bc",
    "__v": 3,
    "enabled": true,
    "linked_services": [],
    "commands": [
      {
        "name": "Open Door",
        "value": "1",
        "transducer_id": "58d2d4398113446f5c8c28c3",
        "_id": "58d2d46d8113446f5c8c28c4"
      },
      {
        "name": "Close Door",
        "value": "0",
        "transducer_id": "58d2d4398113446f5c8c28c3",
        "_id": "58d2d4798113446f5c8c28c5"
      }
    ],
    "transducers": [
      {
        "name": "Door_State",
        "unit": "Integer",
        "_id": "58d2d4398113446f5c8c28c3",
        "is_actuable": true
      }
    ],
    "pubsub": {
      "protocol": "MQTT",
      "endpoint": "/devices/58d2d3078113446f5c8c28c0"
    },
    "id": "58d2d3078113446f5c8c28c0"
  },
  {
    "_id": "58d2d3468113446f5c8c28c2",
    "updated_at": "2017-03-22T19:40:54.798Z",
    "created_at": "2017-03-22T19:40:54.798Z",
    "owner": "58d2ce808113446f5c8c28b7",
    "name": "Xdk Sensor1",
    "location_id": "58d2cf268113446f5c8c28bc",
    "type": "BOSCH_XDK",
    "__v": 0,
    "enabled": true,
    "linked_services": [],
    "commands": [],
    "transducers": [],
    "pubsub": {
      "protocol": "MQTT",
      "endpoint": "/devices/58d2d3468113446f5c8c28c2"
    },
    "id": "58d2d3468113446f5c8c28c2"
  }
]
```

### HTTP Request
`GET /api/location/<locationId>/devices`


### Request Parameters
Parameter | Description
--------- | -----------
locationId | ID of location


