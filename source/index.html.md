---
title: '7580: APIs for 3rd Parties - Gateway Layer v0.4'
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - javascript--nodejs: Node.JS
  - ruby: Ruby
  - python: Python
  - java: Java
toc_footers: []
includes: []
search: true
highlight_theme: Monokai_Sublime
headingLevel: 2


---


<h1 id="7580-APIs-for-3rd-Parties---Gateway-Layer">7580: APIs for 3rd Parties - Gateway Layer v0.4</h1>


> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.


**IMPORTANT:** This is a work in progress, and all information may change at any time. Final APIs may look very different. Until there is an official release, these APIs should be seen as unfinished drafts. For more APIs, in even less finished form, see: https://dnb.restlet.no


**Guidelines:**


* The Swagger file should be self-documented, containing as much relevant information as possible.
* camelCase, starting with lowercase: ```customerEngagement```, ```accountNumber```, ```creditCard```, etc.
* Use, and refer to, standards for all properties and values.
* Use examples for all properties and values. Don't force guesses.
* General rule: Response (object) determines endpoint: If response is ```account```, the endpoint should start with ```/accounts```. In cases where this may be up for discussion, multiple endpoints may, for a limited time, be available in order to evaluate.


**Standards:**


APIs must use ISO and RFC standards:


* Country: ISO 3166-1 alpha-2: : https://www.iso.org/standard/63546.html (```NO```, ```GB```, ```US```)
* Currency: ISO 4217: alpha 3-letter upcase: https://www.iso.org/iso-4217-currency-codes.html (```NOK```, ```EUR```, ```USD```)
* Date: ISO 8601:  www.iso.org/iso/home/standards/iso8601.htm (date: ```2018-12-31```, timestamp: ```2018-12-31T23:59:59+01:00```)
* SWIFT BIC: ISO 9362: https://en.wikipedia.org/wiki/ISO_9362 (```DNBANOKKXXX```)
* IBAN ISO 13616:2007: https://www.iso.org/standard/41031.html (```NO9386011117947```)
* MCC: ISO 18245: https://www.iso.org/standard/33365.html (https://github.com/greggles/mcc-codes) (```3514: Hotels/Motels/Inns/Resorts```)


**HTTP Response Codes**


HTTP response codes should be logical: If an ```account``` does not exist, the response should be ```404 Not Found```.  All errors return a relevant HTTP status code and response with an ``error`` containing additional details. 


Success


* ```200: OK``` https://httpstatuses.com/200 / https://tools.ietf.org/html/rfc7231#section-6.3.1     
* ```201: Created``` https://httpstatuses.com/201 / https://tools.ietf.org/html/rfc7231#section-6.3.2


Client Error


* ```400: Bad Request``` https://httpstatuses.com/400 / https://tools.ietf.org/html/rfc7231#section-6.5.1     
* ```401: Unauthorized``` https://httpstatuses.com/401 / https://tools.ietf.org/html/rfc7235#section-3.1      
* ```403: Forbidden``` https://httpstatuses.com/403 / https://tools.ietf.org/html/rfc7231#section-6.5.3     
* ```404: Not Found``` https://httpstatuses.com/404 / https://tools.ietf.org/html/rfc7231#section-6.5.4      
* ```429: Too Many Requests``` https://httpstatuses.com/429 / https://tools.ietf.org/html/rfc6585#section-4  


Server Error


* ```500: Server Error``` https://httpstatuses.com/500 / https://tools.ietf.org/html/rfc7231#section-6.6.1     
* ```503: Service Unavailable``` https://httpstatuses.com/503 / https://tools.ietf.org/html/rfc7231#section-6.6.503
* ```504: Timeout``` https://httpstatuses.com/504 / https://tools.ietf.org/html/rfc7231#section-6.6.5    


**Github**


Full Swagger documentation and links to other generated documentation is available on Github: https://github.com/cloveras/dnb/


Base URLs:


* <a href="https://1gh7oej.restletmocks.net/">https://1gh7oej.restletmocks.net/</a>


<a href="http://developer.dnb.no/terms">Terms of service</a>
Email: <a href="mailto:cl@dnb.no">Christian L�ver�s</a> Web: <a href="https://dnb.no">Christian L�ver�s</a> 


# Authentication


