## **Funds Confirmation v3.1.5 Sandbox API** 
****
### **Introduction to the API**
This API helps you get informed about Funds Availability before initiating a Payment.
The api conforms to the UK Open Banking PSD2 specification.

### **Real Life Use Case Scenario**
Imagine you want to get informed about funds availability before initiating a payment in a card. What can you do about it? Just use this api to get informed.

### **Create Sandbox**
Your first job is to create a sandbox and save your **sandbox-id** in order to be able to **"play"** with the api.

We will create our sandbox by making an **HTTP POST** request to the following URL:
> https://apis.nbg.gr/sandbox/uk.openbanking.fundsconfirmation/oauth2/v3.1.5/sandbox

Request Body:
```json
 {
   "sandbox-id": "my-fundsconfirmations-sandbox"
 }
``` 

**Note: Remember to store *sandbox-id* somewhere in your application, because you will need to provide it as a header
in each api call. Also remember to use the *Client-Id* provided when you create your application in the portal.**

When you create the sandbox application it has some default data.
## **Request Headers**
The following headers are required for every call. In postman they are in the appropriate environment variables.

**Request Headers**:
```
   'accept: application/json'
   'sandbox-id: {{sandboxId}}'  
   'Client-Id: {{clientId}}'   
   'x-fapi-interaction-id: {{$guid}}'
``` 
## **Scenario Request**
You send **POST /funds-confirmation-consents** request to create a new funds availability consent.
> https://apis.nbg.gr/sandbox/uk.openbanking.fundsconfirmation/oauth2/v3.1.5/funds-confirmation-consents

**Request**
```json
{
	"Data": {
		"ExpirationDateTime": "2021-12-31",
		"DebtorAccount": {
			"SchemeName": "UK.OBIE.IBAN",
			"Identification": "GR3201106970000069774934603",
			"Name": "Users Name"
		}
	}
}
``` 

**Response**
```json
{
    "Data": {
        "ConsentId": "cb4da359-c6cb-4d91-9cb5-7a73b41cbc7e",
        "CreationDateTime": "2020-09-03T13:22:22.3Z",
        "Status": "AwaitingAuthorisation",
        "StatusUpdateDateTime": "2020-09-03T13:22:22.3Z",
        "ExpirationDateTime": "2020-12-31T00:00:00Z",
        "DebtorAccount": {
            "SchemeName": "UK.OBIE.IBAN",
            "Identification": "GR3201106970000069774934603",
            "Name": "Users Name"
        }
    },
    "Links": {
        "Self": "https://apis.nbg.gr/sandbox/uk.openbanking.fundsconfirmation/oauth2/v3.1.5/funds-confirmation-consents/cb4da359-c6cb-4d91-9cb5-7a73b41cbc7e"
    },
    "Meta": {
        "TotalPages": 1
    }
}

``` 


Created by **NBG**.\
See more at https://developer.nbg.gr/