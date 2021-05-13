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
| status | string | Optional desired Client Status. 'Active', 'Inactive', or 'Closed'. | Optional |
| search | string | The search term to look for at the start of email, firstname, lastname, fullname or companyname | Optional |
| orderby | string | The column to order by. id, firstname, lastname, companyname, email, groupid, datecreated, status | Optional |

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
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
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
    "totalresults": 2,
    "startnumber": 0,
    "numreturned": 2,
    "clients": {
        "client": [
            {
                "id": 2,
                "firstname": "Angelica",
                "lastname": "Mohr",
                "companyname": "",
                "email": "price.ima@example.com",
                "datecreated": "2016-01-15",
                "groupid": 0,
                "status": "Active"
            },
            {
                "id": 1,
                "firstname": "Price",
                "lastname": "Beier",
                "companyname": "",
                "email": "cecelia99@example.com",
                "datecreated": "2016-01-01",
                "groupid": 0,
                "status": "Active"
            }
        ]
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 8.2 | Implement new parameter: "orderby". |
