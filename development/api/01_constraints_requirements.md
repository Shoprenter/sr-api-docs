# API request requirements and restrictions

- **Content-Type** value is mandatory in the Header data!<br>
  The following formats are available, the chosen format will define communication with API.
  + JSON: **application/json** (recommended)
  + FormData: **multipart/form-data**
- The default format of API request response received by the application is XML.
- If JSON format is required, **Accept: application/json** should be indicated in the Header of the API request.
- **Maximum request limit is 3/application/shop/second**. Exceeding the limit will result in 429 error code. This means 180 requests per minute. 
