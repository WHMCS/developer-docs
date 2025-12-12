+++
title = "GetClientsAddons"
toc = true
+++

Obtain the Clients Product Addons that match passed criteria

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetClientsAddons" | Required |
| serviceid | int\|string | The service id(s) to obtain the client product addons for. Single number or comma separated list | Optional |
| clientid | int | The client to obtain the client product addons for | Optional |
| addonid | int | The predefined product addon id from tbladdons (tbladdons.id) to obtain client addons for. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| serviceid | int | The specific service id searched for |
| clientid | int | The specific client id searched for |
| addons | array | The client product addons list |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetClientsAddons',
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
$command = 'GetClientsAddons';
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
    "serviceid": "",
    "clientid": "1",
    "totalresults": "1",
    "addons[addon][0][id]": "1",
    "addons[addon][0][qty]": "1",
    "addons[addon][0][userid]": "1",
    "addons[addon][0][orderid]": "0",
    "addons[addon][0][serviceid]": "1",
    "addons[addon][0][addonid]": "0",
    "addons[addon][0][name]": "Addon 1",
    "addons[addon][0][setupfee]": "0.00",
    "addons[addon][0][recurring]": "15.00",
    "addons[addon][0][billingcycle]": "Monthly",
    "addons[addon][0][tax]": "",
    "addons[addon][0][status]": "Active",
    "addons[addon][0][regdate]": "2015-12-03",
    "addons[addon][0][nextduedate]": "2016-10-03",
    "addons[addon][0][nextinvoicedate]": "2016-10-03",
    "addons[addon][0][paymentmethod]": "paypal",
    "addons[addon][0][paymentmethodname]": "PayPal",
    "addons[addon][0][notes]": ""
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 8.12 | Added `qty` parameter |
