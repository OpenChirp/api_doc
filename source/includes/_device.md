# Device

## Create new Device 

> Example Request:

```http
POST /api/device HTTP/1.1
{
  "name":"Lora",
   
}
```

> Example Response:

```json

```

### HTTP Request

`POST /api/device`


### Request body
| Name | Type | Description | Required | Default|
|:----------|:-----|:------------|:----|:--------|
|name|String| Name of device| Yes|-|
|type|Enum {LORA, TWIST, FIREFLY, BOSCH_XDK}| Type of device.| Yes | -|
|location_id| String| Location ID | 
|enabled | Boolean| If set to false, then the device is not monitored| No | True|
|properties | Mixed| JSON object that can include any number of key-value pairs| No|-|


## Create new Device using a template

## Get details of a device

> Example Request :

```http
GET /api/device/582e2b2c065b2545ded3aabd HTTP/1.1

```
> Example Response :

```json


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
PUT /api/device/582e2b2c065b2545ded3aabd HTTP/1.1

{
	"name" : ""
}
```
> Example Response:

```json
{
  
  }
```

### HTTP Request
`PUT /api/device/<ID>`

### Request Parameters

Parameter | Description
--------- | -----------
ID | ID of device to update

### Request body
The request body can include one or more of the fields below that have to updated.
| Name | Type 
|:----------|:-----|
|name|String| 
|type|Enum {LORA, TWIST, FIREFLY, BOSCH_XDK}| 
|location_id| String|  
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

