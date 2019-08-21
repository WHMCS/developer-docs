+++
title = "GetProducts"
toc = true
+++

Retrieve configured products matching provided criteria

NOTE: This API method is designed to be used in the building of custom order
forms. As a result, only custom fields that have the 'Show on Order Form'
setting enabled will be returned for a given product.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetProducts" | Required |
| pid | int|string | Obtain a specific product id configuration. Can be a list of ids comma separated | Optional |
| gid | int | Retrieve products in a specific group id | Optional |
| module | string | Retrieve products utilising a specific module | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| startnumber | int | The starting number for the returned results |
| numreturned | int | The number of results returned |
| products | array | An array of products matching the criteria passed |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetProducts',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'pid' => '1',
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
$command = 'GetProducts';
$postData = array(
    'pid' => '1',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "totalresults": "1",
    "startnumber": "0",
    "numreturned": "1",
    "products[product][0][pid] ": "> 1",
    "products[product][0][gid] ": "> 1",
    "products[product][0][type] ": "> hostingaccount",
    "products[product][0][name] ": "> Starter Package",
    "products[product][0][description] ": "> Disk Space:1GB\\r\\nBandwidth: 3GB\\r\\nEmail Accounts:5\\r\\nSubdomains:0\\r\\nDatabases:0\\r\\nAddon Domains:0",
    "products[product][0][module] ": ">",
    "products[product][0][paytype] ": "> recurring",
    "products[product][0][pricing][USD][prefix] ": "> $",
    "products[product][0][pricing][USD][suffix] ": ">  USD",
    "products[product][0][pricing][USD][msetupfee] ": "> 0.00",
    "products[product][0][pricing][USD][qsetupfee] ": "> 0.00",
    "products[product][0][pricing][USD][ssetupfee] ": "> 0.00",
    "products[product][0][pricing][USD][asetupfee] ": "> 0.00",
    "products[product][0][pricing][USD][bsetupfee] ": "> 0.00",
    "products[product][0][pricing][USD][tsetupfee] ": "> 0.00",
    "products[product][0][pricing][USD][monthly] ": "> -1.00",
    "products[product][0][pricing][USD][quarterly] ": "> -1.00",
    "products[product][0][pricing][USD][semiannually] ": "> 28.95",
    "products[product][0][pricing][USD][annually] ": "> 49.95",
    "products[product][0][pricing][USD][biennially] ": "> -1.00",
    "products[product][0][pricing][USD][triennially] ": "> -1.00",
    "products[product][0][customfields][customfield]": "",
    "products[product][0][configoptions][configoption]": ""
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
