# Device

## Create new Device 

> Example Request:

```http
POST /api/device HTTP/1.1
{
  "name":"Lab Door",
  "location_id":"58d2cf268113446f5c8c28bc"
}
```

> Example Response:

```json
{
    "_id": "58dd50c4e235562ddbc9f231",
    "updated_at": "2017-03-30T19:39:56.719Z",
    "created_at": "2017-03-30T18:39:00.265Z",
    "owner": "58d2ce808113446f5c8c28b7",
    "name": "Lab Door",
    "location_id": "58d2cf268113446f5c8c28bc",
    "__v": 0,
    "enabled": true,
    "linked_services": [],
    "commands": [],
    "transducers": [],
    "pubsub": {
      "protocol": "MQTT",
      "endpoint": "/devices/58dd50c4e235562ddbc9f231"
    },
    "id": "58dd50c4e235562ddbc9f231"
  }

```

### HTTP Request

`POST /api/device`


### Request body
| Name | Type | Description | Required | Default|
|:----------|:-----|:------------|:----|:--------|
|name|String| Name of device| Yes|-|
|type|Enum {LORA, TWIST, FIREFLY, BOSCH_XDK}| Type of device.| No | -|
|location_id| String| Location ID | No | - |
|gateway_id| String| Gateway ID | No | - | 
|enabled | Boolean| If set to false, then the device is not monitored| No | True|
|properties | Mixed| JSON object that can include any number of key-value pairs| No|-|


## Create new Device using a template

> Example Request:

```http
POST /api/device HTTP/1.1
{
  "name":"Lab Door",
  "location_id":"58d2cf268113446f5c8c28bc",
  "template_id":"58d443b5d0222f0b71c5da83"
}
```

> Example Response:

```json
{
    "_id": "58dd50c4e235562ddbc9f231",
    "updated_at": "2017-03-30T19:39:56.719Z",
    "created_at": "2017-03-30T18:39:00.265Z",
    "owner": "58d2ce808113446f5c8c28b7",
    "name": "Lab Door",
    "location_id": "58d2cf268113446f5c8c28bc",
    "__v": 0,
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
      "endpoint": "/devices/58dd50c4e235562ddbc9f231"
    },
    "id": "58dd50c4e235562ddbc9f231"
  }
```

### HTTP Request

`POST /api/device`


### Request body
All the fields in the create device request above can be included plus a template_id which is used to create transducers, commands and linked services.

| Name | Type | Description | Required | Default|
|:----------|:-----|:------------|:----|:--------|
|template_id| String| Device template ID. All transducers, commands and linked services in the template will be added to the device.|No|-|

## Get details of a device

> Example Request :

```http
GET /api/device/58d445bc2881ee1032d63508 HTTP/1.1

```
> Example Response :

```json
{
    "_id": "58d445bc2881ee1032d63508",
    "updated_at": "2017-03-23T22:01:32.151Z",
    "created_at": "2017-03-23T22:01:32.151Z",
    "owner": "58d2ce808113446f5c8c28b7",
    "name": "Lora Device6",
    "__v": 0,
    "enabled": true,
    "linked_services": [],
    "commands": [],
    "transducers": [],
    "pubsub": {
      "protocol": "MQTT",
      "endpoint": "/devices/58d445bc2881ee1032d63508"
    },
    "id": "58d445bc2881ee1032d63508"
 }

```
### HTTP Request
`GET /api/device/<ID>`

### Request Parameters
Parameter | Description
--------- | -----------
ID| ID of device

## Update a device

> Example Request:

```http
PUT /api/device/58d445bc2881ee1032d63508 HTTP/1.1

{
	"type": "LORA"
}
```
> Example Response:

```json
{
    "_id": "58d445bc2881ee1032d63508",
    "updated_at": "2017-03-23T22:01:32.151Z",
    "created_at": "2017-03-23T22:01:32.151Z",
    "owner": "58d2ce808113446f5c8c28b7",
    "name": "Lora Device6",
    "type": "LORA"
    "__v": 0,
    "enabled": true,
    "linked_services": [],
    "commands": [],
    "transducers": [],
    "pubsub": {
      "protocol": "MQTT",
      "endpoint": "/devices/58d445bc2881ee1032d63508"
    },
    "id": "58d445bc2881ee1032d63508"
 }
```

### HTTP Request
`PUT /api/device/<ID>`

### Request Parameters

Parameter | Description
--------- | -----------
ID | ID of device to update

### Request body
The request body can include one or more of the fields below that need to be updated.

| Name | Type 
|:----------|:-----|
|name|String| 
|type|Enum {LORA, TWIST, FIREFLY, BOSCH_XDK}| 
|location_id| String|  
|gateway_id|String|
|enabled | Boolean| 
|properties | Mixed| 


## Delete a device

> Example Request:

```http
DELETE /api/device/582e2b2c065b2545ded3aabd HTTP/1.1
```

> Example Response :

```http
HTTP/1.1 200 OK
```
### HTTP Request
`DELETE /api/device/<ID>`

### Request Parameters
Parameter | Description
--------- | -----------
ID | ID of device to delete

