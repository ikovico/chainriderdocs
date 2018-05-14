# Errors

The ChainRider API uses the following error codes:

Error Code | Meaning
---------- | -------
400        | Bad Request
401        | Unauthorized -- Your API token is wrong.
403        | Forbidden -- You do not have access to the requested resource.
404        | Not Found -- The specified resource could not be found.
405        | Method Not Allowed -- You tried to access a resource with an invalid method.
406        | Not Acceptable -- You requested a format that isn't JSON.
429        | Too Many Requests -- Slow down!
500        | Internal Server Error -- We had a problem with our server. Try again later.
503        | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
