
# Transducer

## Add a transducer to a device

> Example Request:

```http
POST /api/device/582e2b2c065b2545ded3aabd/transducer HTTP/1.1
{
  "name":"Temperature",
  "unit":"Celsius",
  "properties":{
  	"protobuf":"uint:32"
  	}  
}
```

> Example Response:

```json
{
   "name": "Temperature",
   "unit": "Celsius",
   "properties": {
      "protobuf": "uint:32"
    },
   "_id": "58ddc5c9e235562ddbc9f234",
   "is_actuable": false
}

```

### HTTP Request

`POST /api/device/<deviceId>/transducer`


### Request Parameters

Parameter | Description
--------- | -----------
deviceId | Transducer is added to the device identified by its ID

### Request body

| Name | Type | Description | Required | Default|
|:----------|:-----|:------------|:----|:--------|
|name | String| Name of transducer , example : Temperature| Yes| - |
|unit| String| Unit , example : Celsius |Yes | -|
|is_actuable| Boolean| If the transducer is actuable| No | False|
|properties | Mixed| JSON object that can include any number of key-value pairs| No|-|

## Get all transducers on a device

> Example Request :

```http
GET /api/device/582e2b2c065b2545ded3aabd/transducer HTTP/1.1

```
> Example Response :

```json
[
  {
    "name": "Door_State",
    "unit": "Integer",
    "_id": "58d2d4398113446f5c8c28c3",
    "is_actuable": true
  },
  {
    "name": "Temperature",
    "unit": "Celsius",
    "properties": {
      "protobuf": "uint:32"
    },
    "_id": "58ddc5c9e235562ddbc9f234",
    "is_actuable": false
  }
]

```
### HTTP Request
`GET /api/device/<deviceID>/transducer`

### Request Parameters
Parameter | Description
--------- | -----------
deviceID| ID of device

## Update a transducer
Updating a transducer is not supported by design.


## Publish to a transducer

> Example Request:

```http
POST /api/device/582e2b2c065b2545ded3aabd/transducer/58d2d4398113446f5c8c28c3 HTTP/1.1

{
"test":"Hello"
}
```

> Example Response :

```json
{
  "message": "Done"
}
```
### HTTP Request
`POST /api/device/<deviceID>/transducer/<transducerID>`

### Request Parameters
Parameter | Description
--------- | -----------
deviceID| ID of device.
transducerID | ID of transducer to publish to.

### Request Body
The json in the request body is published as-is to the transducer topic.

## Delete a transducer


> Example Request:

```http
DELETE /api/device/582e2b2c065b2545ded3aabd/transducer/58d2d4398113446f5c8c28c3 HTTP/1.1
```

> Example Response :

```http
HTTP/1.1 200 OK
```
### HTTP Request
`DELETE /api/device/<deviceID>/transducer/<transducerID>`

### Request Parameters
Parameter | Description
--------- | -----------
deviceID | ID of device.
transducerID | ID of transducer to delete