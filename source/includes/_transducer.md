
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

## Get values from a transducer

> Example Request:

```http
GET /api/device/590b8ab0c1d7ee2313ee421c/transducer/590cf1d043fc916594746b1b HTTP/1.1
```
> Using ```cURL```:

```shell
curl -G "http://openchirp.andrew.cmu.edu:7000/api/device/590b8ab0c1d7ee2313ee421c/transducer/590cf1d043fc916594746b1b"
```

> Example Response. Returns **all values in a chunked stream** (chunks have a size of 10,000 points), ordered by ascending time order:

```json
{
  "results": [
    {
      "series": [
        {
          "name": "590b8ab0c1d7ee2313ee421c_door_state",
          "columns": [
            "time",
            "value"
          ],
          "values": [

            // all values will be returned in a chunked stream 
            ...
```

Performing an HTTP GET to a transducer resource will return the values stored in the database in ascending time order. 
Additional parameters allow you to define start and end times, maximum number of returned values, and paginate through the values.

The default output format is JSON. It is possible to specify the output format using the Content-Type HTTP header, where:

1. ```text/csv``` or ```application/csv``` specifies CSV output
2. any other content type will produce JSON output (default)

<aside class="notice"> 
By default, results are returned in a chunked stream (chunks have a size of 10,000 points).
</aside>

### HTTP Request
`GET /api/device/<deviceID>/transducer/<transducerID>?[stime=<stime>&etime=<etime>&limit=<limit>&page=<page>]`

### Request Parameters
Parameter | Description
--------- | -----------
deviceID | ID of device.
transducerID | ID of transducer
stime | See [Start and End Times](#Start-and-End-Times)
etime | See [Start and End Times](#Start-and-End-Times)
limit | See [Limit and Paginating](#Limit-and-Paginating)
page | See [Limit and Paginating](#Limit-and-Paginating) 

Parameters ```stime```, ```etime```, ```limit``` and ```page``` are not mandatory, and they can be freely combined, for example to return 5000 results (```limit=5000```) from a week ago (```stime=now - 1w```).

### Start and End Times

> Example Request. Return values from the last week, by passing ```stime=now() - 1w``` (note parameters are URL encoded and there must be spaces (%20) in the time specification):

```http
GET /api/device/582e2b2c065b2545ded3aabd/transducer/58d2d4398113446f5c8c28c3%20%3Fstime%3Dnow%28%29%20-%201w HTTP/1.1
```
> Using ```cURL``` (note the ```--data-urlencode``` and the spaces in the time specification):

```shell
curl -G "http://openchirp.andrew.cmu.edu:7000/api/device/582e2b2c065b2545ded3aabd/transducer/58d2d4398113446f5c8c28c3" --data-urlencode “stime=now() - 1w"
```

It is possible to define start and end times using the ```stime``` and ```etime``` query string parameters. The time specifications are according to [InfluxDB](https://docs.influxdata.com/influxdb/v0.9/query_language/data_exploration/#time-syntax-in-queries). 

For example, ```stime=now() - 1w``` indicates that the query will return values starting one week ago. 
You can use simular time specifications using ‘d’ (days), ‘h’ (hours), ‘m’ (minutes), ’s’ (seconds), ‘ms’ (milliseconds) and ‘u’ (microseconds).

Other time specification examples:

1. ```stime=stime=now() - 1w&etime=stime=now() - 1d```: values from one week ago until yesterday.
2. ```stime=stime=2015-08-18 23:00:01.232000000&etime=stime=2015-09-19```: values between August 18, 2015 23:00:01.232000000 and September 19, 2015 00:00:00.

Please check [InfluxDB’s documentation section on Time syntax in Queries](https://docs.influxdata.com/influxdb/v0.9/query_language/data_exploration/#time-syntax-in-queries) for details.

<aside class="notice"> 
The spaces between the ‘-‘ operator of time specifications are important. Be sure to URL encode parameters (see examples). 
</aside>

### Limit and Paginating

> Example Request. Return the first 5000 values from a week ago in CSV format:

```http
GET /api/device/582e2b2c065b2545ded3aabd/transducer/58d2d4398113446f5c8c28c3%20%3Fstime%3Dnow%28%29%20-%201w%26limit%3D5000 HTTP/1.1

Content-Type: application/csv
```
> Using ```cURL```:

```shell
curl -H "Content-Type: application/csv" -G "http://openchirp.andrew.cmu.edu:7000/api/device/<deviceID>/transducer/<transducerID>" --data-urlencode "limit=5000" --data-urlencode "stime=now() - 1w"
```

You can set a limit to the number of points returned using the ```limit``` query string parameter, which can have a maximum value of 10,000 (```limit=0``` is equal to ```limit=10000```). 

The parameter ```page``` can be used to paginate thought the results, where each page has a size defined by the ```limit``` argument or defaults to 10,000 if no ```limit``` is given.

<aside class="notice"> 
When you provide a <b>limit</b> or <b>page</b> parameter, results are returned in a single (non-chunked) response.
</aside>

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
