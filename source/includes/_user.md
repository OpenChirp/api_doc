
# User

## Get Logged-In User Details
> Example Request:

```http
GET /api/user HTTP/1.1
```

> Example Response:

```json
{
  "_id": "58d2ce808113446f5c8c28b7",
  "updated_at": "2017-03-22T19:20:32.405Z",
  "created_at": "2017-03-22T19:20:32.405Z",
  "name": "Test User",
  "email": "test@test.com",
  "__v": 0,
  "id": "58d2ce808113446f5c8c28b7"

```

### HTTP Request

`GET /api/user`

## Get my services

> Example Request:

```http
GET /api/user/myservices?name=influxdb HTTP/1.1
```

> Example Response:

```json
[
  {
    "_id": "58d2d1a48113446f5c8c28bf",
    "updated_at": "2017-03-22T19:33:56.232Z",
    "created_at": "2017-03-22T19:33:56.232Z",
    "owner": "58d2ce808113446f5c8c28b7",
    "name": "InfluxDB Storage Service",
    "description": "Service that stores all device transducer data into InfluxDB",
    "__v": 0,
    "config_required": [],
    "pubsub": {
      "protocol": "MQTT",
      "remove_thing_endpoint": "/services/58d2d1a48113446f5c8c28bf/thing/remove",
      "update_thing_endpoint": "/services/58d2d1a48113446f5c8c28bf/thing/update",
      "new_thing_endpoint": "/services/58d2d1a48113446f5c8c28bf/thing/new",
      "endpoint": "/services/58d2d1a48113446f5c8c28bf"
    },
    "id": "58d2d1a48113446f5c8c28bf"
  }
]

```

### HTTP Request

`GET /api/user/myservices?name=<search_criteria>`

### Request Parameters
Parameter | Description
--------- | -----------
name| Search by name (Optional)

## Get my devices

> Example Request :

```http
GET /api/user/mydevices HTTP/1.1

```
> Example Response :

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
    "_id": "58d2d3328113446f5c8c28c1",
    "updated_at": "2017-03-30T16:07:55.655Z",
    "created_at": "2017-03-22T19:40:34.101Z",
    "owner": "58d2ce808113446f5c8c28b7",
    "name": "Buildings",
    "location_id": "58d2cf268113446f5c8c28bc",
    "type": "LORA",
    "__v": 3,
    "enabled": true,
    "linked_services": [
      {
        "service_id": "58d442c7d0222f0b71c5da82"
      }
    ],
    "commands": [],
    "transducers": [],
    "pubsub": {
      "protocol": "MQTT",
      "endpoint": "/devices/58d2d3328113446f5c8c28c1"
    },
    "id": "58d2d3328113446f5c8c28c1"
  }
 ]
```

### HTTP Request
`GET /api/user/mydevices?name=<search_criteria>`

### Request Parameters
Parameter | Description
--------- | -----------
name| Search by name (Optional)

## Get my locations

> Example Request:

```http
GET /api/user/mylocations?name=pitt HTTP/1.1

```

> Example Response:

```json
[
 {  
    "_id": "58dc24b2e235562ddbc9f22c",
    "updated_at": "2017-03-30T17:55:52.406Z",
    "created_at": "2017-03-29T21:18:42.682Z",
    "owner": "58d2ce808113446f5c8c28b7",
    "name": "Pitt Campus",
    "__v": 0,
    "test": false,
    "children": [],
    "geo_loc": {
      "coordinates": [],
      "type": "Point"
    },
    "id": "58dc24b2e235562ddbc9f22c" 
  }
 ]
```

### HTTP Request
`GET /api/user/mylocations/?name=<search_criteria>`

### Request Parameters

Parameter | Description
--------- | -----------
name | Search by name (Optional)




