+++
title = "UpdateClientDomain"
toc = true
+++

Updates a Client Domain

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateClientDomain" | Required |
| domainid | int | The id of the client domain to update | Required |
| dnsmanagement | bool | Enable/Disable DNS Management | Optional |
| emailforwarding | bool | Enable/Disable Email Forwarding | Optional |
| idprotection | bool | Enable/Disable ID Protection | Optional |
| donotrenew | bool | Enable/Disable Do Not Renew | Optional |
| type | string | The type of domain order. ('Register', 'Transfer') | Optional |
| regdate | \Carbon\Carbon | The registration date of the domain (Y-m-d) | Optional |
| nextduedate | \Carbon\Carbon | The next due date of the domain (Y-m-d) | Optional |
| expirydate | \Carbon\Carbon | The expiry date of the domain (Y-m-d) | Optional |
| domain | string | The domain name to be changed to | Optional |
| firstpaymentamount | float | The first payment amount on the domain | Optional |
| recurringamount | float | The recurring amount for automatic renewal invoices | Optional |
| registrar | string | The registrar to associate with the domain | Optional |
| regperiod | int | The registration period of the domain | Optional |
| paymentmethod | string | The payment method to associate in system format (eg paypal) | Optional |
| subscriptionid | string | The subscription ID to associate with the domain | Optional |
| status | string | The status to change the domain to | Optional |
| notes | string | The admin notes for the domain | Optional |
| promoid | int | The promotion Id to associate | Optional |
| autorecalc | bool | Should the recurring amount of the domain be automatically recalculated (this will ignore any passed $recurringamount) | Optional |
| updatens | bool | Should the nameservers be updated at the registrar | Optional |
| ns1 | string | The first nameserver to save | Optional |
| ns2 | string | The second nameserver to save | Optional |
| ns3 | string | The third nameserver to save | Optional |
| ns4 | string | The fourth nameserver to save | Optional |
| ns5 | string | The fifth nameserver to save | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| domainid | int | The Id of the updated domain |


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
* ns1 and ns2 required
* Registrar Error Message


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
