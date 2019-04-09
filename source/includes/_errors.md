# Errors

The [WordPress Download Manager](https://www.wpdownloadmanager.com/) REST API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid. YOu SHOULD NOT repeat the request without modifications.
401 | Unauthorized -- Your API key/Username/Password is wrong.
403 | Forbidden -- The resource requested is hidden for administrators only.
404 | Not Found -- The specified resource could not be found.
429 | Too Many Requests -- You're requesting too many resources! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
