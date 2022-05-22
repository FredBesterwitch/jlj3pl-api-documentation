# HTTP response codes

Application clients that are using our API will receive HTTP response codes in response to every request that is issued.

The table below describes the response codes that will be issued and gives potential reasons for why they may have been sent back.

## Successful response codes
<table>
  <thead>
    <tr>
      <td>Response Code</td>
      <td>Meaning</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>200 OK</td>
      <td>Successful request</td>
    </tr>
  </thead>

</table>

## Unsuccessful response codes
<table>
  <thead>
    <tr>
      <td>Response Code</td>
      <td>Meaning</td>
    </tr>
  </thead>
  <tbody>
  <tr>
      <td>550 Import Data Has Errors</td>
      <td>The UOM data in the payload is invalid.<br>
        Will return an Array of Validation Errors</td>
    </tr>
    <tr>
      <td>400 Bad request</td>
      <td>Invalid or missing request parameters.<br>
Inspect the request parameters and ensure that all required parameters are supplied.<br>
Note the error text in the response and update the request accordingly.</td><br>
    </tr>
     <tr>
      <td>401 Unauthorized</td>
      <td>Invalid or no credentials passed in the request.</td>
    </tr>
    <tr>
      <td>403 Forbidden</td>
      <td>Inspect the authorisation header and ensure that a valid authentication has been provided.<br>
          Authorisation credentials passed and accepted but the account doesn't have permission.<br>
          Inspect the authorisation header and ensure that a valid authentication has been provided.<br>
          Returned when HTTP is used instead of HTTPS.<br>
          Returned when invalid API key is used.<br>
          Returned when you have tried to make more API calls than your allowed quota (QPS). Refer to API rate limits.</td>
    </tr>
 <tr>
      <td>404 Not Found</td>
      <td>The requested URL doesn't exist.<br>
The requested resource was not found.<br>
Inspect the ID in the URL that was used and ensure that it's valid.<br>
Inspect the Accept and Content-Type headers that are being used to make sure they’re correct for the URL that is being requested.</td>
    </tr>
     <tr>
      <td>405 Method not allowed</td>
      <td>The requested resource doesn't support the supplied verb.<br>
        Inspect the HTTP method that was used in the request and ensure that it's valid for the resource being requested.</td>
    </tr>
 <tr>
      <td>429 Too many requests</td>
      <td>The requested resource doesn't support the supplied verb.<br>
        Inspect the HTTP method that was used in the request and ensure that it's valid for the resource being requested.<br>
        Above API quota limits. Returned when you have tried to make more API calls than your allowed quota (QPS).</td>
    </tr>

 <tr>
      <td>500 Internal Server Error</td>
      <td>An internal error occurred when processing the request. Attempt the request again and if the HTTP 500 error re-occurs contact the our Support Team.</td>
    </tr>
 <tr>
      <td>501 Method Not Implemented</td>
      <td>The HTTP method being used has not yet been implemented for the requested resource.<br>
The method being used is not implemented for this resource. Check the documentation for the specific resource type.</td>
    </tr>


  </thead>

</table>


	
	
	


	
	