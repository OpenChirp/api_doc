
# Command


## Create new Command

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
|name | String| Name of command, example: Open Door| Yes| - |


## Get all commands on a device

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

## Execute a command

## Update a command

## Delete a command


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