+++
title = "GetClientsDetails"
toc = true
+++

Obtain the Clients Details for a specific client

Note this function returns the client information in the top level array. This information
is deprecated and may be removed in a future version of WHMCS.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetClientsDetails" | Required |
| clientid | int | The client id to obtain the details for. $clientid or $email is required | Optional |
| email | string | The email address of the client to search for | Optional |
| stats | bool | Also return additional client statistics. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| client | array | The information on the client. |
| stats | array | Additional statistics for the client returned. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetClientsDetails',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'clientid' => '1',
            'stats' => true,
            'responsetype' => 'json',
        )
    )
);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'GetClientsDetails';
$postData = array(
    'clientid' => '1',
    'stats' => true,
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "client": {
        "client_id": 1,
        "owner_user_id": 1,
        "userid": 1,
        "id": 1,
        "uuid": "f08ea4d1-c578-441a-9b0a-aa3aff8b1acf",
        "firstname": "Test",
        "lastname": "Client",
        "fullname": "Test Client",
        "companyname": "",
        "email": "test-client@example.com",
        "address1": "123 Test Street",
        "address2": "",
        "city": "Test",
        "fullstate": "Tester",
        "state": "Tester",
        "postcode": "TE5 5ST",
        "countrycode": "GB",
        "country": "GB",
        "phonenumber": "01234567890",
        "tax_id": "",
        "email_preferences": {
            "general": "1",
            "invoice": "1",
            "support": "1",
            "product": "1",
            "domain": "1",
            "affiliate": "1"
        },
        "statecode": "Tester",
        "countryname": "United Kingdom",
        "phonecc": "44",
        "phonenumberformatted": "+44.1234567890",
        "telephoneNumber": "+44.1234567890",
        "billingcid": 0,
        "notes": "",
        "currency": 1,
        "defaultgateway": "",
        "groupid": 0,
        "status": "Active",
        "credit": "0.00",
        "taxexempt": false,
        "latefeeoveride": false,
        "overideduenotices": false,
        "separateinvoices": false,
        "disableautocc": false,
        "emailoptout": false,
        "marketing_emails_opt_in": true,
        "overrideautoclose": false,
        "allowSingleSignOn": 1,
        "email_verified": true,
        "language": "",
        "isOptedInToMarketingEmails": true,
        "lastlogin": "Date: 03\/10\/2016 10:26<br>IP Address:<br>Host:",
        "currency_code": "USD",
        "customfields": [
            {
                "id": 1,
                "value": "Custom Field Value"
            }
        ],
        "customfields1": "Custom Field Value",
        "users": {
            "user": [
                {
                    "id": 1,
                    "name": "Testing User",
                    "email": "testuser@whmcs.com",
                    "is_owner": true
                }
            ]
        }
    },
    "stats": {
        "numdueinvoices": 19,
        "dueinvoicesbalance": "$2645.80 USD",
        "incredit": false,
        "creditbalance": "$0.00 USD",
        "grossRevenue": "$0.00 USD",
        "expenses": "$0.00 USD",
        "income": "$0.00 USD",
        "numoverdueinvoices": 19,
        "overdueinvoicesbalance": "$2645.80 USD",
        "numDraftInvoices": 0,
        "draftInvoicesBalance": "$0.00 USD",
        "numunpaidinvoices": 19,
        "unpaidinvoicesamount": "$2645.80 USD",
        "numpaidinvoices": 0,
        "paidinvoicesamount": "$0.00 USD",
        "numcancelledinvoices": 0,
        "cancelledinvoicesamount": "$0.00 USD",
        "numrefundedinvoices": 0,
        "refundedinvoicesamount": "$0.00 USD",
        "numcollectionsinvoices": 0,
        "collectionsinvoicesamount": "$0.00 USD",
        "numpaymentpendinginvoices": 0,
        "paymentpendinginvoicesamount": "$0.00 USD",
        "productsnumactivehosting": 0,
        "productsnumhosting": 0,
        "productsnumactivereseller": 0,
        "productsnumreseller": 0,
        "productsnumactiveservers": 0,
        "productsnumservers": 0,
        "productsnumactiveother": 2,
        "productsnumother": 2,
        "productsnumactive": 2,
        "productsnumtotal": 2,
        "numactivedomains": 2,
        "numdomains": 2,
        "numacceptedquotes": 0,
        "numquotes": 0,
        "numtickets": 0,
        "numactivetickets": 0,
        "numaffiliatesignups": 0,
        "isAffiliate": false
    }
}
```


### Warning Responses

Warning responses are returned when using API functionality that has been removed or marked as deprecated.
We suggest following any recommended actions in the warning to ensure future compatibility.

Possible warning messages include:

* Credit Card related parameters are now deprecated and have been removed. Use GetPayMethods instead.


### Error Responses

Possible error condition responses include:

* Either clientid Or email Is Required
* Client Not Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 7.8 | Credit Card related parameters have been removed due to the introduction of support for multiple credit cards per client. Use GetPayMethods instead. |
| 7.10 | Added email preferences parameters |
| 8.0 | Added users parameter |
