# Service

## Create new Service

> Example Request:

```http
POST /api/service HTTP/1.1
{
  "name":"InfluxDB Storage Service",
   
}
```

> Example Response:

```json

```

### HTTP Request

`POST /api/service`


### Request body

| Name | Type | Description | Required | Default|
|:----------|:-----|:------------|:----|:--------|
|name | String| Name of service, example: InfluxDBStorageService.| Yes| - |
|description| String| A short description of what this service does.| Yes | - |
|properties | Mixed| Custom properties of this service. JSON object that can include any number of key-value pairs| No|-|
|config_required|ThingsConfig| Config required from things when they link to this service. | No | -

## Get details of a service

> Example Request :

```http
GET /api/service/582e2b2c065b2545ded3aabd HTTP/1.1

```
> Example Response :

```json


```
### HTTP Request
`GET /api/service/<ID>`

### Request Parameters
Parameter | Description
--------- | -----------
ID| ID of service

## Update a service

> Example Request:

```http
PUT /api/service/582e2b2c065b2545ded3aabd HTTP/1.1

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
`PUT /api/service/<ID>`

### Request Parameters

Parameter | Description
--------- | -----------
ID | ID of service to update

### Request body
The request body can include one or more of the fields below that have to updated.

| Name | Type |
|:-----|:-----|
|name|String| 
|description|String|


## Delete a service


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