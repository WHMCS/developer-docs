+++
title = "GetQuotes"
toc = true
+++

Obtain quotes matching the passed criteria

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetQuotes" | Required |
| limitstart | int | The offset for the returned quote data (default: 0). | Optional |
| limitnum | int | The number of records to return (default: 25). | Optional |
| quoteid | int | A specific quote ID to find quotes for. | Optional |
| userid | int | A specific client to find quotes for. | Optional |
| subject | string | A specific subject to find quotes for. | Optional |
| stage | string | A specific stage ('Draft','Delivered','On Hold','Accepted','Lost', or 'Dead') to find quotes for. | Optional |
| datecreated | string | A specific created date to find quotes for. Format: Y-m-d | Optional |
| lastmodified | string | A specific last modified date to find quotes for. Format: Y-m-d | Optional |
| validuntil | string | A specific valid until date to find quotes for. Format: Y-m-d | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available. |
| startnumber | int | The starting number for the returned results. |
| numreturned | int | The number of results returned. |
| quotes | array | An array of quotes matching the criteria passed. |


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
$command = 'GetQuotes';
$postData = array(
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "totalresults": 2,
    "startnumber": 0,
    "numreturned": 2,
    "quotes": {
        "quote": [
            {
                "id": 2,
                "subject": "",
                "stage": "Draft",
                "validuntil": "2023-01-30",
                "userid": 1,
                "client": {
                    "id": 1,
                    "firstname": "Richard",
                    "lastname": "Example",
                    "companyname": "Example Inc.",
                    "email": "amalia@example.com",
                    "datecreated": "2022-12-30",
                    "groupid": 0,
                    "status": "Active"
                },
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
                "tax_id": "",
                "currency": 1,
                "subtotal": "15.86",
                "tax1": "0.00",
                "tax2": "0.00",
                "total": "15.86",
                "proposal": "",
                "customernotes": "",
                "adminnotes": "",
                "datecreated": "2022-12-30",
                "lastmodified": "2022-12-30",
                "datesent": "0000-00-00",
                "dateaccepted": "0000-00-00",
                "items": {
                    "item": [
                        {
                            "id": 1,
                            "description": "Apple",
                            "quantity": "1",
                            "unitprice": "1.23",
                            "discount": "0.00",
                            "taxable": 1
                        },
                        {
                            "id": 2,
                            "description": "Pear",
                            "quantity": "3",
                            "unitprice": "5.00",
                            "discount": "2.50",
                            "taxable": 0
                        }
                    ]
                }
            },
            {
                "id": 1,
                "subject": "",
                "stage": "Draft",
                "validuntil": "2023-01-29",
                "userid": 0,
                "client": null,
                "firstname": "William",
                "lastname": "Smith",
                "companyname": "",
                "email": "",
                "address1": "",
                "address2": "",
                "city": "",
                "state": "",
                "postcode": "",
                "country": "US",
                "phonenumber": "",
                "tax_id": "",
                "currency": 1,
                "subtotal": "0.00",
                "tax1": "0.00",
                "tax2": "0.00",
                "total": "0.00",
                "proposal": "",
                "customernotes": "",
                "adminnotes": "",
                "datecreated": "2022-12-29",
                "lastmodified": "2022-12-30",
                "datesent": "0000-00-00",
                "dateaccepted": "0000-00-00",
                "items": {
                    "item": []
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
| 8.7 | Add the 'client' key to the quote response. If an existing client has been associated to the quote, select client information is returned. |
