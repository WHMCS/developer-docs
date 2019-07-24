+++
title = "AddCredit"
toc = true
+++

Adds credit to a given client.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AddCredit" | Required |
| clientid | int |  | Required |
| description | string | Admin only notes for credit justification | Required |
| amount | float | The amount of credit to add or remove. Must be a positive value. | Required |
| date | string | The date the credit was added. YYYY-mm-dd format. | Optional |
| adminid | int | The active admin id to be associated with the credit record. Defaults to current admin. | Optional |
| type | string | Whether to add or remove credit. One of 'add' or 'remove' | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| newbalance | float | The new total credit balance |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'AddCredit',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'clientid' => '1',
            'description' => 'Adding funds via api',
            'amount' => '12.34',
            'adminid' => '1',
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
$command = 'AddCredit';
$postData = array(
    'clientid' => '1',
    'description' => 'Adding funds via api',
    'amount' => '12.34',
    'adminid' => '1',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "newbalance": "123.45"
}
```


### Error Responses

Possible error condition responses include:

* Type can only be add or remove
* Client ID Not Found
* Admin ID Not Found
* No Amount Provided
* Amount must be in decimal format: ### or ###.##
* Date Format is not Valid


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
