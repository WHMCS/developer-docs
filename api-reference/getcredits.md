+++
title = "GetCredits"
toc = true
+++

Obtain the Credit Log for a Client Account

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetCredits" | Required |
| clientid | int | The Client to obtain the log for | Required |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| clientid | int | The client the log is for |
| credits | array | The credit log entries returned |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetCredits',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'clientid' => '1',
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
$command = 'GetCredits';
$postData = array(
    'clientid' => '1',
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
    "clientid": "1",
    "credits[credit][0][id]": "1",
    "credits[credit][0][date]": "2016-01-01",
    "credits[credit][0][description]": "This is a sample credit record",
    "credits[credit][0][amount]": "10.00",
    "credits[credit][0][relid]": "0",
    "credits[credit][1][id]": "2",
    "credits[credit][1][date]": "2016-01-01",
    "credits[credit][1][description]": "Credit Applied to Invoice #1",
    "credits[credit][1][amount]": "-10.00",
    "credits[credit][1][relid]": "0"
}
```


### Error Responses

Possible error condition responses include:

* Client ID Not Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
