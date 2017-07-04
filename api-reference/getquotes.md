+++
title = "GetQuotes"
toc = true
+++

Obtain quotes matching the passed criteria

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetQuotes" | Required |
| limitstart | int | The offset for the returned quote data (default: 0) | Optional |
| limitnum | int | The number of records to return (default: 25) | Optional |
| quoteid | int | Obtain a specific quote id | Optional |
| userid | int | Find quotes for a specific client id | Optional |
| subject | string | Find quotes for a specific subject | Optional |
| stage | string | Find quotes for a specific stage ('Draft','Delivered','On Hold','Accepted','Lost','Dead') | Optional |
| datecreated | \Carbon\Carbon | Find quotes for a specific created date. Format: Y-m-d | Optional |
| lastmodified | \Carbon\Carbon | Find quotes for a specific last modified date. Format: Y-m-d | Optional |
| validuntil | \Carbon\Carbon | Find quotes for a specific valid until date. Format: Y-m-d | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| startnumber | int | The starting number for the returned results |
| numreturned | int | The number of results returned |
| quotes | array | An array of quotes matching the criteria passed |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetQuotes',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'id' => '1',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'GetQuotes';
$postData = array(
    'id' => '1',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "totalresults": "1",
    "startnumber": 0,
    "numreturned": 1,
    "quotes": {
        "quote": [
            {
                "id": "1",
                "subject": "Sample Quote",
                "stage": "Draft",
                "validuntil": "2016-02-01",
                "userid": "1",
                "firstname": "",
                "lastname": "",
                "companyname": "",
                "email": "",
                "address1": "",
                "address2": "",
                "city": "",
                "state": "",
                "postcode": "",
                "country": "US",
                "phonenumber": "",
                "currency": "1",
                "subtotal": "9.90",
                "tax1": "0.00",
                "tax2": "0.00",
                "total": "9.90",
                "proposal": "This is Proposal Test",
                "customernotes": "These are customer notes",
                "adminnotes": "These are Admin Only notes",
                "datecreated": "2016-01-01",
                "lastmodified": "2016-01-01",
                "datesent": "0000-00-00",
                "dateaccepted": "0000-00-00",
                "items": {
                    "item": [
                        {
                            "id": "1",
                            "description": "This is a line item on a quote",
                            "quantity": "1",
                            "unitprice": "10.00",
                            "discount": "1.00",
                            "taxable": "0"
                        }
                    ]
                }
            }
        ]
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
