
# Import Invoices 

Use this end point to import Invoices 

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
      <td>invoice_number</td>
      <td>Invoice Number</td>
      <td>Must have a Value, cannot be blank and should not exist in the system.</td>
    </tr>
      <tr>
      <td>order_number</td>
      <td>Clients Order Number</td>
      <td>Must have a Value, cannot be blank.</td>
    </tr>
      <tr>
      <td>invoice_date</td>
      <td>Invoice Date</td>
      <td>Must have a Value, cannot be blank, should be in YYYY-MM-DD format.</td>
    </tr>
     <tr>
      <td>customer</td>
      <td>Customer Name</td>
      <td>Must have a Value, cannot be blank.</td>
    </tr>
     <tr>
      <td>address1</td>
      <td>Address 1 Name</td>
      <td>Must have a Value, cannot be blank.</td>
    </tr>
     <tr>
      <td>address2</td>
      <td>Address 2 Name</td>
      <td>can be blank.</td>
    </tr>
     <tr>
      <td>address3</td>
      <td>Address 3 Name</td>
      <td>can be blank.</td>
    </tr>
 <tr>
      <td>city</td>
      <td>City or Suburb</td>
      <td>Must have a Value, cannot be blank.</td>
    </tr> <tr>
      <td>state</td>
      <td>State</td>
      <td>Must have a Value, cannot be blank.</td>
    </tr> <tr>
      <td>postcode</td>
      <td>Postal Code or ZIP</td>
      <td>Must have a Value, cannot be blank.</td>
    </tr> <tr>
      <td>country</td>
      <td>Country</td>
      <td>Must have a Value, cannot be blank.</td>
    </tr>
     </tr> 
     <tr>
      <td>invoicedocument</td>
      <td>Base64 string of the invoice in PDF format</td>
      <td>Must have a Value, cannot be blank and valid PDF.</td>
    </tr>
     <tr>
      <td>items</td>
      <td>Array of Items</td>
      <td>Must have a Value, cannot be blank.</td>
    </tr>
 <tr>
      <td>sku</td>
      <td>SKU of the Line Item</td>
      <td>Must have a Value, cannot be blank and the SKU must be valid.</td>
    </tr>
     <tr>
      <td>quantity</td>
      <td>Quantity - in the UOM quantity setup for this SKU</td>
      <td>Must have a Value and greater than zero</td>
    </tr>

  </thead>
</table>

## Sample Payload
<pre>[
    {
        "invoice_number": "1231",
        "order_number": "1231-01",
        "invoice_date": "2022-04-30",
        "customer": "Customer-1",
        "address1": "7 Skipperstone Glen",
        "address2": "delivery address 2",
        "address3": "delivery address 3",
        "city": "Narre Warren",
        "state": "VIC",
        "postcode": "3805",
        "country": "Australia",
        "invoicedocument":"base64string",
        "items": [
            {
                "sku": "ATR318",
                "quantity": 12
            },
            {
                "sku": "ATRMV18",
                "quantity": 1
            }
        ]
    },
    {
         "invoice_number": "1232",
        "order_number": "1232-01",
        "invoice_date": "2022-04-30",
        "customer": "Customer-2",
        "address1": "7 Skipperstone Glen",
        "address2": "delivery address 2",
        "address3": "delivery address 3",
        "city": "Narre Warren",
        "state": "VIC",
        "postcode": "3805",
        "country": "Australia",
        "invoicedocument":"base64string",
        "items": [
            {
                "sku": "ATRCP18",
                "quantity": 12
            },
            {
                "sku": "ATRPS18",
                "quantity": 1
            }
        ]
    }
]
</pre>


