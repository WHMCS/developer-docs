+++
title = "AddProduct"
toc = true
+++

Adds a product to the system to be available for purchase

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AddProduct" | Required |
| name | string | The name of the product to be added | Required |
| gid | int | The id of the product group to add the product | Required |
| type | string | One of 'hostingaccount', 'reselleraccount', 'server' or 'other' | Optional |
| stockcontrol | bool | Set to true to enable stock control on the product | Optional |
| qty | int | How much of this product is in stock | Optional |
| paytype | string | The payment type of the product. One of 'free', 'onetime', 'recurring' | Optional |
| hidden | bool | Should the product be hidden from the client order form | Optional |
| showdomainoptions | bool | Should the product show the domain registration options. | Optional |
| tax | bool | Does tax apply to the product. | Optional |
| isFeatured | bool | Should the product be featured in the Product Group. | Optional |
| proratabilling | bool | Is pro-rata billing enabled for this product. | Optional |
| description | string | The description of the product to show on the product listing in the cart | Optional |
| welcomeemail | int | The id of the Email Template to use as the welcome email. Product/Service Messages only | Optional |
| proratadate | int | See https://docs.whmcs.com/Products_and_Services#Pricing_Tab | Optional |
| proratachargenextmonth | int | See https://docs.whmcs.com/Products_and_Services#Pricing_Tab | Optional |
| subdomain | string | A comma separated list of subdomains to offer on the domain register page. eg: .domain1.com,.domain2.com | Optional |
| autosetup | string | When should the product be automatically setup. One of '' (never), 'on' (pending order), 'payment' (on payment), 'order' (on order) | Optional |
| module | string | The server module system name to associate with the product. eg: cpanel, autorelease, plesk | Optional |
| servergroupid | int | The server group id used on product creation to associate an appropriate server | Optional |
| configoption1 | mixed | The first module configuration value | Optional |
| configoption2 | mixed | The second module configuration value | Optional |
| configoption3 | mixed | The third module configuration value | Optional |
| configoption4 | mixed | The fourth module configuration value | Optional |
| configoption5 | mixed | The fifth module configuration value | Optional |
| configoption6 | mixed | The sixth module configuration value | Optional |
| order | int | The order to in which to display on the order form | Optional |
| pricing | array | The pricing array to associate with the product. Format: $pricing[currencyid][cycle]. See Example. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| pid | int | The id of the newly created product |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'AddProduct',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'type' => 'other',
            'gid' => '1',
            'name' => 'Sample Product',
            'welcomeemail' => '5',
            'paytype' => 'recurring',
            'pricing' => array(2 => array('monthly' => 8.00, 'annually' => 80.00)),
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
$command = 'AddProduct';
$postData = array(
    'type' => 'other',
    'gid' => '1',
    'name' => 'Sample Product',
    'welcomeemail' => '5',
    'paytype' => 'recurring',
    'pricing' => array(2 => array('monthly' => 8.00, 'annually' => 80.00)),
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

* You must supply a name for the product


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
