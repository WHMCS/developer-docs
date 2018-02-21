+++
title = "GetTLDPricing"
toc = true
+++

Retrieve TLD pricing

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetTLDPricing" | Required |
| currencyid | int | The currency ID to fetch pricing for | Optional |
| clientid | int | The id of the client to fetch pricing for. Pass one or the other. clientid being passed will override currencyid | Optional |

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
    "currency": {
        "id": "1",
        "code": "USD",
        "prefix": "$",
        "suffix": " USD",
        "format": "2",
        "rate": "1.00000"
    },
    "pricing": {
        "com": {
            "categories": [
                "Popular",
                "gTLD"
            ],
            "addons": {
                "dns": true,
                "email": true,
                "idprotect": true
            },
            "group": "new",
            "register": {
                "1": "9.95",
                "2": "19.90",
                "3": "29.85"
            },
            "transfer": {
                "1": "9.95",
                "2": "15.00",
                "3": "25.00"
            },
            "renew": {
                "1": "9.95",
                "2": "15.00",
                "3": "25.00"
            }
        },
        "net": {
            "categories": [
                "Popular",
                "gTLD"
            ],
            "addons": {
                "dns": false,
                "email": false,
                "idprotect": false
            },
            "group": "sale",
            "register": {
                "1": "9.00"
            },
            "transfer": {
                "1": "11.95"
            },
            "renew": {
                "1": "11.95"
            }
        },
        "org": {
            "categories": [
                "Popular",
                "gTLD"
            ],
            "addons": {
                "dns": false,
                "email": false,
                "idprotect": false
            },
            "group": "hot",
            "register": {
                "1": "11.95"
            },
            "transfer": {
                "1": "11.95"
            },
            "renew": {
                "1": "11.95"
            }
        }
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
