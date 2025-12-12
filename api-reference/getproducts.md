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
| pid | int\|string | Obtain a specific product id configuration. Can be a list of ids comma separated | Optional |
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
    "totalresults": 1,
    "products": {
        "product": [
            {
                "pid": 1,
                "gid": 1,
                "type": "hostingaccount",
                "name": "Best Hosting Plan",
                "slug": "best-hosting-plan",
                "product-url": "https:\/\/www.example.com\/whmcs\/product-group\/best-hosting-plan",
                "description": "This is our best hosting plan, with all the bells and whistles.",
                "module": "cpanel",
                "paytype": "recurring",
                "allowqty": 2,
                "quantity_available": 0,
                "pricing": {
                    "USD": {
                        "prefix": "$",
                        "suffix": " USD",
                        "msetupfee": "0.00",
                        "qsetupfee": "0.00",
                        "ssetupfee": "0.00",
                        "asetupfee": "0.00",
                        "bsetupfee": "0.00",
                        "tsetupfee": "0.00",
                        "monthly": "25.99",
                        "quarterly": "-1.00",
                        "semiannually": "-1.00",
                        "annually": "-1.00",
                        "biennially": "-1.00",
                        "triennially": "-1.00"
                    }
                },
                "customfields": {
                    "customfield": [
                        {
                            "id": 2,
                            "name": "Secondary Contact",
                            "description": "Would you like to provide a secondary point of contact?",
                            "required": ""
                        }
                    ]
                },
                "configoptions": {
                    "configoption": [
                        {
                            "id": 4,
                            "name": "MultiPHP Services",
                            "type": "3",
                            "minqty": 1,
                            "maxqty": 10,
                            "options": {
                                "option": [
                                    {
                                        "id": 4,
                                        "name": "Include MultiPHP Options",
                                        "rawName": null,
                                        "recurring": 0,
                                        "required": null,
                                        "pricing": {
                                            "USD": {
                                                "msetupfee": "0.00",
                                                "qsetupfee": "0.00",
                                                "ssetupfee": "0.00",
                                                "asetupfee": "0.00",
                                                "bsetupfee": "0.00",
                                                "tsetupfee": "0.00",
                                                "monthly": "2.99",
                                                "quarterly": "0.00",
                                                "semiannually": "0.00",
                                                "annually": "0.00",
                                                "biennially": "0.00",
                                                "triennially": "0.00"
                                            }
                                        }
                                    }
                                ]
                            }
                        }
                    ]
                }
            }
        ]
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 8.3 | Added `slug` and `product_url` in response |
| 8.12 | Added `allowqty` and `quantity_available` in response |
| 8.12 | Added `minqty` and `maxqty` to configurable options |
