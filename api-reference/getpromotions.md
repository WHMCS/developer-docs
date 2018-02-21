+++
title = "GetPromotions"
toc = true
+++

Obtain promotions matching the passed criteria

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetPromotions" | Required |
| code | string | Retrieve a specific promotion code. Do not pass to retrieve all | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| promotions | array | An array of promotional codes matching the criteria passed |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetPromotions',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
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
$command = 'GetPromotions';
$postData = array(
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
    "promotions": {
        "promotion": [
            {
                "id": 1,
                "code": "sample",
                "type": "Percentage",
                "recurring": 1,
                "value": 10,
                "cycles": "",
                "appliesto": "1,2",
                "requires": "1,2",
                "requiresexisting": 0,
                "startdate": "0000-00-00",
                "expirationdate": "0000-00-00",
                "maxuses": 0,
                "uses": 1,
                "lifetimepromo": 0,
                "applyonce": 0,
                "newsignups": 0,
                "existingclient": 0,
                "onceperclient": 0,
                "recurfor": 0,
                "upgrades": 0,
                "upgradeconfig": "a:4:{s:5:\"value\";s:4:\"0.00\";s:4:\"type\";s:0:\"\";s:12:\"discounttype\";s:10:\"Percentage\";s:13:\"configoptions\";s:0:\"\";}",
                "notes": ""
            }
        ]
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
