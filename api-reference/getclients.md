+++
title = "GetClients"
toc = true
+++

Obtain the Clients that match passed criteria

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetClients" | Required |
| limitstart | int | The offset for the returned log data (default: 0) | Optional |
| limitnum | int | The number of records to return (default: 25) | Optional |
| sorting | string | The direction to sort the results. ASC or DESC. Default: ASC | Optional |
| search | string | The search term to look for at the start of email, firstname, lastname, fullname or companyname | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| startnumber | int | The starting number for the returned results |
| numreturned | int | The number of results returned |
| clients | array | The client entries returned |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetClients',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'search' => 'example.com',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'GetClients';
$postData = array(
    'search' => 'example.com',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "totalresults": "2",
    "startnumber": "0",
    "numreturned": "2",
    "clients[client][0][id]": "1",
    "clients[client][0][firstname]": "Price",
    "clients[client][0][lastname]": "Beier",
    "clients[client][0][companyname]": "",
    "clients[client][0][email]": "cecelia99@example.com",
    "clients[client][0][datecreated]": "2016-01-01",
    "clients[client][0][groupid]": "0",
    "clients[client][0][status]": "Active",
    "clients[client][1][id]": "1",
    "clients[client][1][firstname]": "Angelica",
    "clients[client][1][lastname]": "Mohr",
    "clients[client][1][companyname]": "",
    "clients[client][1][email]": "price.ima@example.com",
    "clients[client][1][datecreated]": "2016-01-15",
    "clients[client][1][groupid]": "0",
    "clients[client][1][status]": "Active"
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