## CURL
curl --location --request POST 'BASE-URL/import/importinvoice' \
--header 'Content-Type: application/json' \
--header 'x-api-key: YOUR-API-KEY' \
--header 'REQUIRED-API-VERSION: 2000' \
--header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IkxwT3NWTWFjcmlhZTgzTWE1THRNMyJ9.eyJpc3MiOiJodHRwczovL2psai0zcGwtZGV2LmF1LmF1dGgwLmNvbS8iLCJzdWIiOiJMa2lOTGtrZUo5ZzU2aGhhVXBscUZXTW9QN0VMRW53dUBjbGllbnRzIiwiYXVkIjoiaHR0cHM6Ly9sb2NhbGhvc3Q6OTAwMCIsImlhdCI6MTY1MzE5OTExMSwiZXhwIjoxNjUzMjg1NTExLCJhenAiOiJMa2lOTGtrZUo5ZzU2aGhhVXBscUZXTW9QN0VMRW53dSIsImd0eSI6ImNsaWVudC1jcmVkZW50aWFscyJ9.D2jt51j8WMcpTbUWJlaVDOKzgkEPFoQaJZVjsi6FpFk_pSgRKp1-bJ_QYPfkPzaz1u0R-t6Ut9xQlDlyL8NVJ7qFc_ilh5AIvZkOm9GQ0_2__G0uZR4AaZ7t2SzJZqwdyawhwbWuXeMmju4jrZuQjk5QlkEbGjawUGrwy8q-8zCYTRD22ts7ojTzgQ03Dyuo-a91zP2rhGGl2Fqb3La30MCJmDOOZuh7kj28lWdzLrTha7Ohnboyx6ngtweh4e-Npp-sbOIQuM4FBRDvOuKJGB4O0vLtUbpB3iBzLN1IkJr4J0rnnatbd1HV8zkJF6ro6pK5Yb2bUk08Sakxl6srdQ' \
--data-raw '[
    {
        "invoice_number": "1231",
        "order_number": "1231-01",
        "invoice_date": "2022-04-30",
        "customer": "Customer-1",
        "address1": "7 Skipperstone Glen",
        "address2": "delivery address 2",
        "address3": "delivery address 3",
        "city": "Narre Warren",
        "state": "VIC",
        "postcode": "3805",
        "country": "Australia",
        "invoicedocument":"",
        "items": [
            {
                "sku": "ATR318",
                "quantity": 12
            },
            {
                "sku": "ATRMV18",
                "quantity": 1
            }
        ]
    },
    {
         "invoice_number": "1232",
        "order_number": "1232-01",
        "invoice_date": "2022-04-30",
        "customer": "Customer-2",
        "address1": "7 Skipperstone Glen",
        "address2": "delivery address 2",
        "address3": "delivery address 3",
        "city": "Narre Warren",
        "state": "VIC",
        "postcode": "3805",
        "country": "Australia",
        "invoicedocument":"",
        "items": [
            {
                "sku": "ATRCP18",
                "quantity": 12
            },
            {
                "sku": "ATRPS18",
                "quantity": 1
            }
        ]
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
<pre>[
    {
        "Data": {
            "ponumber": "",
            "supplier": "",
            "podate": "2022-04-30",
            "expecteddate": "2022-05-01",
            "items": [
                {
                    "sku": "ATR318",
                    "quantity": 0
                },
                {
                    "sku": "ATRMV18",
                    "quantity": 1
                }
            ]
        },
        "Errors": [
            "PO Number Is Empty",
            "Supplier Is Empty",
            "Quantity should be > 0 for  SKU -> ATR318"
        ]
    },
    {
        "Data": {
            "ponumber": "1232",
            "supplier": "Supplier-1",
            "podate": "2022-04-01",
            "expecteddate": "2022-04-03",
            "items": [
                {
                    "sku": "ATRCP18",
                    "quantity": 12
                },
                {
                    "sku": "ATRPS18",
                    "quantity": 1
                }
            ]
        },
        "Errors": [
            "PO Number Exists!"
        ]
    },
    {
        "Data": {
            "ponumber": "1233",
            "supplier": "Supplier-1",
            "podate": "2022-04-30",
            "expecteddate": "",
            "items": [
                {
                    "sku": "ATR319",
                    "quantity": 12
                },
                {
                    "sku": "ATR320",
                    "quantity": 1
                }
            ]
        },
        "Errors": [
            "PO Number Exists!"
        ]
    }
]
</pre>
