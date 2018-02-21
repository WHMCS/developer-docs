+++
title = "GetTransactions"
toc = true
+++

Obtain transactions matching the passed criteria

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetTransactions" | Required |
| invoiceid | int | Obtain transactions for a specific invoice id | Optional |
| clientid | int | Find transactions for a specific client id | Optional |
| transid | string | Find transactions for a specific transaction id | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| startnumber | int | The starting number for the returned results |
| numreturned | int | The number of results returned |
| transactions | array | An array of transactions matching the criteria passed |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetTransactions',
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
$command = 'GetTransactions';
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
    "totalresults": 1,
    "startnumber": 0,
    "numreturned": 1,
    "transactions": {
        "transaction": [
            {
                "id": "10",
                "userid": "1",
                "currency": "0",
                "gateway": "paypal",
                "date": "2016-01-01 06:41:11",
                "description": "Invoice Payment",
                "amountin": "45.90",
                "fees": "0.00",
                "amountout": "0.00",
                "rate": "1.00000",
                "transid": "1479732071aad259f3513ec",
                "invoiceid": "59",
                "refundid": "0"
            }
        ]
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
