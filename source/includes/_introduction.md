
# OpenChirp API Reference
The document specifies a RESTful API for interacting with the OpenChirp infrastructure. Usage of the API is via the HTTP protocol. All operations are defined as GET, POST, PUT, DELETE on resource URLs. Some examples of resources in the OpenChirp software stack are Location, Device, Gateway, Service etc. All these resources are represented in JSON.


## Errors

The OpenChirp REST API uses the following error codes:


HTTP Error Code | Meaning
---------- | -------
400 | Bad Request -- The json in request body is not well-formed.
401 | Unauthorized -- Invalid credentials.
403 | Forbidden -- Logged in user does not have permissions to do this operation.
404 | Not Found 
500 | Internal Server Error
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
