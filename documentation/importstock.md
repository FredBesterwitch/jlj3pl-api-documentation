
# Import Stock - SKU's

Use this end point to import SKU's

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
      <td>sku</td>
      <td>the Stock Code used by your client</td>
      <td>Must have a Value, cannot be blank.</td>
    </tr>
        <tr>
      <td>description</td>
      <td>The Description of the SKU</td>
      <td>Must have a Value, cannot be blank.</td>
    </tr>
   <tr>
      <td>uom</td>
      <td>The Unit Of Measurement for this SKU</td>
      <td>Must have a Value, cannot be blank and valid UOM Code.</td>
    </tr>
       <tr>
      <td>supplier</td>
      <td>The supplier for this SKU</td>
      <td>Must have a Value, cannot be blank and valid Supplier Code.</td>
    </tr>

  </thead>
</table>

## Sample Payload
<pre>[{
    "sku":"1234",
    "description":"SKU 1234",
    "uom":"DOZEN",
    "supplier":"A.T. RICHARDSON WINES PTY LTD"
},
{
    "sku":"123456",
    "description":"SKU 123456",
    "uom":"EACH",
    "supplier":"A.T. RICHARDSON WINES PTY LTD"
},
{
    "sku":"11111111",
    "description":"SKU 11111111",
    "uom":"DOZEN",
    "supplier":"A.T. RICHARDSON WINES PTY LTD"
}
]
</pre>


## CURL
curl --location --request POST 'BASE-URL/import/importstock' \
--header 'Content-Type: application/json' \
--header 'x-api-key: YOUR-API-KEY' \
--header 'REQUIRED-API-VERSION: 2000' \
--header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IkxwT3NWTWFjcmlhZTgzTWE1THRNMyJ9.eyJpc3MiOiJodHRwczovL2psai0zcGwtZGV2LmF1LmF1dGgwLmNvbS8iLCJzdWIiOiJMa2lOTGtrZUo5ZzU2aGhhVXBscUZXTW9QN0VMRW53dUBjbGllbnRzIiwiYXVkIjoiaHR0cHM6Ly9sb2NhbGhvc3Q6OTAwMCIsImlhdCI6MTY1MzE5OTExMSwiZXhwIjoxNjUzMjg1NTExLCJhenAiOiJMa2lOTGtrZUo5ZzU2aGhhVXBscUZXTW9QN0VMRW53dSIsImd0eSI6ImNsaWVudC1jcmVkZW50aWFscyJ9.D2jt51j8WMcpTbUWJlaVDOKzgkEPFoQaJZVjsi6FpFk_pSgRKp1-bJ_QYPfkPzaz1u0R-t6Ut9xQlDlyL8NVJ7qFc_ilh5AIvZkOm9GQ0_2__G0uZR4AaZ7t2SzJZqwdyawhwbWuXeMmju4jrZuQjk5QlkEbGjawUGrwy8q-8zCYTRD22ts7ojTzgQ03Dyuo-a91zP2rhGGl2Fqb3La30MCJmDOOZuh7kj28lWdzLrTha7Ohnboyx6ngtweh4e-Npp-sbOIQuM4FBRDvOuKJGB4O0vLtUbpB3iBzLN1IkJr4J0rnnatbd1HV8zkJF6ro6pK5Yb2bUk08Sakxl6srdQ' \
--data-raw '[{
    "sku":"1234",
    "description":"SKU 1234",
    "uom":"DOZEN",
    "supplier":"A.T. RICHARDSON WINES PTY LTD"
},
{
    "sku":"123456",
    "description":"SKU 123456",
    "uom":"EACH",
    "supplier":"A.T. RICHARDSON WINES PTY LTD"
},
{
    "sku":"11111111",
    "description":"SKU 11111111",
    "uom":"DOZEN",
    "supplier":"A.T. RICHARDSON WINES PTY LTD"
}
]'

### Response
for each reponse you have to check the 'error' flag

### All Good
200 OK , if error is false, then your data has been accepted and the client will get an email notifying about the successful import
<pre>{
    "error": false
}</pre>

###### Failed Validation
- 200 OK , if error is true, then check the validations array for the errors.
- In each element of the validation array there would be two pats, the data you sent us in the payload and the description of the error
<pre>{
    "error": true,
    "validations": [
        {
            "Data": {
                "sku": "1234",
                "description": "",
                "uom": "DOZEN",
                "supplier": "A.T. RICHARDSON WINES PTY LTD"
            },
            "Errors": [
                "Description Is Empty"
            ]
        },
        {
            "Data": {
                "sku": "123456",
                "description": "SKU 123456",
                "uom": "EACHSKU",
                "supplier": "A.T. RICHARDSON WINES PTY LTD"
            },
            "Errors": [
                "UOM Not Found"
            ]
        }
    ]
}
</pre>