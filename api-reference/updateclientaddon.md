+++
title = "UpdateClientAddon"
toc = true
+++

Updates a Client Addon

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateClientAddon" | Required |
| id | int | The ID of the client addon to update. | Required |
| status | string | The status to change the addon to. | Optional |
| addonid | int | The configured addon ID to update the client addon to. | Optional |
| name | string | The custom name to apply to the addon. | Optional |
| setupfee | float | The setup fee for the client addon. | Optional |
| recurring | float | The recurring amount for the client addon. | Optional |
| billingcycle | string | The billing cycle for the addon. | Optional |
| nextduedate | string | The next due date for the addon. Format: Y-m-d | Optional |
| terminationdate | string | The termination date of the addon. Format: Y-m-d | Optional |
| notes | string | The admin notes to associate with the addon. | Optional |
| autorecalc | bool | Whether to automatically recalculate the recurring amount of the addon (this will ignore any passed $recurring). | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| id | int | The ID of the updated addon. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'UpdateClientAddon',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'id' => '1',
            'status' => 'Terminated',
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
$command = 'UpdateClientAddon';
$postData = array(
    'id' => '1',
    'status' => 'Terminated',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "id": "1"
}
```


### Error Responses

Possible error condition responses include:

* Addon ID Not Found
* Nothing to Update


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
