
# Get Version

The easiest way to check if you can access our API is by checking the Current Version of the API

##### CURL
curl --location --request POST 'BASE-URL/getversion' \
--header 'Content-Type: application/json' \
--header 'x-api-key: YOUR-API-KEY' \
--header 'Authorization: Bearer --Bearer Token--'

##### Response
{
    "version": "7.00"
}