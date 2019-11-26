+++
title = "AcceptOrder"
toc = true
+++

Accepts a pending order

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AcceptOrder" | Required |
| orderid | int | The order id to be accepted | Required |
| serverid | int | The specific server to assign to products within the order | Optional |
| serviceusername | string | The specific username to assign to products within the order | Optional |
| servicepassword | string | The specific password to assign to products within the order | Optional |
| registrar | string | The specific registrar to assign to domains within the order | Optional |
| sendregistrar | bool | Send the request to the registrar to register the domain. | Optional |
| autosetup | bool | Send the request to the product module to activate the service. This can override the product configuration. | Optional |
| sendemail | bool | Send any automatic emails. This can be Product Welcome, Domain Renewal, Domain Transfer etc. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'AcceptOrder',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'orderid' => '1',
            'registrar' => 'enom',
            'autosetup' => true,
            'sendemail' => true,
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
$command = 'AcceptOrder';
$postData = array(
    'orderid' => '1',
    'registrar' => 'enom',
    'autosetup' => true,
    'sendemail' => true,
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success"
}
```


### Error Responses

Possible error condition responses include:

* Order ID not found or Status not Pending
* Server and/or registrar response message


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
