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
| subaccount | bool | Search for sub-accounts | Optional |

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
    "totalresults": "1",
    "startnumber": "0",
    "numreturned": "1",
    "contacts[contact][0][id]": "1",
    "contacts[contact][0][userid]": "1",
    "contacts[contact][0][firstname]": "Test",
    "contacts[contact][0][lastname]": "Contact",
    "contacts[contact][0][companyname]": "",
    "contacts[contact][0][email]": "contact@example.com",
    "contacts[contact][0][address1]": "404 Street Not Found",
    "contacts[contact][0][address2]": "",
    "contacts[contact][0][city]": "Test",
    "contacts[contact][0][state]": "Tester",
    "contacts[contact][0][postcode]": "TE5 5ST",
    "contacts[contact][0][country]": "GB",
    "contacts[contact][0][phonenumber]": "",
    "contacts[contact][0][subaccount]": "0",
    "contacts[contact][0][password]": "$2y$10$WuJGdclhF0cocxoKCzNpF.4OfAQNOmbXpg9z0Mt1d977oAPYPoZhq",
    "contacts[contact][0][permissions]": "",
    "contacts[contact][0][domainemails]": "1",
    "contacts[contact][0][generalemails]": "1",
    "contacts[contact][0][invoiceemails]": "1",
    "contacts[contact][0][productemails]": "1",
    "contacts[contact][0][supportemails]": "1",
    "contacts[contact][0][affiliateemails]": "1",
    "contacts[contact][0][pwresetkey]": "",
    "contacts[contact][0][created_at]": "0000-00-00 00:00:00",
    "contacts[contact][0][updated_at]": "0000-00-00 00:00:00",
    "contacts[contact][0][pwresetexpiry]": "0000-00-00 00:00:00"
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
