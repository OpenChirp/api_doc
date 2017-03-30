
# Device Template

## Create new device template

> Example Request:

```http
POST /api/devicetemplate HTTP/1.1
{
  "name":"InfluxDB Storage Service",
   
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
|name | String| Name of service, example: InfluxDBStorageService.| Yes| - |
|description| String| A short description of what this service does.| Yes | - |
|device_id|String|

## Get details of a template

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