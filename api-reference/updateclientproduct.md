+++
title = "UpdateClientProduct"
toc = true
+++

Updates a Client Service

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateClientProduct" | Required |
| serviceid | int | The ID of the client service to update. | Required |
| pid | int | The package ID to associate with the service. | Optional |
| serverid | int | The server ID to associate with the service. | Optional |
| regdate | string | The registration date of the service. Format: Y-m-d | Optional |
| nextduedate | string | The next due date of the service. Format: Y-m-d | Optional |
| terminationdate | string | Update the termination date of the service. Format: Y-m-d | Optional |
| domain | string | The domain name to be changed to. | Optional |
| firstpaymentamount | float | The first payment amount on the service. | Optional |
| recurringamount | float | The recurring amount for automatic renewal invoices. | Optional |
| paymentmethod | string | The payment method to associate, in system format (for example, paypal). | Optional |
| billingcycle | string | The term in which the product is billed on (for example, One-Time, Monthly, or Quarterly). | Optional |
| subscriptionid | string | The subscription ID to associate with the service. | Optional |
| status | string | The status to change the service to. | Optional |
| notes | string | The admin notes for the service. | Optional |
| serviceusername | string | The service username. | Optional |
| servicepassword | string | The service password. | Optional |
| overideautosuspend | string | Whether to provide override auto suspend ('on' or 'off'). | Optional |
| overidesuspenduntil | string | Update the Override Suspend date of the service. Format: Y-m-d | Optional |
| ns1 | string | (VPS/Dedicated servers only) | Optional |
| ns2 | string | (VPS/Dedicated servers only) | Optional |
| dedicatedip | string |  | Optional |
| assignedips | string | (VPS/Dedicated servers only) | Optional |
| diskusage | int | The disk usage in megabytes. | Optional |
| disklimit | int | The disk limit in megabytes. | Optional |
| bwusage | int | The bandwidth usage in megabytes. | Optional |
| bwlimit | int | The bandwidth limit in megabytes. | Optional |
| suspendreason | string |  | Optional |
| promoid | int | The promotion ID to associate. | Optional |
| unset | array | An array of items to unset. Can be one of: 'domain', 'serviceusername', 'servicepassword', 'subscriptionid', 'ns1', 'ns2', 'dedicatedip', 'assignedips', 'notes', or 'suspendreason' | Optional |
| autorecalc | bool | Whether to automatically recalculate the recurring amount of the service (this will ignore any passed $recurringamount). | Optional |
| customfields | string | Base64 encoded serialized array of custom field values - base64_encode(serialize(array("1"=>"Yahoo"))); | Optional |
| configoptions | string | Base64 encoded serialized array of configurable option field values - base64_encode(serialize(array(configoptionid => dropdownoptionid, XXX => array('optionid' => YYY, 'qty' => ZZZ)))) - XXX is the ID of the configurable option - YYY is the optionid found in tblhostingconfigoption.optionid - ZZZ is the quantity you want to use for that option | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| serviceid | int | The ID of the updated service. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'UpdateClientProduct',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'serviceid' => '1',
            'status' => 'Terminated',
            'customfields' => base64_encode(serialize(array("1"=>"Yahoo"))),
            'configoptions' => base64_encode(serialize(array(configoptionid => dropdownoptionid, XXX => array('optionid' => YYY, 'qty' => ZZZ)))),
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
$command = 'UpdateClientProduct';
$postData = array(
    'serviceid' => '1',
    'status' => 'Terminated',
    'customfields' => base64_encode(serialize(array("1"=>"Yahoo"))),
    'configoptions' => base64_encode(serialize(array(configoptionid => dropdownoptionid, XXX => array('optionid' => YYY, 'qty' => ZZZ)))),
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

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
