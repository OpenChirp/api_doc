
# Device Template

## Get all device templates

> Example Request:

```http
GET /api/devicetemplate HTTP/1.1
```

> Example Response:

```json
[
  {
    "_id": "58d443b5d0222f0b71c5da83",
    "updated_at": "2017-03-23T21:52:53.580Z",
    "created_at": "2017-03-23T21:52:53.580Z",
    "owner": "58d2ce808113446f5c8c28b7",
    "name": "Lora Template1",
    "description": "Template with 3 transducers with properties",
    "__v": 0,
    "linked_services": [
      {
        "service_id": "58d442c7d0222f0b71c5da82"
      }
    ],
    "transducers": [
      {
        "name": "Temperature",
        "unit": "Celsius",
        "is_actuable": false,
        "properties": {
          "protobuf": "uint:1"
        },
        "commands": []
      },
      {
        "name": "Pressure",
        "unit": "Psi",
        "is_actuable": false,
        "properties": {
          "protobuf": "uint:2"
        },
        "commands": []
      },
      {
        "name": "Voltage",
        "unit": "V",
        "is_actuable": false,
        "properties": {
          "protobuf": "uint:3"
        },
        "commands": []
      }
    ],
    "id": "58d443b5d0222f0b71c5da83"
  }
]
```

### HTTP Request
`GET /api/devicetemplate`

## Create new device template

> Example Request:

```http
POST /api/devicetemplate HTTP/1.1
{
  "name":"Lora Template",
  "device_id":"58d445bc2881ee1032d63508"  
}
```

> Example Response:

```json

```

### HTTP Request

`POST /api/devicetemplate`

### Request body

| Name | Type | Description | Required | Default|
|:----------|:-----|:------------|:----|:--------|
|name | String| Name of device template Yes| - |
|description| String| A short description of what this template contains.| Yes | - |
|device_id|String| ID of device from which to generate this template| Yes|-|

## Get details of a template

> Example Request :

```http
GET /api/devicetemplate/582e2b2c065b2545ded3aabd HTTP/1.1

```
> Example Response :

```json


```
### HTTP Request
`GET /api/devicetemplate/<ID>`

### Request Parameters
Parameter | Description
--------- | -----------
ID| ID of device template

## Update a device template

Not supported.

## Delete a device template


> Example Request:

```http
DELETE /api/devicetemplate/582e2b2c065b2545ded3aabd HTTP/1.1
```

> Example Response :

```http
HTTP/1.1 200 OK
```
### HTTP Request
`DELETE /api/devicetemplate/<ID>`

### Request Parameters
Parameter | Description
--------- | -----------
ID | ID of device template to delete