# Gateway

## Create new Gateway 

> Example Request:

```http
POST /api/gateway HTTP/1.1
{
    "name": "LabGateway",
    "location_id": "5833479babdafd7b34858958",
    "type": "LORA"
}
```

> Example Response:

```json
{
    "_id": "5873dfefc653394e3f0966b9",
    "name": "LabGateway",
    "location_id": "5833479babdafd7b34858958",
    "type": "LORA",
    "__v": 0,
    "enabled": true
}
```

### HTTP Request
`POST /api/gateway`

### Request Body
| Name | Type | Description | Required | Default|
|:----------|:-----|:------------|:----|:--------|
|name|String| Name of gateway| Yes|-|
|type|Enum {LORA, ZIGBEE}| Type of gateway.| Yes | -|
|location_id| String| Location ID | 
|enabled | Boolean| If set to false, then the gateway is not monitored| No | True|
|properties | Mixed| JSON object that can include any number of key-value pairs| No|-|

## Get all gateways

> Example Request:

```http
GET /api/gateway HTTP/1.1
```
>Example Response:

```json
 [
  {
    "_id": "5873dfefc653394e3f0966b9",
    "name": "LabGateway",
    "location_id": "5833479babdafd7b34858958",
    "type": "LORA",
    "__v": 0,
    "enabled": true
  },
  {
    "_id": "587e9cf0ee4cf540f8590784",
    "name": "CICGateway",
    "location_id": "5833479babdafd7b34858958",
    "type": "LORA",
    "__v": 0,
    "enabled": true
 ]    

```

### HTTP Request
`GET /api/gateway`

## Get details of a gateway

> Example Request:

```http
GET /api/gateway/587e9cf0ee4cf540f8590784 HTTP/1.1

```

> Example Response:

```json

{
    "_id": "587e9cf0ee4cf540f8590784",
    "name": "CICGateway",
    "location_id": "5833479babdafd7b34858958",
    "type": "LORA",
    "__v": 0,
    "enabled": true
}
```
### HTTP Request
`GET /api/gateway/<gatewayID> `

### Request Parameters
Parameter | Description
--------- | -----------
gatewayID| ID of gateway

## Get devices linked to a gateway

> Example Request:

```http
GET /api/gateway/587e9cf0ee4cf540f8590784/devices HTTP/1.1
```

> Example Response:

```json
TODO

```

## Update gateway

> Example Request :

```http
PUT /api/gateway/587e9cf0ee4cf540f8590784 HTTP/1.1

{
	"name" : "CICGateway_Lab"
}
```

> Example Response :

```json
{
    "_id": "587e9cf0ee4cf540f8590784",
    "name": "CICGateway_Lab",
    "location_id": "5833479babdafd7b34858958",
    "type": "LORA",
    "__v": 0,
    "enabled": true
}
```


### HTTP Request
`PUT /api/gateway/<ID>`

### Request Parameters

Parameter | Description
--------- | -----------
ID | ID of gateway to update

### Request body
The request body can include one or more of the fields below that have to updated.

| Name | Type |
|:-----|:-----|
|name|String| 
|location_id|String|
|type|Enum|
|enabled| Boolean|


## Delete a gateway


> Example Request:

```http
DELETE /api/gateway/582e2b2c065b2545ded3aabd HTTP/1.1
```

> Example Response :

```http
HTTP/1.1 200 OK
```
### HTTP Request
`DELETE /api/gateway/<ID>`

### Request Parameters

Parameter | Description
--------- | -----------
ID | ID of gateway to delete

