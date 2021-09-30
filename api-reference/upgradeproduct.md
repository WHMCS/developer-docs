+++
title = "UpgradeProduct"
toc = true
+++

Upgrade, or calculate an upgrade on, a product

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpgradeProduct" | Required |
| serviceid | int | The ID of the service to update | Required |
| calconly | bool | Only calculate the upgrade amount | Optional |
| paymentmethod | string | The upgrade payment method in system format (e.g. paypal) | Required |
| type | string | The type of upgrade ('product', 'configoptions') | Required |
| newproductid | int | The ID of the new product | Optional |
| newproductbillingcycle | string | The new products billing cycle | Optional |
| promocode | string | The promotion code to apply to the upgrade | Optional |
| configoptions | array | If type=configoptions - Config options to include in the upgrade. Keys represent config option IDs while their values represent the config option choice ID or value (depending on type). In the example provided, config option ID=1 is a dropdown specifying option ID 4, and config option ID=2 is a quantity specifying a desire for 5 units. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| upgradeinprogress | bool | Is an upgrade in progress (for calconly) |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'UpgradeProduct',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'serviceid' => '1',
            'paymentmethod' => 'paypal',
            'newproductbillingcycle' => 'monthly',
            'type' => 'product',
            'newproductid' => '11',
            'configoptions' => [1 => 4, 2 => 5],
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
$command = 'UpgradeProduct';
$postData = array(
    'serviceid' => '1',
    'paymentmethod' => 'paypal',
    'newproductbillingcycle' => 'monthly',
    'type' => 'product',
    'newproductid' => '11',
    'configoptions' => [1 => 4, 2 => 5],
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "oldproductid": "12",
    "oldproductname": "5 Years",
    "newproductid": 11,
    "newproductname": "4 Years",
    "daysuntilrenewal": 13,
    "totaldays": 30,
    "newproductbillingcycle": "monthly",
    "price": "$-8.67 USD",
    "id": "44",
    "orderid": 73,
    "order_number": "9093331404",
    "invoiceid": null
}
```


### Error Responses

Possible error condition responses include:

* Service ID Not Found
* Unable to accept upgrade order. Previous upgrade invoice for service is still unpaid.
* Invalid Payment Method. Valid options include xxx
* Invalid Upgrade Type


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
