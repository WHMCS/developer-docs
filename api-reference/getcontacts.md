+++
title = "GetContacts"
toc = true
+++

Obtain the Client Contacts that match passed criteria

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetContacts" | Required |
| limitstart | int | The offset for the returned log data (default: 0) | Optional |
| limitnum | int | The number of records to return (default: 25) | Optional |
| userid | int | Find contacts for a specific client id | Optional |
| firstname | string | Find contacts with a specific first name | Optional |
| lastname | string | Find contacts with a specific last name | Optional |
| companyname | string | Find contacts with a specific company name | Optional |
| email | string | Find contacts with a specific email address | Optional |
| address1 | string | Find contacts with a specific address line 1 | Optional |
| address2 | string | Find contacts with a specific address line 2 | Optional |
| city | string | Find contacts with a specific city | Optional |
| state | string | Find contacts with a specific state | Optional |
| postcode | string | Find contacts with a specific post/zip code | Optional |
| country | string | Find contacts with a specific country | Optional |
| phonenumber | string | Find contacts with a specific phone number | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| startnumber | int | The starting number for the returned results |
| numreturned | int | The number of results returned |
| contacts | array | The contact entries returned |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetContacts',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'userid' => '1',
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
$command = 'GetContacts';
$postData = array(
    'userid' => '1',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "totalresults": 1,
    "startnumber": 0,
    "numreturned": 1,
    "contacts": {
        "contact": [
            {
                "id": 1,
                "userid": 1,
                "firstname": "Test",
                "lastname": "Contact",
                "email": "contact@example.com",
                "address1": "404 Street Not Found",
                "address2": "",
                "city": "Test",
                "state": "Test",
                "postcode": "TE5 5ST",
                "country": "GB",
                "phonenumber": "",
                "domainemails": true,
                "generalemails": true,
                "invoiceemails": true,
                "productemails": true,
                "supportemails": true,
                "affiliateemails": true,
                "created_at": "0000-00-00 00:00:00",
                "updated_at": "0000-00-00 00:00:00"
            }
        ]
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 8.0 | Removed sub-account functionality |
