# Errors

The GearGag API uses the following error codes:

<strong>HTTP Response status code</strong>

Status code | Description
------- | -------------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API token is wrong.
422 | Bad Request/ Unprocessable Entity - Your data is invalid
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.

<strong>Data Response status value</strong>

Status value | Description
------- | -------------
true | Ok
false | Not OK