+++
title = "UpdateClientProduct"
toc = true
+++

Updates a Client Service

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateClientProduct" | Required |
| serviceid | int | The id of the client service to update | Required |
| pid | int | The package id to associate with the service | Optional |
| serverid | int | The server id to associate with the service | Optional |
| nextduedate | \Carbon\Carbon | The next due date of the service (Y-m-d) | Optional |
| terminationDate | \Carbon\Carbon | Update the termination date of the service (Y-m-d) | Optional |
| completedDate | \Carbon\Carbon | Update the completed date of the service (Y-m-d) | Optional |
| domain | string | The domain name to be changed to | Optional |
| firstpaymentamount | float | The first payment amount on the service | Optional |
| recurringamount | float | The recurring amount for automatic renewal invoices | Optional |
| paymentmethod | string | The payment method to associate in system format (eg paypal) | Optional |
| subscriptionid | string | The subscription ID to associate with the service | Optional |
| status | string | The status to change the service to | Optional |
| notes | string | The admin notes for the service | Optional |
| serviceusername | string | The service username | Optional |
| servicepassword | string | The service password | Optional |
| overideautosuspend | string | Should override auto suspend be provided ('on' or 'off') | Optional |
| overidesuspenduntil | \Carbon\Carbon | Update the Override Suspend date of the service (Y-m-d) | Optional |
| ns1 | string | (VPS/Dedicated servers only) | Optional |
| ns2 | string | (VPS/Dedicated servers only) | Optional |
| dedicatedip | string |  | Optional |
| assignedips | string | (VPS/Dedicated servers only) | Optional |
| diskusage | int | The disk usage in bytes | Optional |
| disklimit | int | The disk limit in bytes | Optional |
| bwusage | int | The bandwidth usage in bytes | Optional |
| bwlimit | int | The bandwidth limit in bytes | Optional |
| overidesuspenduntil | \Carbon\Carbon |  | Optional |
| suspendreason | string |  | Optional |
| promoid | int | The promotion Id to associate | Optional |
| unset | array | An array of items to unset. Can be one of: 'domain', 'serviceusername', 'servicepassword', 'subscriptionid', 'ns1', 'ns2', 'dedicatedip', 'assignedips', 'notes', 'suspendreason' | Optional |
| autorecalc | bool | Should the recurring amount of the service be automatically recalculated (this will ignore any passed $recurringamount) | Optional |
| customfields | string | Base64 encoded serialized array of custom field values | Optional |
| configoptions | string | Base64 encoded serialized array of configurable option field values | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| serviceid | int | The Id of the updated service |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'UpdateClientProduct',
            'username' => 'ADMIN_USERNAME',
            'password' => 'ADMIN_PASSWORD',
            'serviceid' => '1',
            'status' => 'Terminated',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'UpdateClientProduct';
$postData = array(
    'serviceid' => '1',
    'status' => 'Terminated',
);
$adminUsername = 'ADMIN_USERNAME';

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "serviceid": "1"
}
```


### Error Responses

Possible error condition responses include:

* Service ID Not Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
