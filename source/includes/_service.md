# Service

## Create new Service

> Example Request:

```http
POST /api/service HTTP/1.1
{
  "name":"InfluxDB Storage Service",
  "description": "Service that stores all device transducer data into InfluxDB"
   
}
```

> Example Response:

```json
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
GET /api/service/58d2d1a48113446f5c8c28bf HTTP/1.1

```
> Example Response :

```json
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
|properties|Mixed|


## Delete a service


> Example Request:

```http
DELETE /api/service/582e2b2c065b2545ded3aabd HTTP/1.1
```

> Example Response :

```http
HTTP/1.1 200 OK
```
### HTTP Request
`DELETE /api/service/<ID>`

### Request Parameters
Parameter | Description
--------- | -----------
ID | ID of service to delete

## Add a device to a service
## Update device service config
## Remove a device from a service

## Get all things linked to a service