- oAuth2 authentication. 


    - Flow: authorizationCode
    - Authorization URL = [https://api.dnb.no/oauth/authorize](https://api.dnb.no/oauth/authorize)
    - Token URL = [https://api.dnb.no/oauth/token](https://api.dnb.no/oauth/token)


|Scope|Scope Description|
|---|---|
|read|Read|
|write|Write|


- HTTP Authentication, scheme: basic 



<h1 id="7580-APIs-for-3rd-Parties---Gateway-Layer-Customers">Customers</h1>


## get__customers_current


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//customers/current \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//customers/current HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//customers/current',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//customers/current',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//customers/current',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//customers/current', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//customers/current");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /customers/current`


*Get current customer's details*


Get current ```customer``` details. The ```customerId```is included in the context object.


> Example responses


```json
{
  "customerId": "12345678901",
  "customerType": "PERSON",
  "firstName": "Rune",
  "lastName": "Bjerke",
  "companyName": "DNB",
  "address": {
    "postalAddressLine1": "Dronning Eufemias gate 30",
    "postalAddressLine2": "c/o CEO office",
    "postalAddressLine3": "string",
    "postCode": "0191",
    "postCity": "Oslo",
    "postCountry": "NO"
  },
  "email": "example@example.com",
  "phone": "+4791504800",
  "countryOfBirth": "NO",
  "countryCitizenships": [
    "NO"
  ],
  "countryTax": [
    "NO"
  ],
  "customerEngagement": [
    {
      "engagementId": "12345",
      "engagementType": "DEPOSIT",
      "accountNumber": "12345678901",
      "friendlyName": "SAGA MasterCard",
      "corporate": true
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```

<h3 id="get__customers_current-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Customer found|[customer](#schemacustomer)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## get__customers_{customerId}


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//customers/{customerId} \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//customers/{customerId} HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//customers/{customerId}',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//customers/{customerId}',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//customers/{customerId}',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//customers/{customerId}', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//customers/{customerId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /customers/{customerId}`


*Get customer's details by id*


Get ```customer``` details by id.


<h3 id="get__customers_{customerId}-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|customerId|path|string|true|No description|


> Example responses


```json
{
  "customerId": "12345678901",
  "customerType": "PERSON",
  "firstName": "Rune",
  "lastName": "Bjerke",
  "companyName": "DNB",
  "address": {
    "postalAddressLine1": "Dronning Eufemias gate 30",
    "postalAddressLine2": "c/o CEO office",
    "postalAddressLine3": "string",
    "postCode": "0191",
    "postCity": "Oslo",
    "postCountry": "NO"
  },
  "email": "example@example.com",
  "phone": "+4791504800",
  "countryOfBirth": "NO",
  "countryCitizenships": [
    "NO"
  ],
  "countryTax": [
    "NO"
  ],
  "customerEngagement": [
    {
      "engagementId": "12345",
      "engagementType": "DEPOSIT",
      "accountNumber": "12345678901",
      "friendlyName": "SAGA MasterCard",
      "corporate": true
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__customers_{customerId}-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Customer found|[customer](#schemacustomer)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


<h1 id="7580-APIs-for-3rd-Parties---Gateway-Layer-Accounts">Accounts</h1>


## get__accounts


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//accounts \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//accounts HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//accounts',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//accounts',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//accounts',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//accounts', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//accounts");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /accounts`


*Get all accounts for current user*


> Example responses


```json
[
  {
    "accountNumber": "12345678901",
    "type": "DEPOSIT",
    "accountName": "Standard account",
    "balanceAvailable": 100.01,
    "accountDetails": {
      "IBAN": "NO9386011117947",
      "BIC": "DNBANOKKXXX",
      "currency": "NOK",
      "created": "2018-12-31T23:59:59+01",
      "updated": "2018-12-31T23:59:59+01",
      "accountInterestDetails": {
        "interestRate": 2.01,
        "earnedInterestToDate": 100.01,
        "accruedInterestAndFeesToDate": 1.01,
        "feesToDate": 5.01,
        "accruedInterestFromLastYear": 500.01
      }
    }
  }
]
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```



<h3 id="get__accounts-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Status 200|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Status 400|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Status 404|[error](#schemaerror)|


<h3 id="get__accounts-responseschema">Response Schema</h3>


Status Code **200**


|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[account](#schemaaccount)]|false|No description|
|» accountNumber|string|true|11 digits. Bank, etc can be determined from this: https://no.wikipedia.org/wiki/Kontonummer|
|» type|string|true|Any type of account.|
|» accountName|string|false|Friendly name for the account:|
|» balanceAvailable|number|true|No description|
|» accountDetails|[accountDetails](#schemaaccountdetails)|false|Details for an ```account```, with optional reference to ```accountDetails```.  IBAN help: http://www.xe.com/ibancalculator/sample/?ibancountry=norway|
|»» IBAN|string|true|ISO 13616:2007: https://www.iso.org/standard/41031.html No whitespace|
|»» BIC|string|true|ISO 9362: https://en.wikipedia.org/wiki/ISO_9362|
|»» currency|string|true|Currency: ISO 4217: alpha 3-letter upcase. https://www.iso.org/iso-4217-currency-codes.html|
|»» created|string(date-time)|true|ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|»» updated|string(date-time)|true|ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|»» accountInterestDetails|[accountInterestDetails](#schemaaccountinterestdetails)|false|Details about an the interest for an ```account```.|
|»»» interestRate|number|true|No description|
|»»» earnedInterestToDate|number|true|No description|
|»»» accruedInterestAndFeesToDate|number|true|No description|
|»»» feesToDate|number|true|No description|
|»»» accruedInterestFromLastYear|number|false|No description|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## get__accounts_{accountNumber}


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//accounts/{accountNumber} \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//accounts/{accountNumber} HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//accounts/{accountNumber}',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//accounts/{accountNumber}',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//accounts/{accountNumber}',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//accounts/{accountNumber}', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//accounts/{accountNumber}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /accounts/{accountNumber}`


*Get account details*


Returns Account.


<h3 id="get__accounts_{accountNumber}-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|accountNumber|path|string|true|No description|


> Example responses


```json
{
  "IBAN": "NO9386011117947",
  "BIC": "DNBANOKKXXX",
  "currency": "NOK",
  "created": "2018-12-31T23:59:59+01",
  "updated": "2018-12-31T23:59:59+01",
  "accountInterestDetails": {
    "interestRate": 2.01,
    "earnedInterestToDate": 100.01,
    "accruedInterestAndFeesToDate": 1.01,
    "feesToDate": 5.01,
    "accruedInterestFromLastYear": 500.01
  }
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__accounts_{accountNumber}-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|[accountDetails](#schemaaccountdetails)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|customerId unknown|[error](#schemaerror)|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## get__accounts_{accountNumber}_balances


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//accounts/{accountNumber}/balances \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//accounts/{accountNumber}/balances HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//accounts/{accountNumber}/balances',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//accounts/{accountNumber}/balances',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//accounts/{accountNumber}/balances',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//accounts/{accountNumber}/balances', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//accounts/{accountNumber}/balances");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /accounts/{accountNumber}/balances`


*Get account balances*


<h3 id="get__accounts_{accountNumber}_balances-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|accountNumber|path|string|true|No description|


> Example responses


```json
{
  "accountNumber": "12345678901",
  "amountAvailable": 100.01,
  "amountBooked": 100.01,
  "timestamp": "2018-12-31T23:59:59+01"
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
counts_{accountNumber}_balances-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|[accountBalance](#schemaaccountbalance)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## get__accounts_{accountNumber}_transactions


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//accounts/{accountNumber}/transactions \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//accounts/{accountNumber}/transactions HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//accounts/{accountNumber}/transactions',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//accounts/{accountNumber}/transactions',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//accounts/{accountNumber}/transactions',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//accounts/{accountNumber}/transactions', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//accounts/{accountNumber}/transactions");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```

`GET /accounts/{accountNumber}/transactions`


*Get transaction list for account*


**Note:** Duplicates endpoint in ```Transactions```. For evaluation purposes. 


Optional query parameters below. Note: Sorting and filtering affects backend, and may change.


* SortOrder: "ASC", "DESC"
* DateFrom: "YYYY-MM-DD": ISO 8601: www.iso.org/iso/home/standards/iso8601.htm
* DateTo: "YYYY-MM-DD": ISO 8601: www.iso.org/iso/home/standards/iso8601.htm
* AmountMinimum: Include amount from (and including) this amount.
* AmountMaximum: Include amount from (and including) this amount.
* MCC: Include only this MCC code: ISO 18245: https://www.iso.org/standard/33365.html 
* FreeText: Filter by free text


<h3 id="get__accounts_{accountNumber}_transactions-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|SortOrder|query|string|false|Ascending, descending|
|DateFrom|query|string(date)|false|Filter for start date (included). ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|DateTo|query|string(date)|false|Filter for end date (included). ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|AmountMinimum|query|number|false|Filter for minimum amount (included). No decimals.|
|AmountMaximum|query|string|false|Filter for maximum amount (included). No decimals.|
|MCC|query|string|false|Filter for MCC. Use code only.|
|FreeText|query|string|false|Filter for free text. Case insensitive.|
|IncludePending|query|boolean|false|Should pending transactions be included?|
|accountNumber|path|string|true|No description|


> Example responses


```json
[
  {
    "transactionId": "12345",
    "amount": "1500.00",
    "currencyValue": "90.00",
    "currency": "NOK",
    "dateBooking": "2018-13-12",
    "dateValue": "2018-12-31",
    "description": "Lunch at The Restaurant at the End of the Universe",
    "status": "BOOKED",
    "merchantName": "Coffee Shop ChainName, shop number 10",
    "MCC": "3514: Hotels/Motels/Inns/Resorts"
  }
]
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```

<h3 id="get__accounts_{accountNumber}_transactions-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<h3 id="get__accounts_{accountNumber}_transactions-responseschema">Response Schema</h3>


Status Code **200**


|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[transaction](#schematransaction)]|false|No description|
|» transactionId|string|true|No description|
|» amount|string|true|No description|
|» currencyValue|string|false|Amount in foreign currency (if relevant)|
|» currency|string|false|If not the currency of the account/card.|
|» dateBooking|string(date)|true|YYYY-MM-DD: Date: ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|» dateValue|string(date)|false|YYYY-MM. ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|» description|string|false|Descriptive text for the transaction.|
|» status|string|false|Booked, reserved, and, if this is to be merged with ```payment```: Completed (or something similar, to indicate that this has, in fact, been processed and finalized)|
|» merchantName|string|false|Name of merchant. With a merhant register, this could be replaced with a (for now, non-existant) ```merchantId```.|
|» MCC|string|false|MCC: Number and "combined description". ISO 18245: https://www.iso.org/standard/33365.html|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>

## get__accounts_{accountNumber}_transactions-{transactionId}


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//accounts/{accountNumber}/transactions/{transactionId} \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//accounts/{accountNumber}/transactions/{transactionId} HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//accounts/{accountNumber}/transactions/{transactionId}',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//accounts/{accountNumber}/transactions/{transactionId}',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//accounts/{accountNumber}/transactions/{transactionId}',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//accounts/{accountNumber}/transactions/{transactionId}', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//accounts/{accountNumber}/transactions/{transactionId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /accounts/{accountNumber}/transactions/{transactionId}`


*Get transaction specified by id*


**Note:** Duplicates endpoint in ```Transactions```. For evaluation purposes. 


<h3 id="get__accounts_{accountNumber}_transactions_{transactionId}-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|accountNumber|path|string|true|No description|
|transactionId|path|string|true|No description|


> Example responses


```json
{
  "transactionId": "12345",
  "amount": "1500.00",
  "currencyValue": "90.00",
  "currency": "NOK",
  "dateBooking": "2018-13-12",
  "dateValue": "2018-12-31",
  "description": "Lunch at The Restaurant at the End of the Universe",
  "status": "BOOKED",
  "merchantName": "Coffee Shop ChainName, shop number 10",
  "MCC": "3514: Hotels/Motels/Inns/Resorts"
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__accounts_{accountNumber}_transactions_{transactionId}-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|[transaction](#schematransaction)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## get__accounts_{accountNumber}_payments_due


> Code samples

```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//accounts/{accountNumber}/payments/due \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//accounts/{accountNumber}/payments/due HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//accounts/{accountNumber}/payments/due',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//accounts/{accountNumber}/payments/due',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//accounts/{accountNumber}/payments/due',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//accounts/{accountNumber}/payments/due', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//accounts/{accountNumber}/payments/due");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /accounts/{accountNumber}/payments/due`


*Get due payments for account by date range*


<h3 id="get__accounts_{accountNumber}_payments_due-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|startDate|query|string(date)|false|YYYY-MM-DD�: ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|stopDate|query|string|false|YYYY-MM-DD�: ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|accountNumber|path|string|true|No description|


> Example responses


```json
[
  {
    "paymentId": "123456789",
    "debitAccount": "12345678901",
    "creditAccount": "12345678901",
    "amount": 1500.01,
    "type": "TBD1",
    "date": "2018-31-12",
    "status": "PAID",
    "paymentDetails": {
      "invoiceReference": "12345678901"
    }
  }
]
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```

<h3 id="get__accounts_{accountNumber}_payments_due-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Status 200|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Status 400|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Status 404|[error](#schemaerror)|


<h3 id="get__accounts_{accountNumber}_payments_due-responseschema">Response Schema</h3>


Status Code **200**


|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[payment](#schemapayment)]|false|No description|
|» paymentId|string|true|No description|
|» debitAccount|string|true|No description|
|» creditAccount|string|true|No description|
|» amount|number|true|No description|
|» type|string|true|TBD|
|» date|string(date)|false|YYYY-MM-DD: Date: ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|» status|string|true|Statuses TBD|
|» paymentDetails|[paymentDetails](#schemapaymentdetails)|false|More details about a payment. Some payment types have more data than others.|
|»» invoiceReference|string|false|Used for eFaktura|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//accounts/{accountNumber}/payments/due/{paymentId} \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//accounts/{accountNumber}/payments/due/{paymentId} HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//accounts/{accountNumber}/payments/due/{paymentId}',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//accounts/{accountNumber}/payments/due/{paymentId}',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//accounts/{accountNumber}/payments/due/{paymentId}',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//accounts/{accountNumber}/payments/due/{paymentId}', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//accounts/{accountNumber}/payments/due/{paymentId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /accounts/{accountNumber}/payments/due/{paymentId}`


*Get details for a payment for an account*


<h3 id="get__accounts_{accountNumber}_payments_due_{paymentId}-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|accountNumber|path|string|true|No description|
|paymentId|path|string|true|No description|


> Example responses


```json
{
  "paymentId": "123456789",
  "debitAccount": "12345678901",
  "creditAccount": "12345678901",
  "amount": 1500.01,
  "type": "TBD1",
  "date": "2018-31-12",
  "status": "PAID",
  "paymentDetails": {
    "invoiceReference": "12345678901"
  }
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```

<h3 id="get__accounts_{accountNumber}_payments_due_{paymentId}-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Status 200|[payment](#schemapayment)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Status 400|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Status 404|[error](#schemaerror)|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


<h1 id="7580-APIs-for-3rd-Parties---Gateway-Layer-Cards">Cards</h1>


## get__cards


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//cards \
  -H 'Accept: application/json'


```

```http
GET https://1gh7oej.restletmocks.net//cards HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//cards',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//cards',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//cards',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//cards', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//cards");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /cards`


*Get cards for current customer*


List over the current ```customer```'s debet and credit cards. 


> Example responses


```json
[
  {
    "cardId": "12345",
    "maskedCardNumber": "XXXX XXXX XXXX 1234",
    "cardType": "VISA",
    "cardGroup": "DEBIT",
    "accountNumber": "012345678901",
    "cardStatus": "NORMAL",
    "blockCode": "12345",
    "expiryDate": "2018-12",
    "debitBalance": {
      "accountNumber": "12345678901",
      "amountAvailable": 100.01,
      "amountBooked": 100.01,
      "timestamp": "2018-12-31T23:59:59+01"
    },
    "creditBalance": {
      "currency": "NOK",
      "creditLimit": "100000.00",
      "amountAvailable": 90000.01,
      "amountBook": 90000.01,
      "timestamp": "2018-12-31T23:59:59+01:00"
    }
  }
]
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__cards-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<h3 id="get__cards-responseschema">Response Schema</h3>


Status Code **200**


|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[card](#schemacard)]|false|No description|
|» cardId|string|true|No description|
|» maskedCardNumber|string|true|16 characters: Twelve "X", and the last four digits ofr the card number. 4x4 nubers with whitespace.|
|» cardType|string|true|Visa, MasterCard, American Express, etc|
|» cardGroup|string|true|Debit or credit.|
|» accountNumber|string|true|Both for debit and credit cards|
|» cardStatus|string|true|Normal, active, blocked|
|» blockCode|string|false|If blocked: Code for the blocking reason.|
|» expiryDate|string(date)|true|YYYY-MM. ISO 8601: https://www.iso.org/iso-8601-date-and-time-format.html|
|» debitBalance|[accountBalance](#schemaaccountbalance)|false|Balances for an ```account```. See also: ```cardBalance```.|
|»» accountNumber|string|true|11 digits|
|»» amountAvailable|number|true|Amount available|
|»» amountBooked|number|true|Booked amount available|
|»» timestamp|string(date-time)|true|ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|» creditBalance|[cardBalance](#schemacardbalance)|false|Used by ```card```. See also: ```accountBalance```.|
|»» currency|string|true|ISO 4217: alpha 3-letter upcase: https://www.iso.org/iso-4217-currency-codes.html|
|»» creditLimit|string|false|No description|
|»» amountAvailable|number|true|Debit: The amount in the ```account```.Credit: The limit minus the registered payments.|
|»» amountBook|number|false|No description|
|»» timestamp|string(date-time)|false|ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## get__cards_{cardId}_details


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//cards/{cardId}/details \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//cards/{cardId}/details HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//cards/{cardId}/details',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//cards/{cardId}/details',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//cards/{cardId}/details',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//cards/{cardId}/details', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//cards/{cardId}/details");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /cards/{cardId}/details`


*Get card details*


Includes balance and credit limit (when applicable).


<h3 id="get__cards_{cardId}_details-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|cardId|path|string|true|No description|


> Example responses


```json
{
  "cardId": "12345",
  "maskedCardNumber": "XXXX XXXX XXXX 1234",
  "cardType": "VISA",
  "cardGroup": "DEBIT",
  "accountNumber": "012345678901",
  "cardStatus": "NORMAL",
  "blockCode": "12345",
  "expiryDate": "2018-12",
  "debitBalance": {
    "accountNumber": "12345678901",
    "amountAvailable": 100.01,
    "amountBooked": 100.01,
    "timestamp": "2018-12-31T23:59:59+01"
  },
  "creditBalance": {
    "currency": "NOK",
    "creditLimit": "100000.00",
    "amountAvailable": 90000.01,
    "amountBook": 90000.01,
    "timestamp": "2018-12-31T23:59:59+01:00"
  }
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__cards_{cardId}_details-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|[card](#schemacard)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## get__cards_{cardId}_transactions


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//cards/{cardId}/transactions \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//cards/{cardId}/transactions HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//cards/{cardId}/transactions',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//cards/{cardId}/transactions',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//cards/{cardId}/transactions',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//cards/{cardId}/transactions', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//cards/{cardId}/transactions");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /cards/{cardId}/transactions`


*Get card transactions*


**Note:** Duplicates endpoint in ```Transactions```. For evaluation purposes. 


Transactionlist for the customers creditcard


<h3 id="get__cards_{cardId}_transactions-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|cardId|path|string|true|No description|


> Example responses


```json
[
  {
    "transactionId": "12345",
    "amount": "1500.00",
    "currencyValue": "90.00",
    "currency": "NOK",
    "dateBooking": "2018-13-12",
    "dateValue": "2018-12-31",
    "description": "Lunch at The Restaurant at the End of the Universe",
    "status": "BOOKED",
    "merchantName": "Coffee Shop ChainName, shop number 10",
    "MCC": "3514: Hotels/Motels/Inns/Resorts"
  }
]
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__cards_{cardId}_transactions-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<h3 id="get__cards_{cardId}_transactions-responseschema">Response Schema</h3>


Status Code **200**


|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[transaction](#schematransaction)]|false|No description|
|» transactionId|string|true|No description|
|» amount|string|true|No description|
|» currencyValue|string|false|Amount in foreign currency (if relevant)|
|» currency|string|false|If not the currency of the account/card.|
|» dateBooking|string(date)|true|YYYY-MM-DD: Date: ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|» dateValue|string(date)|false|YYYY-MM. ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|» description|string|false|Descriptive text for the transaction.|
|» status|string|false|Booked, reserved, and, if this is to be merged with ```payment```: Completed (or something similar, to indicate that this has, in fact, been processed and finalized)|
|» merchantName|string|false|Name of merchant. With a merhant register, this could be replaced with a (for now, non-existant) ```merchantId```.|
|» MCC|string|false|MCC: Number and "combined description". ISO 18245: https://www.iso.org/standard/33365.html|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## patch__cards_{cardId}_block


> Code samples


```shell
# You can also use wget
curl -X PATCH https://1gh7oej.restletmocks.net//cards/{cardId}/block \
  -H 'Accept: application/json'


```


```http
PATCH https://1gh7oej.restletmocks.net//cards/{cardId}/block HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//cards/{cardId}/block',
  method: 'patch',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//cards/{cardId}/block',
{
  method: 'PATCH',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.patch 'https://1gh7oej.restletmocks.net//cards/{cardId}/block',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.patch('https://1gh7oej.restletmocks.net//cards/{cardId}/block', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//cards/{cardId}/block");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`PATCH /cards/{cardId}/block`


*Block card*


Aviability for end-customet to block a debit or credit card. (Not Cresco Cards)


<h3 id="patch__cards_{cardId}_block-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|cardId|path|string|true|No description|


> Example responses


```json
{
  "value": "ReasonCode"
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


-|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The card is now blocked|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<h3 id="patch__cards_{cardId}_block-responseschema">Response Schema</h3>


Status Code **200**


|Name|Type|Required|Description|
|---|---|---|---|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## patch__cards_{cardId}_unblock


> Code samples


```shell
# You can also use wget
curl -X PATCH https://1gh7oej.restletmocks.net//cards/{cardId}/unblock \
  -H 'Accept: application/json'


```


```http
PATCH https://1gh7oej.restletmocks.net//cards/{cardId}/unblock HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//cards/{cardId}/unblock',
  method: 'patch',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//cards/{cardId}/unblock',
{
  method: 'PATCH',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.patch 'https://1gh7oej.restletmocks.net//cards/{cardId}/unblock',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.patch('https://1gh7oej.restletmocks.net//cards/{cardId}/unblock', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//cards/{cardId}/unblock");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`PATCH /cards/{cardId}/unblock`


*Unblock card*


Unblock a blocked ```card```.


<h3 id="patch__cards_{cardId}_unblock-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|cardId|path|string|true|No description|

> Example responses


```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```

<h3 id="patch__cards_{cardId}_unblock-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Unblocked|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## get__cards_{cardId}_invoice-{year}-{month}

> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//cards/{cardId}/invoice/{year}/{month} \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//cards/{cardId}/invoice/{year}/{month} HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//cards/{cardId}/invoice/{year}/{month}',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//cards/{cardId}/invoice/{year}/{month}',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//cards/{cardId}/invoice/{year}/{month}',
  params: {
  }, headers: headers


p JSON.parse(result)


```

```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//cards/{cardId}/invoice/{year}/{month}', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//cards/{cardId}/invoice/{year}/{month}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /cards/{cardId}/invoice/{year}/{month}`


*Get card invoice*


Get card invoice form chosen month


<h3 id="get__cards_{cardId}_invoice_{year}_{month}-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|cardId|path|string|true|No description|
|year|path|string|true|YYYY|
|month|path|string|true|MM, where January is 01|


> Example responses


```json
{
  "card": {
    "cardId": "12345",
    "maskedCardNumber": "XXXX XXXX XXXX 1234",
    "cardType": "VISA",
    "cardGroup": "DEBIT",
    "accountNumber": "012345678901",
    "cardStatus": "NORMAL",
    "blockCode": "12345",
    "expiryDate": "2018-12",
    "debitBalance": {
      "accountNumber": "12345678901",
      "amountAvailable": 100.01,
      "amountBooked": 100.01,
      "timestamp": "2018-12-31T23:59:59+01"
    },
    "creditBalance": {
      "currency": "NOK",
      "creditLimit": "100000.00",
      "amountAvailable": 90000.01,
      "amountBook": 90000.01,
      "timestamp": "2018-12-31T23:59:59+01:00"
    }
  },
  "year": "2018",
  "month": "01",
  "amount": "100.00",
  "dueDate": "2018-12-31",
  "accountNumber": "012345678901",
  "KID": "42",
  "transactions": [
    {
      "transactionId": "12345",
      "amount": "1500.00",
      "currencyValue": "90.00",
      "currency": "NOK",
      "dateBooking": "2018-13-12",
      "dateValue": "2018-12-31",
      "description": "Lunch at The Restaurant at the End of the Universe",
      "status": "BOOKED",
      "merchantName": "Coffee Shop ChainName, shop number 10",
      "MCC": "3514: Hotels/Motels/Inns/Resorts"
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__cards_{cardId}_invoice_{year}_{month}-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|[cardInvoice](#schemacardinvoice)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


<h1 id="7580-APIs-for-3rd-Parties---Gateway-Layer-Payments">Payments</h1>



## post__payments


> Code samples


```shell
# You can also use wget
curl -X POST https://1gh7oej.restletmocks.net//payments \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'


```


```http
POST https://1gh7oej.restletmocks.net//payments HTTP/1.1
Host: 1gh7oej.restletmocks.net
Content-Type: application/json
Accept: application/json


```


```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//payments',
  method: 'post',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "type": "KID",
  "debitAccountNumber": "12345678901",
  "creditAccountNumber": "12345678901",
  "amount": "1500.00",
  "paymentDate": "2018-12-31",
  "message": "35298562958265982749",
  "initiator": "DNB"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//payments',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}


result = RestClient.post 'https://1gh7oej.restletmocks.net//payments',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}


r = requests.post('https://1gh7oej.restletmocks.net//payments', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//payments");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`POST /payments`


*Initiate payment*


Domestic payment with KID or message.


Returns HTTP 201 and the ```PaymentId``` of successfully created payment.


> Body parameter


```json
{
  "type": "KID",
  "debitAccountNumber": "12345678901",
  "creditAccountNumber": "12345678901",
  "amount": "1500.00",
  "paymentDate": "2018-12-31",
  "message": "35298562958265982749",
  "initiator": "DNB"
}
```


<h3 id="post__payments-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[paymentInitiation](#schemapaymentinitiation)|true|No description|


> Example responses


```json
{
  "value": "1234567890"
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="post__payments-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|string|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## get__payments_{accountNumber}_due


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//payments/{accountNumber}/due?accountNumber=string \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//payments/{accountNumber}/due?accountNumber=string HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//payments/{accountNumber}/due',
  method: 'get',
  data: '?accountNumber=string',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//payments/{accountNumber}/due?accountNumber=string',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//payments/{accountNumber}/due',
  params: {
  'accountNumber' => 'string'
}, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//payments/{accountNumber}/due', params={
  'accountNumber': '12345678901'
}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//payments/{accountNumber}/due?accountNumber=string");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /payments/{accountNumber}/due`


*Get due payments by date range*


Gets all due ```payment```s, both domestic and international.


<h3 id="get__payments_{accountNumber}_due-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|accountNumber|query|string|true|No description|
|startDate|query|string(date)|false|"YYYY-MM-DD": ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|stopDate|query|string(date)|false|"YYYY-MM-DD": ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|accountNumber|path|string|true|No description|


> Example responses


```json
[
  {
    "paymentId": "123456789",
    "debitAccount": "12345678901",
    "creditAccount": "12345678901",
    "amount": 1500.01,
    "type": "TBD1",
    "date": "2018-31-12",
    "status": "PAID",
    "paymentDetails": {
      "invoiceReference": "12345678901"
    }
  }
]
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__payments_{accountNumber}_due-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<h3 id="get__payments_{accountNumber}_due-responseschema">Response Schema</h3>


Status Code **200**

|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[payment](#schemapayment)]|false|No description|
|» paymentId|string|true|No description|
|» debitAccount|string|true|No description|
|» creditAccount|string|true|No description|
|» amount|number|true|No description|
|» type|string|true|TBD|
|» date|string(date)|false|YYYY-MM-DD: Date: ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|» status|string|true|Statuses TBD|
|» paymentDetails|[paymentDetails](#schemapaymentdetails)|false|More details about a payment. Some payment types have more data than others.|
|»» invoiceReference|string|false|Used for eFaktura|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## get__payments_{accountNumber}_due{paymentId}


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//payments/{accountNumber}/due/{paymentId} \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//payments/{accountNumber}/due/{paymentId} HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//payments/{accountNumber}/due/{paymentId}',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//payments/{accountNumber}/due/{paymentId}',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//payments/{accountNumber}/due/{paymentId}',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//payments/{accountNumber}/due/{paymentId}', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//payments/{accountNumber}/due/{paymentId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /payments/{accountNumber}/due/{paymentId}`


*Get due payment by payment id*


Returns ```payment,``` complete with with ```paymentDetails```.


This endpoint may change, as it is offers the same as ```accounts/{accountNumber}/payments/due/{paymentId}```, and the placement is not decided yet.


<h3 id="get__payments_{accountNumber}_due_{paymentId}-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|accountNumber|path|string|true|No description|
|paymentId|path|string|true|No description|


> Example responses


```json
{
  "paymentId": "123456789",
  "debitAccount": "12345678901",
  "creditAccount": "12345678901",
  "amount": 1500.01,
  "type": "TBD1",
  "date": "2018-31-12",
  "status": "PAID",
  "paymentDetails": {
    "invoiceReference": "12345678901"
  }
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__payments_{accountNumber}_due_{paymentId}-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|[payment](#schemapayment)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## delete__payments_{paymentId}


> Code samples


```shell
# You can also use wget
curl -X DELETE https://1gh7oej.restletmocks.net//payments/{paymentId}


```


```http
DELETE https://1gh7oej.restletmocks.net//payments/{paymentId} HTTP/1.1
Host: 1gh7oej.restletmocks.net


```


```javascript


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//payments/{paymentId}',
  method: 'delete',


  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


fetch('https://1gh7oej.restletmocks.net//payments/{paymentId}',
{
  method: 'DELETE'


})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


result = RestClient.delete 'https://1gh7oej.restletmocks.net//payments/{paymentId}',
  params: {
  }


p JSON.parse(result)


```


```python
import requests


r = requests.delete('https://1gh7oej.restletmocks.net//payments/{paymentId}', params={


)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//payments/{paymentId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`DELETE /payments/{paymentId}`


*Delete payment by id*


<h3 id="delete__payments_{paymentId}-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|paymentId|path|string|true|No description|


<h3 id="delete__payments_{paymentId}-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Gone forever|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Status 400|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Status 401|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Status 403|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Unknown paymentId|None|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## patch__payments_{paymentId}


> Code samples


```shell
# You can also use wget
curl -X PATCH https://1gh7oej.restletmocks.net//payments/{paymentId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'


```


```http
PATCH https://1gh7oej.restletmocks.net//payments/{paymentId} HTTP/1.1
Host: 1gh7oej.restletmocks.net
Content-Type: application/json
Accept: application/json


```


```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//payments/{paymentId}',
  method: 'patch',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');
const inputBody = '[
  "string"
]';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//payments/{paymentId}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}


result = RestClient.patch 'https://1gh7oej.restletmocks.net//payments/{paymentId}',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}


r = requests.patch('https://1gh7oej.restletmocks.net//payments/{paymentId}', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//payments/{paymentId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`PATCH /payments/{paymentId}`


*Update existing payment*


A payment can be updatet until due dtae. 
Possible to udate :
* Date ("YYYY-MM-DD", ISO 8601: www.iso.org/iso/home/standards/iso8601.htm)
* Amount
* Status (deactivate, reactivate)


Returns the updated Payment.


> Body parameter


```json
[
  "string"
]
```


<h3 id="patch__payments_{paymentId}-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|array[string]|true|No description|
|paymentId|path|string|true|No description|


> Example responses


```json
{
  "paymentId": "123456789",
  "debitAccount": "12345678901",
  "creditAccount": "12345678901",
  "amount": 1500.01,
  "type": "TBD1",
  "date": "2018-31-12",
  "status": "PAID",
  "paymentDetails": {
    "invoiceReference": "12345678901"
  }
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="patch__payments_{paymentId}-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Changed|[payment](#schemapayment)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


<h1 id="7580-APIs-for-3rd-Parties---Gateway-Layer-Transactions">Transactions</h1>



## get__transactions_accounts_{accountNumber}


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//transactions/accounts/{accountNumber} \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//transactions/accounts/{accountNumber} HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//transactions/accounts/{accountNumber}',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//transactions/accounts/{accountNumber}',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//transactions/accounts/{accountNumber}',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//transactions/accounts/{accountNumber}', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//transactions/accounts/{accountNumber}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /transactions/accounts/{accountNumber}`


*Get transactions for account*


**Note:** Duplicates ```Transactions```endpoint in ```Accounts```. For evaluation purposes. 


Optional query parameters below. Note: Sorting and filtering affects backend, and may change.


* SortOrder: "ASC", "DESC"
* DateFrom: "YYYY-MM-DD": ISO 8601: www.iso.org/iso/home/standards/iso8601.htm
* DateTo: "YYYY-MM-DD": ISO 8601: www.iso.org/iso/home/standards/iso8601.htm
* AmountMinimum: Include amount from (and including) this amount.
* AmountMaximum: Include amount from (and including) this amount.
* MCC: Include only this MCC code: ISO 18245: https://www.iso.org/standard/33365.html 
* FreeText: Filter by free text


<h3 id="get__transactions_accounts_{accountNumber}-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|SortOrder|query|string|false|Ascending, descending|
|DateFrom|query|string(date)|false|Filter for start date (included). ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|DateTo|query|string(date)|false|Filter for end date (included). ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|AmountMinimum|query|number|false|Filter for minimum amount (included). No decimals.|
|AmountMaximum|query|string|false|Filter for maximum amount (included). No decimals.|
|MCC|query|string|false|Filter for MCC. Use code only.|
|FreeText|query|string|false|Filter for free text. Case insensitive.|
|IncludePending|query|boolean|false|Should pending transactions be included?|
|accountNumber|path|string|true|No description|


> Example responses


```json
[
  {
    "transactionId": "12345",
    "amount": "1500.00",
    "currencyValue": "90.00",
    "currency": "NOK",
    "dateBooking": "2018-13-12",
    "dateValue": "2018-12-31",
    "description": "Lunch at The Restaurant at the End of the Universe",
    "status": "BOOKED",
    "merchantName": "Coffee Shop ChainName, shop number 10",
    "MCC": "3514: Hotels/Motels/Inns/Resorts"
  }
]
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__transactions_accounts_{accountNumber}-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<h3 id="get__transactions_accounts_{accountNumber}-responseschema">Response Schema</h3>


Status Code **200**


|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[transaction](#schematransaction)]|false|No description|
|» transactionId|string|true|No description|
|» amount|string|true|No description|
|» currencyValue|string|false|Amount in foreign currency (if relevant)|
|» currency|string|false|If not the currency of the account/card.|
|» dateBooking|string(date)|true|YYYY-MM-DD: Date: ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|» dateValue|string(date)|false|YYYY-MM. ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|» description|string|false|Descriptive text for the transaction.|
|» status|string|false|Booked, reserved, and, if this is to be merged with ```payment```: Completed (or something similar, to indicate that this has, in fact, been processed and finalized)|
|» merchantName|string|false|Name of merchant. With a merhant register, this could be replaced with a (for now, non-existant) ```merchantId```.|
|» MCC|string|false|MCC: Number and "combined description". ISO 18245: https://www.iso.org/standard/33365.html|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## get__transactions_accounts_{accountNumber}_{transactionId}


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//transactions/accounts/{accountNumber}/{transactionId} \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//transactions/accounts/{accountNumber}/{transactionId} HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//transactions/accounts/{accountNumber}/{transactionId}',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//transactions/accounts/{accountNumber}/{transactionId}',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//transactions/accounts/{accountNumber}/{transactionId}',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//transactions/accounts/{accountNumber}/{transactionId}', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//transactions/accounts/{accountNumber}/{transactionId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /transactions/accounts/{accountNumber}/{transactionId}`


*Get transaction for account by transaction id*


**Note:** Duplicates ```Transactions```endpoint in ```Accounts```. For evaluation purposes. 


<h3 id="get__transactions_accounts_{accountNumber}_{transactionId}-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|accountNumber|path|string|true|No description|
|transactionId|path|string|true|No description|


> Example responses


```json
[
  {
    "transactionId": "12345",
    "amount": "1500.00",
    "currencyValue": "90.00",
    "currency": "NOK",
    "dateBooking": "2018-13-12",
    "dateValue": "2018-12-31",
    "description": "Lunch at The Restaurant at the End of the Universe",
    "status": "BOOKED",
    "merchantName": "Coffee Shop ChainName, shop number 10",
    "MCC": "3514: Hotels/Motels/Inns/Resorts"
  }
]
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__transactions_accounts_{accountNumber}_{transactionId}-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<h3 id="get__transactions_accounts_{accountNumber}_{transactionId}-responseschema">Response Schema</h3>


Status Code **200**


|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[transaction](#schematransaction)]|false|No description|
|» transactionId|string|true|No description|
|» amount|string|true|No description|
|» currencyValue|string|false|Amount in foreign currency (if relevant)|
|» currency|string|false|If not the currency of the account/card.|
|» dateBooking|string(date)|true|YYYY-MM-DD: Date: ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|» dateValue|string(date)|false|YYYY-MM. ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|» description|string|false|Descriptive text for the transaction.|
|» status|string|false|Booked, reserved, and, if this is to be merged with ```payment```: Completed (or something similar, to indicate that this has, in fact, been processed and finalized)|
|» merchantName|string|false|Name of merchant. With a merhant register, this could be replaced with a (for now, non-existant) ```merchantId```.|
|» MCC|string|false|MCC: Number and "combined description". ISO 18245: https://www.iso.org/standard/33365.html|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## get__transactions_cards_{cardId}


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//transactions/cards/{cardId} \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//transactions/cards/{cardId} HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//transactions/cards/{cardId}',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//transactions/cards/{cardId}',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//transactions/cards/{cardId}',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//transactions/cards/{cardId}', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//transactions/cards/{cardId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /transactions/cards/{cardId}`


*Get transactions for credit card*


**Note:** Duplicates ```Transactions```endpoint in ```Cards```. For evaluation purposes. 


Optional query parameters below. Note: Sorting and filtering affects backend, and may change.


* SortOrder: "ASC", "DESC"
* DateFrom: "YYYY-MM-DD": ISO 8601: www.iso.org/iso/home/standards/iso8601.htm
* DateTo: "YYYY-MM-DD": ISO 8601: www.iso.org/iso/home/standards/iso8601.htm
* AmountMinimum: Include amount from (and including) this amount.
* AmountMaximum: Include amount from (and including) this amount.
* MCC: Include only this MCC code: ISO 18245: https://www.iso.org/standard/33365.html 
* FreeText: Filter by free text


<h3 id="get__transactions_cards_{cardId}-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|SortOrder|query|string|false|Ascending, descending|
|DateFrom|query|string(date)|false|Filter for start date (included). ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|DateTo|query|string(date)|false|Filter for end date (included). ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|AmountMinimum|query|number|false|Filter for minimum amount (included). No decimals.|
|AmountMaximum|query|string|false|Filter for maximum amount (included). No decimals.|
|MCC|query|string|false|Filter for MCC. Use code only.|
|FreeText|query|string|false|Filter for free text. Case insensitive.|
|IncludePending|query|boolean|false|Should pending transactions be included?|
|cardId|path|string|true|No description|


> Example responses


```json
[
  {
    "transactionId": "12345",
    "amount": "1500.00",
    "currencyValue": "90.00",
    "currency": "NOK",
    "dateBooking": "2018-13-12",
    "dateValue": "2018-12-31",
    "description": "Lunch at The Restaurant at the End of the Universe",
    "status": "BOOKED",
    "merchantName": "Coffee Shop ChainName, shop number 10",
    "MCC": "3514: Hotels/Motels/Inns/Resorts"
  }
]
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__transactions_cards_{cardId}-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<h3 id="get__transactions_cards_{cardId}-responseschema">Response Schema</h3>


Status Code **200**


|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[transaction](#schematransaction)]|false|No description|
|» transactionId|string|true|No description|
|» amount|string|true|No description|
|» currencyValue|string|false|Amount in foreign currency (if relevant)|
|» currency|string|false|If not the currency of the account/card.|
|» dateBooking|string(date)|true|YYYY-MM-DD: Date: ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|» dateValue|string(date)|false|YYYY-MM. ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|» description|string|false|Descriptive text for the transaction.|
|» status|string|false|Booked, reserved, and, if this is to be merged with ```payment```: Completed (or something similar, to indicate that this has, in fact, been processed and finalized)|
|» merchantName|string|false|Name of merchant. With a merhant register, this could be replaced with a (for now, non-existant) ```merchantId```.|
|» MCC|string|false|MCC: Number and "combined description". ISO 18245: https://www.iso.org/standard/33365.html|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


<h1 id="7580-APIs-for-3rd-Parties---Gateway-Layer-Currencies">Currencies</h1>


## get__currencies_convert_{base}_{currency}-{amount}


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//currencies/convert/{base}/{currency}/{amount} \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//currencies/convert/{base}/{currency}/{amount} HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//currencies/convert/{base}/{currency}/{amount}',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//currencies/convert/{base}/{currency}/{amount}',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//currencies/convert/{base}/{currency}/{amount}',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//currencies/convert/{base}/{currency}/{amount}', params={


}, headers = headers)


print r.json()


```



```java
URL obj = new URL("https://1gh7oej.restletmocks.net//currencies/convert/{base}/{currency}/{amount}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /currencies/convert/{base}/{currency}/{amount}`


*Convert amount from CUR1 to CUR2*


Quite basic for now. Input welcome.


<h3 id="get__currencies_convert_{base}_{currency}_{amount}-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|date|query|string(date)|false|End of day. ISO 8601: "YYYY-MM-DD": https://en.wikipedia.org/wiki/ISO_8601|
|base|path|string|true|ISO 4217: alpha 3-letter upcase e.g EUR|
|currency|path|string|true|ISO 4217: alpha 3-letter upcase e.g EUR|
|amount|path|number|true|No description|


> Example responses


```json
{
  "currency": "NOK",
  "currencyRate": "123.45"
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__currencies_convert_{base}_{currency}_{amount}-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|[currencyRate](#schemacurrencyrate)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## get__currencies_list_{base}


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//currencies/list/{base} \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//currencies/list/{base} HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//currencies/list/{base}',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//currencies/list/{base}',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//currencies/list/{base}',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//currencies/list/{base}', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//currencies/list/{base}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /currencies/list/{base}`


*Get a list rates for the most common currencies, with a specified base*


Suitable for making a table or similar.


```
{
    timestamp: 1504548341,
    base: "NOK",
    rates: {
        AED: 3.672538,
        AFN: 66.809999,
        ALL: 125.716501,
        AMD: 484.902502,
        ANG: 1.788575,
        AOA: 135.295998,
        ARS: 9.750101,
        AUD: 1.390866,
        /* ... */
    }
}
```


<h3 id="get__currencies_list_{base}-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|date|query|string|false|End of day. ISO 8601: �YYYY-MM-DD�: https://en.wikipedia.org/wiki/ISO_8601|
|base|path|string|true|"Home" currency. ISO 4217: alpha 3-letter upcase|


> Example responses


```json
[
  {
    "currency": "NOK",
    "currencyRate": "123.45"
  }
]
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__currencies_list_{base}-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<h3 id="get__currencies_list_{base}-responseschema">Response Schema</h3>


Status Code **200**


|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[currencyRate](#schemacurrencyrate)]|false|No description|
|» currency|string|false|ISO 4217: alpha 3-letter upcase: https://www.iso.org/iso-4217-currency-codes.html|
|» currencyRate|string|false|No description|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


<h1 id="7580-APIs-for-3rd-Parties---Gateway-Layer-Location">Location</h1>


## get__locations_branch_findbyaddress


> Code samples



```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//locations/branch/findbyaddress \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//locations/branch/findbyaddress HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//locations/branch/findbyaddress',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//locations/branch/findbyaddress',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//locations/branch/findbyaddress',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//locations/branch/findbyaddress', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//locations/branch/findbyaddress");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /locations/branch/findbyaddress`


*Find nearest branch by address*


Basic geocoding functionality similar to Google Maps: https://developers.google.com/maps/documentation/geocoding/intro


<h3 id="get__locations_branch_findbyaddress-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|address|query|string|false|For now: Assume geocoding functionality similar to Google Maps: https://developers.google.com/maps/documentation/geocoding/intro|


> Example responses


```json
{
  "branchId": "string",
  "name": "DNB headquarters, lobby",
  "phoneNumber": "+4791504800",
  "email": "example@example.com",
  "address": {
    "postalAddressLine1": "Dronning Eufemias gate 30",
    "postalAddressLine2": "c/o CEO office",
    "postalAddressLine3": "string",
    "postCode": "0191",
    "postCity": "Oslo",
    "postCountry": "NO"
  },
  "openingTimes": [
    {
      "day": 0,
      "openingTime": "09:00",
      "closingTime": "16:00"
    }
  ],
  "location": {
    "id": "12345",
    "friendlyName": "DNB headquarters",
    "latitude": "59.9075823",
    "longditude": "10.760133399999972",
    "description": "Lobby"
  }
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__locations_branch_findbyaddress-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|[branch](#schemabranch)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## get__locations_branch_{latitude}-{longditude}_



> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//locations/branch/{latitude}/{longditude}/ \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//locations/branch/{latitude}/{longditude}/ HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//locations/branch/{latitude}/{longditude}/',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//locations/branch/{latitude}/{longditude}/',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//locations/branch/{latitude}/{longditude}/',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//locations/branch/{latitude}/{longditude}/', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//locations/branch/{latitude}/{longditude}/");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /locations/branch/{latitude}/{longditude}/`


*Find nearest branch by coordinates*


<h3 id="get__locations_branch_{latitude}_{longditude}_-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|latitude|path|string|true|No description|
|longditude|path|string|true|No description|


> Example responses


```json
{
  "branchId": "string",
  "name": "DNB headquarters, lobby",
  "phoneNumber": "+4791504800",
  "email": "example@example.com",
  "address": {
    "postalAddressLine1": "Dronning Eufemias gate 30",
    "postalAddressLine2": "c/o CEO office",
    "postalAddressLine3": "string",
    "postCode": "0191",
    "postCity": "Oslo",
    "postCountry": "NO"
  },
  "openingTimes": [
    {
      "day": 0,
      "openingTime": "09:00",
      "closingTime": "16:00"
    }
  ],
  "location": {
    "id": "12345",
    "friendlyName": "DNB headquarters",
    "latitude": "59.9075823",
    "longditude": "10.760133399999972",
    "description": "Lobby"
  }
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__locations_branch_{latitude}_{longditude}_-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|[branch](#schemabranch)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## get__locations_branch_{branchid}_details


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//locations/branch/{branchid}/details \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//locations/branch/{branchid}/details HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//locations/branch/{branchid}/details',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//locations/branch/{branchid}/details',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//locations/branch/{branchid}/details',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//locations/branch/{branchid}/details', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//locations/branch/{branchid}/details");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /locations/branch/{branchid}/details`


*Get branch details*


Contact information, opening hours, etc.


<h3 id="get__locations_branch_{branchid}_details-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|branchid|path|string|true|Id of branch|


> Example responses


```json
{
  "branchId": "string",
  "name": "DNB headquarters, lobby",
  "phoneNumber": "+4791504800",
  "email": "example@example.com",
  "address": {
    "postalAddressLine1": "Dronning Eufemias gate 30",
    "postalAddressLine2": "c/o CEO office",
    "postalAddressLine3": "string",
    "postCode": "0191",
    "postCity": "Oslo",
    "postCountry": "NO"
  },
  "openingTimes": [
    {
      "day": 0,
      "openingTime": "09:00",
      "closingTime": "16:00"
    }
  ],
  "location": {
    "id": "12345",
    "friendlyName": "DNB headquarters",
    "latitude": "59.9075823",
    "longditude": "10.760133399999972",
    "description": "Lobby"
  }
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__locations_branch_{branchid}_details-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|[branch](#schemabranch)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## get__locations_branch_{branchid}_openingtimes


> Code samples



```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//locations/branch/{branchid}/openingtimes \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//locations/branch/{branchid}/openingtimes HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//locations/branch/{branchid}/openingtimes',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//locations/branch/{branchid}/openingtimes',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//locations/branch/{branchid}/openingtimes',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//locations/branch/{branchid}/openingtimes', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//locations/branch/{branchid}/openingtimes");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /locations/branch/{branchid}/openingtimes`


*Get a branch's opening times*


Opening times is also included in Branch.


<h3 id="get__locations_branch_{branchid}_openingtimes-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|branchid|path|string|true|Id of a branch|


> Example responses


```json
[
  {
    "day": 0,
    "openingTime": "09:00",
    "closingTime": "16:00"
  }
]
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__locations_branch_{branchid}_openingtimes-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|[openingTimes](#schemaopeningtimes)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## get__locations_atm_{latitude}-{longditude}_


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//locations/atm/{latitude}/{longditude}/ \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//locations/atm/{latitude}/{longditude}/ HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//locations/atm/{latitude}/{longditude}/',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//locations/atm/{latitude}/{longditude}/',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//locations/atm/{latitude}/{longditude}/',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//locations/atm/{latitude}/{longditude}/', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//locations/atm/{latitude}/{longditude}/");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /locations/atm/{latitude}/{longditude}/`


*Find nearest ATM by coordinates*


If no details (as for now): Assume ATM is open 24h.


<h3 id="get__locations_atm_{latitude}_{longditude}_-parameters">Parameters</h3>


|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|latitude|path|string|true|Current latitude.|
|longditude|path|string|true|Current longditude.|


> Example responses


```json
[
  {
    "id": "12345",
    "name": "DNB headquarters, lobby",
    "address": {
      "postalAddressLine1": "Dronning Eufemias gate 30",
      "postalAddressLine2": "c/o CEO office",
      "postalAddressLine3": "string",
      "postCode": "0191",
      "postCity": "Oslo",
      "postCountry": "NO"
    },
    "location": {
      "id": "12345",
      "friendlyName": "DNB headquarters",
      "latitude": "59.9075823",
      "longditude": "10.760133399999972",
      "description": "Lobby"
    },
    "openingTimes": [
      {
        "day": 0,
        "openingTime": "09:00",
        "closingTime": "16:00"
      }
    ],
    "currencies": [
      "NOK"
    ]
  }
]
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__locations_atm_{latitude}_{longditude}_-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<h3 id="get__locations_atm_{latitude}_{longditude}_-responseschema">Response Schema</h3>


Status Code **200**


|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[ATM](#schemaatm)]|false|No description|
|» id|string|false|No description|
|» name|string|false|No description|
|» address|[address](#schemaaddress)|false|Corresponds with address fields used internally in DNB.|
|»» postalAddressLine1|string|false|Street name and number|
|»» postalAddressLine2|string|false|No description|
|»» postalAddressLine3|string|false|No description|
|»» postCode|string|true|No description|
|»» postCity|string|true|No description|
|»» postCountry|string|true|ISO 3166-1 alpha-2: https://www.iso.org/standard/63546.html|
|» location|[location](#schemalocation)|false|Data object for physical location based on GPS coordinates. May be used for something that does not have a specific address, or somethjing that needs a more specific than an address provides, such as an ```ATM``` at a train station. A ```location``` may be used in addition to an ```address```.|
|»» id|string|false|Internal id|
|»» friendlyName|string|false|Descriptive name|
|»» latitude|string|false|No description|
|»» longditude|string|false|No description|
|»» description|string|false|May be used for large areas like airports, train stations, stadiums, etc.|
|» openingTimes|[object]|false|Opening times for a ```branch```, ```ATM```, or something else.  If open 24 hours, use "00:00" both for ```openingTime``` and ```closingTime```.|
|»» day|integer|false|1: Monday, 2: Tuesday, etc|
|»» openingTime|string|false|HH:MM|
|»» closingTime|string|false|HH:MM|
|» currencies|[string]|false|Array of ISO 4217: alpha 3-letter upcase. https://www.iso.org/iso-4217-currency-codes.html|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


## get__locations_branches


> Code samples


```shell
# You can also use wget
curl -X GET https://1gh7oej.restletmocks.net//locations/branches \
  -H 'Accept: application/json'


```


```http
GET https://1gh7oej.restletmocks.net//locations/branches HTTP/1.1
Host: 1gh7oej.restletmocks.net


Accept: application/json


```


```javascript
var headers = {
  'Accept':'application/json'


};


$.ajax({
  url: 'https://1gh7oej.restletmocks.net//locations/branches',
  method: 'get',


  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})


```


```javascript--nodejs
const request = require('node-fetch');


const headers = {
  'Accept':'application/json'


};


fetch('https://1gh7oej.restletmocks.net//locations/branches',
{
  method: 'GET',


  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});


```


```ruby
require 'rest-client'
require 'json'


headers = {
  'Accept' => 'application/json'
}


result = RestClient.get 'https://1gh7oej.restletmocks.net//locations/branches',
  params: {
  }, headers: headers


p JSON.parse(result)


```


```python
import requests
headers = {
  'Accept': 'application/json'
}


r = requests.get('https://1gh7oej.restletmocks.net//locations/branches', params={


}, headers = headers)


print r.json()


```


```java
URL obj = new URL("https://1gh7oej.restletmocks.net//locations/branches");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());


```


`GET /locations/branches`


*Get list of all DNB branches*


> Example responses


```json
[
  {
    "branchId": "string",
    "name": "DNB headquarters, lobby",
    "phoneNumber": "+4791504800",
    "email": "example@example.com",
    "address": {
      "postalAddressLine1": "Dronning Eufemias gate 30",
      "postalAddressLine2": "c/o CEO office",
      "postalAddressLine3": "string",
      "postCode": "0191",
      "postCity": "Oslo",
      "postCountry": "NO"
    },
    "openingTimes": [
      {
        "day": 0,
        "openingTime": "09:00",
        "closingTime": "16:00"
      }
    ],
    "location": {
      "id": "12345",
      "friendlyName": "DNB headquarters",
      "latitude": "59.9075823",
      "longditude": "10.760133399999972",
      "description": "Lobby"
    }
  }
]
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```
```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


<h3 id="get__locations_branches-responses">Responses</h3>


|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Request succeeded|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[error](#schemaerror)|


<h3 id="get__locations_branches-responseschema">Response Schema</h3>


Status Code **200**


|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[branch](#schemabranch)]|false|No description|
|» branchId|string|false|No description|
|» name|string|false|No description|
|» phoneNumber|string|false|Including "+" and international prefix. Whitespace is stripped.|
|» email|string|false|No description|
|» address|[address](#schemaaddress)|false|Corresponds with address fields used internally in DNB.|
|»» postalAddressLine1|string|false|Street name and number|
|»» postalAddressLine2|string|false|No description|
|»» postalAddressLine3|string|false|No description|
|»» postCode|string|true|No description|
|»» postCity|string|true|No description|
|»» postCountry|string|true|ISO 3166-1 alpha-2: https://www.iso.org/standard/63546.html|
|» openingTimes|[object]|false|Opening times for a ```branch```, ```ATM```, or something else.  If open 24 hours, use "00:00" both for ```openingTime``` and ```closingTime```.|
|»» day|integer|false|1: Monday, 2: Tuesday, etc|
|»» openingTime|string|false|HH:MM|
|»» closingTime|string|false|HH:MM|
|» location|[location](#schemalocation)|false|Data object for physical location based on GPS coordinates. May be used for something that does not have a specific address, or somethjing that needs a more specific than an address provides, such as an ```ATM``` at a train station. A ```location``` may be used in addition to an ```address```.|
|»» id|string|false|Internal id|
|»» friendlyName|string|false|Descriptive name|
|»» latitude|string|false|No description|
|»» longditude|string|false|No description|
|»» description|string|false|May be used for large areas like airports, train stations, stadiums, etc.|


<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read write ), Basic_authentication
</aside>


# Schemas


<h2 id="tocScustomer">customer</h2>


<a id="schemacustomer"></a>


```json
{
  "customerId": "12345678901",
  "customerType": "PERSON",
  "firstName": "Rune",
  "lastName": "Bjerke",
  "companyName": "DNB",
  "address": {
    "postalAddressLine1": "Dronning Eufemias gate 30",
    "postalAddressLine2": "c/o CEO office",
    "postalAddressLine3": "string",
    "postCode": "0191",
    "postCity": "Oslo",
    "postCountry": "NO"
  },
  "email": "example@example.com",
  "phone": "+4791504800",
  "countryOfBirth": "NO",
  "countryCitizenships": [
    "NO"
  ],
  "countryTax": [
    "NO"
  ],
  "customerEngagement": [
    {
      "engagementId": "12345",
      "engagementType": "DEPOSIT",
      "accountNumber": "12345678901",
      "friendlyName": "SAGA MasterCard",
      "corporate": true
    }
  ]
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|customerId|string|true|SSN or organization number|
|customerType|string|true|```PERSON```, ```COMPANY```|
|firstName|string|false|First name. May be used contact person if type is ```COMPANY```.|
|lastName|string|false|Surname. May be used contact person if type is ```COMPANY```.|
|companyName|string|false|Company name, if type is ```COMPANY```.|
|address|[address](#schemaaddress)|true|No description|
|email|string|false|Email address.|
|phone|string|false|Including "+" and international prefix. Whitespace is stripped.|
|countryOfBirth|string|false|ISO 3166-1 alpha-2: https://www.iso.org/standard/63546.html|
|countryCitizenships|[string]|false|ISO 3166-1 alpha-2: https://www.iso.org/standard/63546.html|
|countryTax|[string]|true|ISO 3166-1 alpha-2: https://www.iso.org/standard/63546.html|
|customerEngagement|[[customerEngagement](#schemacustomerengagement)]|false|One or more engagements|


<h2 id="tocScustomerengagement">customerEngagement</h2>


<a id="schemacustomerengagement"></a>


```json
{
  "engagementId": "12345",
  "engagementType": "DEPOSIT",
  "accountNumber": "12345678901",
  "friendlyName": "SAGA MasterCard",
  "corporate": true
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|engagementId|string|true|No description|
|engagementType|string|false|Types of engagements: To be determined. Needs to be aligned with DNB CIM, without exposing internal complexity.|
|accountNumber|string|false|No description|
|friendlyName|string|false|No description|
|corporate|boolean|false|No description|


<h2 id="tocSaccount">account</h2>


<a id="schemaaccount"></a>


```json
{
  "accountNumber": "12345678901",
  "type": "DEPOSIT",
  "accountName": "Standard account",
  "balanceAvailable": 100.01,
  "accountDetails": {
    "IBAN": "NO9386011117947",
    "BIC": "DNBANOKKXXX",
    "currency": "NOK",
    "created": "2018-12-31T23:59:59+01",
    "updated": "2018-12-31T23:59:59+01",
    "accountInterestDetails": {
      "interestRate": 2.01,
      "earnedInterestToDate": 100.01,
      "accruedInterestAndFeesToDate": 1.01,
      "feesToDate": 5.01,
      "accruedInterestFromLastYear": 500.01
    }
  }
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|accountNumber|string|true|11 digits. Bank, etc can be determined from this: https://no.wikipedia.org/wiki/Kontonummer|
|type|string|true|Any type of account.|
|accountName|string|false|Friendly name for the account:|
|balanceAvailable|number|true|No description|
|accountDetails|[accountDetails](#schemaaccountdetails)|false|No description|


<h2 id="tocSaccountbalance">accountBalance</h2>


<a id="schemaaccountbalance"></a>


```json
{
  "accountNumber": "12345678901",
  "amountAvailable": 100.01,
  "amountBooked": 100.01,
  "timestamp": "2018-12-31T23:59:59+01"
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|accountNumber|string|true|11 digits|
|amountAvailable|number|true|Amount available|
|amountBooked|number|true|Booked amount available|
|timestamp|string(date-time)|true|ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|


<h2 id="tocSaccountdetails">accountDetails</h2>


<a id="schemaaccountdetails"></a>


```json
{
  "IBAN": "NO9386011117947",
  "BIC": "DNBANOKKXXX",
  "currency": "NOK",
  "created": "2018-12-31T23:59:59+01",
  "updated": "2018-12-31T23:59:59+01",
  "accountInterestDetails": {
    "interestRate": 2.01,
    "earnedInterestToDate": 100.01,
    "accruedInterestAndFeesToDate": 1.01,
    "feesToDate": 5.01,
    "accruedInterestFromLastYear": 500.01
  }
}
```

### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|IBAN|string|true|ISO 13616:2007: https://www.iso.org/standard/41031.html No whitespace|
|BIC|string|true|ISO 9362: https://en.wikipedia.org/wiki/ISO_9362|
|currency|string|true|Currency: ISO 4217: alpha 3-letter upcase. https://www.iso.org/iso-4217-currency-codes.html|
|created|string(date-time)|true|ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|updated|string(date-time)|true|ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|accountInterestDetails|[accountInterestDetails](#schemaaccountinterestdetails)|false|No description|


<h2 id="tocSaccountinterestdetails">accountInterestDetails</h2>


<a id="schemaaccountinterestdetails"></a>


```json
{
  "interestRate": 2.01,
  "earnedInterestToDate": 100.01,
  "accruedInterestAndFeesToDate": 1.01,
  "feesToDate": 5.01,
  "accruedInterestFromLastYear": 500.01
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|interestRate|number|true|No description|
|earnedInterestToDate|number|true|No description|
|accruedInterestAndFeesToDate|number|true|No description|
|feesToDate|number|true|No description|
|accruedInterestFromLastYear|number|false|No description|


<h2 id="tocSaccountstatement">accountStatement</h2>


<a id="schemaaccountstatement"></a>


```json
{
  "accountNumber": "12345678901",
  "year": "1990",
  "month": "01",
  "transactions": [
    {
      "transactionId": "12345",
      "amount": "1500.00",
      "currencyValue": "90.00",
      "currency": "NOK",
      "dateBooking": "2018-13-12",
      "dateValue": "2018-12-31",
      "description": "Lunch at The Restaurant at the End of the Universe",
      "status": "BOOKED",
      "merchantName": "Coffee Shop ChainName, shop number 10",
      "MCC": "3514: Hotels/Motels/Inns/Resorts"
    }
  ]
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|accountNumber|string|true|No description|
|year|string|true|YYYY: ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|month|string|true|MM: ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|transactions|[[transaction](#schematransaction)]|true|No description|


<h2 id="tocScard">card</h2>


<a id="schemacard"></a>


```json
{
  "cardId": "12345",
  "maskedCardNumber": "XXXX XXXX XXXX 1234",
  "cardType": "VISA",
  "cardGroup": "DEBIT",
  "accountNumber": "012345678901",
  "cardStatus": "NORMAL",
  "blockCode": "12345",
  "expiryDate": "2018-12",
  "debitBalance": {
    "accountNumber": "12345678901",
    "amountAvailable": 100.01,
    "amountBooked": 100.01,
    "timestamp": "2018-12-31T23:59:59+01"
  },
  "creditBalance": {
    "currency": "NOK",
    "creditLimit": "100000.00",
    "amountAvailable": 90000.01,
    "amountBook": 90000.01,
    "timestamp": "2018-12-31T23:59:59+01:00"
  }
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|cardId|string|true|No description|
|maskedCardNumber|string|true|16 characters: Twelve "X", and the last four digits ofr the card number. 4x4 nubers with whitespace.|
|cardType|string|true|Visa, MasterCard, American Express, etc|
|cardGroup|string|true|Debit or credit.|
|accountNumber|string|true|Both for debit and credit cards|
|cardStatus|string|true|Normal, active, blocked|
|blockCode|string|false|If blocked: Code for the blocking reason.|
|expiryDate|string(date)|true|YYYY-MM. ISO 8601: https://www.iso.org/iso-8601-date-and-time-format.html|
|debitBalance|[accountBalance](#schemaaccountbalance)|false|No description|
|creditBalance|[cardBalance](#schemacardbalance)|false|No description|


<h2 id="tocScardbalance">cardBalance</h2>


<a id="schemacardbalance"></a>


```json
{
  "currency": "NOK",
  "creditLimit": "100000.00",
  "amountAvailable": 90000.01,
  "amountBook": 90000.01,
  "timestamp": "2018-12-31T23:59:59+01:00"
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|currency|string|true|ISO 4217: alpha 3-letter upcase: https://www.iso.org/iso-4217-currency-codes.html|
|creditLimit|string|false|No description|
|amountAvailable|number|true|Debit: The amount in the ```account```.Credit: The limit minus the registered payments.|
|amountBook|number|false|No description|
|timestamp|string(date-time)|false|ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|


<h2 id="tocScardinvoice">cardInvoice</h2>


<a id="schemacardinvoice"></a>


```json
{
  "card": {
    "cardId": "12345",
    "maskedCardNumber": "XXXX XXXX XXXX 1234",
    "cardType": "VISA",
    "cardGroup": "DEBIT",
    "accountNumber": "012345678901",
    "cardStatus": "NORMAL",
    "blockCode": "12345",
    "expiryDate": "2018-12",
    "debitBalance": {
      "accountNumber": "12345678901",
      "amountAvailable": 100.01,
      "amountBooked": 100.01,
      "timestamp": "2018-12-31T23:59:59+01"
    },
    "creditBalance": {
      "currency": "NOK",
      "creditLimit": "100000.00",
      "amountAvailable": 90000.01,
      "amountBook": 90000.01,
      "timestamp": "2018-12-31T23:59:59+01:00"
    }
  },
  "year": "2018",
  "month": "01",
  "amount": "100.00",
  "dueDate": "2018-12-31",
  "accountNumber": "012345678901",
  "KID": "42",
  "transactions": [
    {
      "transactionId": "12345",
      "amount": "1500.00",
      "currencyValue": "90.00",
      "currency": "NOK",
      "dateBooking": "2018-13-12",
      "dateValue": "2018-12-31",
      "description": "Lunch at The Restaurant at the End of the Universe",
      "status": "BOOKED",
      "merchantName": "Coffee Shop ChainName, shop number 10",
      "MCC": "3514: Hotels/Motels/Inns/Resorts"
    }
  ]
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|card|[card](#schemacard)|true|No description|
|year|string|true|YYYY|
|month|string|true|MM, where January is 01|
|amount|string|true|No description|
|dueDate|string(date)|true|YYYY-MM-DD. ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|accountNumber|string|true|Account to pay to. 11 digits.|
|KID|string|false|2-25 digits|
|transactions|[[transaction](#schematransaction)]|true|No description|


<h2 id="tocSpayment">payment</h2>


<a id="schemapayment"></a>


```json
{
  "paymentId": "123456789",
  "debitAccount": "12345678901",
  "creditAccount": "12345678901",
  "amount": 1500.01,
  "type": "TBD1",
  "date": "2018-31-12",
  "status": "PAID",
  "paymentDetails": {
    "invoiceReference": "12345678901"
  }
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|paymentId|string|true|No description|
|debitAccount|string|true|No description|
|creditAccount|string|true|No description|
|amount|number|true|No description|
|type|string|true|TBD|
|date|string(date)|false|YYYY-MM-DD: Date: ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|status|string|true|Statuses TBD|
|paymentDetails|[paymentDetails](#schemapaymentdetails)|false|No description|


<h2 id="tocSpaymentdetails">paymentDetails</h2>


<a id="schemapaymentdetails"></a>


```json
{
  "invoiceReference": "12345678901"
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|invoiceReference|string|false|Used for eFaktura|


<h2 id="tocSpaymentinitiation">paymentInitiation</h2>


<a id="schemapaymentinitiation"></a>


```json
{
  "type": "KID",
  "debitAccountNumber": "12345678901",
  "creditAccountNumber": "12345678901",
  "amount": "1500.00",
  "paymentDate": "2018-12-31",
  "message": "35298562958265982749",
  "initiator": "DNB"
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|type|string|true|KID, message (and transfer?)|
|debitAccountNumber|string|true|No description|
|creditAccountNumber|string|true|No description|
|amount|string|true|No description|
|paymentDate|string(date-time)|true|YYYY-MM-DD: Date: ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|message|string|false|Used for both KID and Message, based on Type.|
|initiator|string|true|Nu phone who dis?|


<h2 id="tocStransaction">transaction</h2>


<a id="schematransaction"></a>


```json
{
  "transactionId": "12345",
  "amount": "1500.00",
  "currencyValue": "90.00",
  "currency": "NOK",
  "dateBooking": "2018-13-12",
  "dateValue": "2018-12-31",
  "description": "Lunch at The Restaurant at the End of the Universe",
  "status": "BOOKED",
  "merchantName": "Coffee Shop ChainName, shop number 10",
  "MCC": "3514: Hotels/Motels/Inns/Resorts"
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|transactionId|string|true|No description|
|amount|string|true|No description|
|currencyValue|string|false|Amount in foreign currency (if relevant)|
|currency|string|false|If not the currency of the account/card.|
|dateBooking|string(date)|true|YYYY-MM-DD: Date: ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|dateValue|string(date)|false|YYYY-MM. ISO 8601: www.iso.org/iso/home/standards/iso8601.htm|
|description|string|false|Descriptive text for the transaction.|
|status|string|false|Booked, reserved, and, if this is to be merged with ```payment```: Completed (or something similar, to indicate that this has, in fact, been processed and finalized)|
|merchantName|string|false|Name of merchant. With a merhant register, this could be replaced with a (for now, non-existant) ```merchantId```.|
|MCC|string|false|MCC: Number and "combined description". ISO 18245: https://www.iso.org/standard/33365.html|


<h2 id="tocSaddress">address</h2>


<a id="schemaaddress"></a>


```json
{
  "postalAddressLine1": "Dronning Eufemias gate 30",
  "postalAddressLine2": "c/o CEO office",
  "postalAddressLine3": "string",
  "postCode": "0191",
  "postCity": "Oslo",
  "postCountry": "NO"
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|postalAddressLine1|string|false|Street name and number|
|postalAddressLine2|string|false|No description|
|postalAddressLine3|string|false|No description|
|postCode|string|true|No description|
|postCity|string|true|No description|
|postCountry|string|true|ISO 3166-1 alpha-2: https://www.iso.org/standard/63546.html|


<h2 id="tocSlocation">location</h2>


<a id="schemalocation"></a>


```json
{
  "id": "12345",
  "friendlyName": "DNB headquarters",
  "latitude": "59.9075823",
  "longditude": "10.760133399999972",
  "description": "Lobby"
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|id|string|false|Internal id|
|friendlyName|string|false|Descriptive name|
|latitude|string|false|No description|
|longditude|string|false|No description|
|description|string|false|May be used for large areas like airports, train stations, stadiums, etc.|


<h2 id="tocSbranch">branch</h2>


<a id="schemabranch"></a>


```json
{
  "branchId": "string",
  "name": "DNB headquarters, lobby",
  "phoneNumber": "+4791504800",
  "email": "example@example.com",
  "address": {
    "postalAddressLine1": "Dronning Eufemias gate 30",
    "postalAddressLine2": "c/o CEO office",
    "postalAddressLine3": "string",
    "postCode": "0191",
    "postCity": "Oslo",
    "postCountry": "NO"
  },
  "openingTimes": [
    {
      "day": 0,
      "openingTime": "09:00",
      "closingTime": "16:00"
    }
  ],
  "location": {
    "id": "12345",
    "friendlyName": "DNB headquarters",
    "latitude": "59.9075823",
    "longditude": "10.760133399999972",
    "description": "Lobby"
  }
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|branchId|string|false|No description|
|name|string|false|No description|
|phoneNumber|string|false|Including "+" and international prefix. Whitespace is stripped.|
|email|string|false|No description|
|address|[address](#schemaaddress)|false|No description|
|openingTimes|[openingTimes](#schemaopeningtimes)|false|No description|
|location|[location](#schemalocation)|false|No description|


<h2 id="tocSatm">ATM</h2>


<a id="schemaatm"></a>


```json
{
  "id": "12345",
  "name": "DNB headquarters, lobby",
  "address": {
    "postalAddressLine1": "Dronning Eufemias gate 30",
    "postalAddressLine2": "c/o CEO office",
    "postalAddressLine3": "string",
    "postCode": "0191",
    "postCity": "Oslo",
    "postCountry": "NO"
  },
  "location": {
    "id": "12345",
    "friendlyName": "DNB headquarters",
    "latitude": "59.9075823",
    "longditude": "10.760133399999972",
    "description": "Lobby"
  },
  "openingTimes": [
    {
      "day": 0,
      "openingTime": "09:00",
      "closingTime": "16:00"
    }
  ],
  "currencies": [
    "NOK"
  ]
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|id|string|false|No description|
|name|string|false|No description|
|address|[address](#schemaaddress)|false|No description|
|location|[location](#schemalocation)|false|No description|
|openingTimes|[openingTimes](#schemaopeningtimes)|false|No description|
|currencies|[string]|false|Array of ISO 4217: alpha 3-letter upcase. https://www.iso.org/iso-4217-currency-codes.html|


<h2 id="tocSopeningtimes">openingTimes</h2>


<a id="schemaopeningtimes"></a>


```json
[
  {
    "day": 0,
    "openingTime": "09:00",
    "closingTime": "16:00"
  }
]
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|day|integer|false|1: Monday, 2: Tuesday, etc|
|openingTime|string|false|HH:MM|
|closingTime|string|false|HH:MM|


<h2 id="tocSerror">error</h2>


<a id="schemaerror"></a>


```json
{
  "httpStatus": "400",
  "errorNumber": 1234,
  "errorMessage": "Computer says no",
  "errorDocumentation": "https://docs.example.com/help-for-this-endpoint/",
  "errorDetails": [
    {
      "errorNumber": "5432",
      "errorField": "firstName",
      "errorDescription": "First name cannot have non-Latin characters."
    }
  ]
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|httpStatus|string|false|Implicit, but still included.|
|errorNumber|number|false|DNB's error number|
|errorMessage|string|false|Explanation|
|errorDocumentation|string|false|URI to developer documentation for this error|
|errorDetails|[[errorDetails](#schemaerrordetails)]|false|Details about the cause of this error. Zero or more.|


<h2 id="tocSerrordetails">errorDetails</h2>


<a id="schemaerrordetails"></a>


```json
{
  "errorNumber": "5432",
  "errorField": "firstName",
  "errorDescription": "First name cannot have non-Latin characters."
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|errorNumber|string|true|DNB's internal error number.|
|errorField|string|false|Name of field that caused the error.|
|errorDescription|string|false|No description|


<h2 id="tocSheaderlinks">headerLinks</h2>


<a id="schemaheaderlinks"></a>


```json
{
  "first": "string",
  "self": "https://api.example.com/something",
  "previous": "https://api.example.com/something-previous",
  "next": "https://api.example.com/something-next"
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|first|string|true|https://api.example.com/something-first|
|self|string|true|No description|
|previous|string|false|No description|
|next|string|false|No description|


<h2 id="tocScurrencyrate">currencyRate</h2>


<a id="schemacurrencyrate"></a>


```json
{
  "currency": "NOK",
  "currencyRate": "123.45"
}
```


### Properties


|Name|Type|Required|Description|
|---|---|---|---|
|currency|string|false|ISO 4217: alpha 3-letter upcase: https://www.iso.org/iso-4217-currency-codes.html|
|currencyRate|string|false|No description|


