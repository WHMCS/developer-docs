+++
title = "GetTLDPricing"
toc = true
+++

Retrieve TLD pricing

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetTLDPricing" | Required |
| currencyid | int | The currency ID to fetch pricing for. Pass this or clientid, but not both. clientid overrides currencyid. | Optional |
| clientid | int | The client ID to fetch pricing for. Pass this or clientid, but not both. clientid overrides currencyid. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| currency | array | An array of information about the associated currency. |
| pricing | array | An array of pricing and other information for configured TLDs. The items in this array are conditional and only appear when a user has already configured pricing (including a price of 0). |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetTLDPricing',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'currencyid' => '1',
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
$command = 'GetTLDPricing';
$postData = array(
    'currencyid' => '1',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "currency": {
        "id": 1,
        "code": "USD",
        "prefix": "$",
        "suffix": " USD",
        "format": 1,
        "rate": "1.00000"
    },
    "pricing": {
        "com": {
            "tld": "com",
            "categories": [
                "Popular"
            ],
            "addons": {
                "dns": false,
                "email": false,
                "idprotect": false
            },
            "group": "",
            "register": {
                "1": "14.95"
            },
            "transfer": {
                "1": "14.95"
            },
            "renew": {
                "1": "14.95"
            },
            "grace_period": null,
            "redemption_period": null
        },
        "net": {
            "tld": "net",
            "categories": [
                "Popular"
            ],
            "addons": {
                "dns": false,
                "email": false,
                "idprotect": false
            },
            "group": "",
            "register": {
                "1": "14.95"
            },
            "transfer": {
                "1": "14.95"
            },
            "renew": {
                "1": "14.95"
            },
            "grace_period": null,
            "redemption_period": null
        },
        "org": {
            "tld": "org",
            "categories": [
                "Popular"
            ],
            "addons": {
                "dns": false,
                "email": false,
                "idprotect": false
            },
            "group": "",
            "register": {
                "1": "14.95"
            },
            "transfer": {
                "1": "14.95"
            },
            "renew": {
                "1": "14.95"
            },
            "grace_period": null,
            "redemption_period": null
        },
        "biz": {
            "tld": "biz",
            "categories": [
                "Popular"
            ],
            "addons": {
                "dns": false,
                "email": false,
                "idprotect": false
            },
            "group": "",
            "register": {
                "1": "14.95"
            },
            "transfer": {
                "1": "14.95"
            },
            "renew": {
                "1": "14.95"
            },
            "grace_period": null,
            "redemption_period": null
        },
        "info": {
            "tld": "info",
            "categories": [
                "Popular"
            ],
            "addons": {
                "dns": false,
                "email": false,
                "idprotect": false
            },
            "group": "",
            "register": {
                "1": "14.95"
            },
            "transfer": {
                "1": "14.95"
            },
            "renew": {
                "1": "14.95"
            },
            "grace_period": null,
            "redemption_period": null
        }
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
