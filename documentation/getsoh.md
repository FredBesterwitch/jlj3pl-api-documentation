
# Get Stock On Hand

Use this end point to get the current SOH for a list of SKU's

## Payload 

<table>
<tr>
      <td>Property</td>
      <td>Value</td>
      <td>Rules</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Array of SKU's</td>
      <td>An Array of valid SKU's</td>
      <td>Must have a Value, cannot be blank.</td>
    </tr>
    

  </thead>
</table>

## Sample Payload
<pre>["ATR318","ATRMV18","ATRCP18","ATR319"]
</pre>


## CURL
curl --location --request POST 'BASE-URL/getstockonhand' \
--header 'Content-Type: application/json' \
--header 'x-api-key: YOUR-API-KEY' \
--header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IkxwT3NWTWFjcmlhZTgzTWE1THRNMyJ9.eyJpc3MiOiJodHRwczovL2psai0zcGwtZGV2LmF1LmF1dGgwLmNvbS8iLCJzdWIiOiJMa2lOTGtrZUo5ZzU2aGhhVXBscUZXTW9QN0VMRW53dUBjbGllbnRzIiwiYXVkIjoiaHR0cHM6Ly9sb2NhbGhvc3Q6OTAwMCIsImlhdCI6MTY1MzE5OTExMSwiZXhwIjoxNjUzMjg1NTExLCJhenAiOiJMa2lOTGtrZUo5ZzU2aGhhVXBscUZXTW9QN0VMRW53dSIsImd0eSI6ImNsaWVudC1jcmVkZW50aWFscyJ9.D2jt51j8WMcpTbUWJlaVDOKzgkEPFoQaJZVjsi6FpFk_pSgRKp1-bJ_QYPfkPzaz1u0R-t6Ut9xQlDlyL8NVJ7qFc_ilh5AIvZkOm9GQ0_2__G0uZR4AaZ7t2SzJZqwdyawhwbWuXeMmju4jrZuQjk5QlkEbGjawUGrwy8q-8zCYTRD22ts7ojTzgQ03Dyuo-a91zP2rhGGl2Fqb3La30MCJmDOOZuh7kj28lWdzLrTha7Ohnboyx6ngtweh4e-Npp-sbOIQuM4FBRDvOuKJGB4O0vLtUbpB3iBzLN1IkJr4J0rnnatbd1HV8zkJF6ro6pK5Yb2bUk08Sakxl6srdQ'
--data-raw '["ATR318","ATRMV18","ATRCP18","ATR319"]'

### Response
for each reponse you have to check the 'error' flag

### All Good
200 OK , if error is false, then your data has been accepted and the client will get an email notifying about the successful import
<pre>{
    "error": false,
    "data": [
        {
            "sku": "ATR318",
            "soh": 0
        },
        {
            "sku": "ATR319",
            "soh": 0
        },
        {
            "sku": "ATRCP18",
            "soh": 192
        },
        {
            "sku": "ATRMV18",
            "soh": 24
        }
    ]
}</pre>

## Response Data
- if a SKU is not found, it wont be sent back in the array
- All return SOH quantities are in each quantity. Must be converted to your UOM. Your application should convert it back -> soh/UOM Quantity
