
# Command


## Create new Command

> Example Request:

```http
POST /api/device/58d445bc2881ee1032d63508/command HTTP/1.1
{
  "name":"Open Door",
  "transducer_id":"58d2d4398113446f5c8c28c3",
  "value" :"1"
}
```

> Example Response:

```json
{
    "name": "Open Door",
    "value": "1",
    "transducer_id": "58d2d4398113446f5c8c28c3",
    "_id": "58d2d46d8113446f5c8c28c4"
  }

```

### HTTP Request

`POST /api/device/<deviceID>/command`


### Request body

| Name | Type | Description | Required | Default|
|:----------|:-----|:------------|:----|:--------|
|name | String| Name of command, example: Open Door| Yes| - |
|transducer_id|String| Transducer to publish value to | Yes|-|
|value| String | Value to publish to transducer| Yes |-|

<aside class="notice"> Commands can only be created for transducers that have is_actuable set to true.</aside>

## Get all commands on a device

> Example Request :

```http
GET /api/device/582e2b2c065b2545ded3aabd/command HTTP/1.1

```
> Example Response :

```json
[
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
]

```
### HTTP Request
`GET /api/device/<deviceID>/command`

### Request Parameters
Parameter | Description
--------- | -----------
deviceID| 

## Execute a command

> Example Request:

```http
POST /api/device/582e2b2c065b2545ded3aabd/command/58d445bc2881ee1032d63508 HTTP/1.1
```

> Example Response:

```json
{ 
"message": "Done"
}
```

### HTTP Request
`POST /api/device/<deviceID>/command/<commandID>`

### Request Parameters
Parameter | Description
--------- | -----------
deviceID| ID of device
commandID| ID of command to execute

## Update a command

Not supported.

## Delete a command


> Example Request:

```http
DELETE /api/device/582e2b2c065b2545ded3aabd/command/58d445bc2881ee1032d63508 HTTP/1.1
```

> Example Response :

```http
HTTP/1.1 200 OK
```
### HTTP Request
`DELETE /api/device/<deviceID>/command/<commandID>`

### Request Parameters
Parameter | Description
--------- | -----------
deviceID | ID of command's device.
commandID| ID of command to delete.