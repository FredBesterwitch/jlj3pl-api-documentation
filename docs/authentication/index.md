# Authentication

In order to access our API, you will need to get authenticated, We use Auth0 as a our authentication platform. 

### Keys required
- Client ID: Provided by the Application Administrator
- Client Secret: Provided by the Application Administrator
- API Key : Provided by the Application Administrator


### Getting an access token from the Authentication provider

#### Warning!!!
The below URL's and keys will change, so please sure please make these settings are easily configurable in your applications.

##### CURL
curl --location --request POST 'https://jlj-3pl-dev.au.auth0.com/oauth/token' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'grant_type=client_credentials' \
--data-urlencode 'client_id=YOUR-CLIENT-ID>>' \
--data-urlencode 'client_secret=YOUR-CLIENT-SECRET>>' \
--data-urlencode 'audience=https://localhost:9000'

##### Response
{"access_token":"eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IkxwT3NWTWFjcmlhZTgzTWE1THRNMyJ9.eyJpc3MiOiJodHRwczovL2psai0zcGwtZGV2LmF1LmF1dGgwLmNvbS8iLCJzdWIiOiJMa2lOTGtrZUo5ZzU2aGhhVXBscUZXTW9QN0VMRW53dUBjbGllbnRzIiwiYXVkIjoiaHR0cHM6Ly9sb2NhbGhvc3Q6OTAwMCIsImlhdCI6MTY1MzE5ODdweezMCwiZXhwIjoxNjUzMjg0NTMwLCJhenAiOiJMa2lOTGtrZUo5ZzU2aGhhVXBscUZXTW9QN0VMRW53dSIsImd0eSI6ImNsaWVudC1jcmVkZW50aWFscyJ9.ToT4NwO-jc4PyGo2_3wkPAJNmbZ3eOlF7zmZaoQxpr-nl3zndbDkL8vuBE8i7zhLY9ntcJMd-cMYJBrpN77zGNfNzHhGx0yQc87Vg1loqEKXGkgj_6QqlcMKFVKN4Xs0uC-uSFGanM5EffehnYI1w4uWBe0fIRBnVo3s61wRCFwe7osvljdhd-ivNsk1Tx25G1UouxD3Ra-5YmGbgbsNWdQ2A90quDuCa_dAFPWqbsMoUKI_RMnb4zbkVmCXsSFXW3z3E6ZD2l2ZILcMb2kgFxwh1XvlYEsdlIBsjDlVGE0HU8SEpC2MD-mFlkRvJ146l9SXb-GZOTR77CBuNrHI-A","expires_in":86400,"token_type":"Bearer"}


