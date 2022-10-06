+++
title = "GetUsers"
toc = true
+++

Obtain the Users that match passed criteria

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetUsers" | Required |
| limitstart | int | The offset for the returned log data (default: 0) | Optional |
| limitnum | int | The number of records to return (default: 25) | Optional |
| sorting | string | The direction to sort the results. ASC or DESC. Default: ASC | Optional |
| search | string | The search term to look for at the start of email, firstname, lastname, or fullname | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| startnumber | int | The starting number for the returned results |
| numreturned | int | The number of results returned |
| users | array | The user entries returned |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetUsers',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'search' => 'john.smith@example.net',
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
$command = 'GetUsers';
$postData = array(
    'search' => 'john.smith@example.net',
    'responsetype' => 'json',
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
    "users": [
        {
            "id": 1,
            "firstname": "John",
            "lastname": "Smith",
            "email": "john.smith@example.net",
            "datecreated": "2020-12-15 15:29:49",
            "validationdata": "",
            "clients": [
                {
                    "id": 1,
                    "isOwner": true
                }
            ]
        }
    ]
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 8.1.0 | Initial Version |
