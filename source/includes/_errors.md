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
