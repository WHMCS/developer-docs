+++
title = "UpdateClientDomain"
toc = true
+++

Updates a Client Domain

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateClientDomain" | Required |
| domainid | int | The ID of the client domain to update. | Required |
| dnsmanagement | bool | Whether to enable or disable DNS management. | Optional |
| emailforwarding | bool | Whether to enable or disable Email forwarding. | Optional |
| idprotection | bool | Whether to enable or disable ID protection. | Optional |
| donotrenew | bool | Whether to prevent renewal. | Optional |
| type | string | The type of domain order ('Register' or 'Transfer'). | Optional |
| regdate | string | The registration date of the domain. Format: Y-m-d | Optional |
| nextduedate | string | The next due date of the domain. Format: Y-m-d | Optional |
| expirydate | string | The expiration date of the domain. Format: Y-m-d | Optional |
| domain | string | The domain name to be changed to. | Optional |
| firstpaymentamount | float | The first payment amount on the domain. | Optional |
| recurringamount | float | The recurring amount for automatic renewal invoices. | Optional |
| registrar | string | The registrar to associate with the domain. Example: enom, resellerclub, customregistrarname | Optional |
| regperiod | int | The registration period of the domain. | Optional |
| paymentmethod | string | The payment method to associate in system format (for example, paypal). | Optional |
| subscriptionid | string | The subscription ID to associate with the domain. | Optional |
| status | string | The status to change the domain to. | Optional |
| notes | string | The admin notes for the domain. | Optional |
| promoid | int | The promotion ID to associate. | Optional |
| autorecalc | bool | Whether to recalculate the recurring amount of the domain (this will ignore any passed $recurringamount). | Optional |
| updatens | bool | Whether to update the nameservers at the registrar. | Optional |
| ns1 | string | The first nameserver to save. | Optional |
| ns2 | string | The second nameserver to save. | Optional |
| ns3 | string | The third nameserver to save. | Optional |
| ns4 | string | The fourth nameserver to save. | Optional |
| ns5 | string | The fifth nameserver to save. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| domainid | int | The ID of the updated domain. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'UpdateClientDomain',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'domainid' => '1',
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
$command = 'UpdateClientDomain';
$postData = array(
    'domainid' => '1',
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
    "domainid": "1"
}
```


### Error Responses

Possible error condition responses include:

* Domain ID Not Found
* The Registrar is not active
* ns1 and ns2 required
* Registrar Error Message


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
