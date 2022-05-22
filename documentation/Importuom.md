
# Import UOM - Unit of Measure

Use this end point to import UOM

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
      <td>description</td>
      <td>the description or code used by your client in their SKU UOM E.G. Dozen, Each, Bottle etc.</td>
      <td>Must have a Value, cannot be blank.</td>
    </tr>
        <tr>
      <td>quantity</td>
      <td>12,1,12 etc.</td>
      <td>Must be Numeric and Greater then 0</td>
    </tr>

  </thead>
</table>

## Sample Payload
<pre>[{
    "description":"EACH",
    "qty":1
},
{
    "description":"HALF A DOZEN",
    "qty":6
},
{
    "description":"DOZEN",
    "qty":12
}
]
</pre>


## CURL
curl --location --request POST 'BASE-URL/import/importuom' \
--header 'Content-Type: application/json' \
--header 'x-api-key: YOUR-API-KEY' \
--header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IkxwT3NWTWFjcmlhZTgzTWE1THRNMyJ9.eyJpc3MiOiJodHRwczovL2psai0zcGwtZGV2LmF1LmF1dGgwLmNvbS8iLCJzdWIiOiJMa2lOTGtrZUo5ZzU2aGhhVXBscUZXTW9QN0VMRW53dUBjbGllbnRzIiwiYXVkIjoiaHR0cHM6Ly9sb2NhbGhvc3Q6OTAwMCIsImlhdCI6MTY1MzE5OTExMSwiZXhwIjoxNjUzMjg1NTExLCJhenAiOiJMa2lOTGtrZUo5ZzU2aGhhVXBscUZXTW9QN0VMRW53dSIsImd0eSI6ImNsaWVudC1jcmVkZW50aWFscyJ9.D2jt51j8WMcpTbUWJlaVDOKzgkEPFoQaJZVjsi6FpFk_pSgRKp1-bJ_QYPfkPzaz1u0R-t6Ut9xQlDlyL8NVJ7qFc_ilh5AIvZkOm9GQ0_2__G0uZR4AaZ7t2SzJZqwdyawhwbWuXeMmju4jrZuQjk5QlkEbGjawUGrwy8q-8zCYTRD22ts7ojTzgQ03Dyuo-a91zP2rhGGl2Fqb3La30MCJmDOOZuh7kj28lWdzLrTha7Ohnboyx6ngtweh4e-Npp-sbOIQuM4FBRDvOuKJGB4O0vLtUbpB3iBzLN1IkJr4J0rnnatbd1HV8zkJF6ro6pK5Yb2bUk08Sakxl6srdQ'
--data-raw '[{
    "description":"EACH",
    "qty":1
},
{
    "description":"HALF A DOZEN",
    "qty":6
},
{
    "description":"DOZEN",
    "qty":12
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
                "description": "",
                "qty": 0
            },
            "Errors": [
                "Description Is Empty",
                "Quantity should be > 0"
            ]
        }
    ]
}
</pre>