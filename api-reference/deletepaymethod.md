+++
title = "DeletePayMethod"
toc = true
+++

Delete a Pay Method.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "DeletePayMethod" | Required |
| clientid | int | The id of the client matching the Pay Method | Required |
| paymethodid | int | The id of the Pay Method to delete | Required |
| failonremotefailure | bool | Pass as true to return an error if a remote token deletion fails | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| paymethodid | int | The id of the Pay Method deleted |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'DeletePayMethod',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'paymethodid' => '1',
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
$command = 'DeletePayMethod';
$postData = array(
    'paymethodid' => '1',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "paymethodid": "1"
}
```


### Error Responses

Possible error condition responses include:

* Client ID is Required
* Pay Method ID is Required
* Invalid Pay Method ID
* Pay Method does not belong to passed Client ID
* Error Deleting Remote Pay Method: xxx (response from module)


### Version History

| Version | Changelog |
| ------- | --------- |
| 7.8.0 | Initial Version |
