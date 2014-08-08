
#cURL

### Authentication

An Api-Key header is needed authenticate to the Api and will allow you access to read-only operations. The curl option for setting the Api-Key header is:

    -H "Api-Key:{your-api-key}"

### Authorization 

An Authorization header is required to perform download operations. The format of the header is the word **Bearer** followed by the token received from a call to oauth2/token as follows:
	
	curl -d 'grant_type=client_credentials&client_id={your-api-key}&client_secret={your-api-secret}' https://connect.gettyimages.com/oauth2/token

The curl option for setting the Authorization header is:
    
	-H "Authorization: Bearer {your-token}"

### Search

Use the authentication/authorization header option in the operations below depending on the operation used:

##### Images
    curl {headers} https://connect.gettyimages.com/v3/search/images?phrase=kitties

##### Images Creative
    curl {headers} https://connect.gettyimages.com/v3/search/images/creative?phrase=kitties

##### Images Editorial
    curl {headers} https://connect.gettyimages.com/v3/search/images/editorial?phrase=kitties

##### Paging Results
    curl {headers} https://connect.gettyimages.com/v3/search/images?phrase=kitties&page=1&page_size=10

### Image Metadata
NOTE: Some command line tools may require you to quote the url

    curl {headers} https://connect.gettyimages.com/v3/images/83454811,186239980
### Downloads
NOTE: This operation requires an Authorization Header

    curl -H "Api-Key:{your-api-key}" -H "Authorization: Bearer {your-token}" https://connect.gettyimages.com/v3/downloads/83454811 -d "'" -L -o 83454811.jpg

### Countries
This endpoint returns allowed country codes for use with other endpoints. It supports localization.

    curl -i -H "Api-Key:{your-api-key}" -H "Accept-Language:en-US" https://connect.gettyimages.com/v3/countries

### Customers
Thus endpoint creates a new candidate using a JSON file, customers.json, as its POST data.  It supports localiation.

	curl -X -H"Api-Key:t2gw9qk74q69ghgvc6hgn3hr" -H"Accept-Language:en-US" -H"Authorization: Bearer nGnKS1bYYVV6hqlrs+IWl3Lvv...CkxpRElCZz09CjEwMAowCgo=|350" -dcustomer.json "https://connect.gettyimages.com/v3/countries"

The contents of `customers.json`:

	{
	  "email_address": "jtkirk@ussenterprise.sfc",
	  "user_name": "jtkirk"
	  "password": "picard_rules!",
	  "firstName": "James",
	  "middleName": "Tiberius",
	  "lastName": "Kirk",
	  "billing_country_char3iso": "",
	  "marketing_email_opt_in": false,
	  "phone-number": "2065551212"
	}


