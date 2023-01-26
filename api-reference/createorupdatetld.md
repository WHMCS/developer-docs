+++
title = "CreateOrUpdateTLD"
toc = true
+++

Create or Update a TLD Extension. If a TLD exists, the existing record will be updated. If it does not, a new TLD will be created. Allows for configuration of TLD related selling parameters, pricing, grace periods and display order. Pricing can be supplied in any active currency and will be automatically converted into all active currencies within the WHMCS installation.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "CreateOrUpdateTLD" | Required |
| extension | string | The extension to add or update eg: .com, .net, etc... | Required |
| id_protection | bool | Offer ID Protection for the extension | Optional |
| dns_management | bool | Offer DNS Management for the extension | Optional |
| email_forwarding | bool | Offer Email Forwarding for the extension | Optional |
| epp_required | bool | Is an EPP required for domain transfers | Optional |
| auto_registrar | string | The active registrar the extension should automatically register with on payment | Optional |
| group | string | Specify a group label. One of 'HOT', 'NEW' or 'SALE'. Leave blank for none. | Optional |
| currency_code | string | The currency code the pricing is in. Required when defining pricing, grace fee, or redemption fee. Price will be converted for all active currencies. The currency must exist in the target WHMCS install and be configured with an exchange rate. | Optional |
| grace_period_days | int | The number of days for the grace period | Optional |
| grace_period_fee | float | The grace period fee for the extension. -1 will disable the grace period | Optional |
| redemption_period_days | int | The number of days for the redemption period | Optional |
| redemption_period_fee | float | The redemption period fee for the extension. -1 will disable the redemption period | Optional |
| register | array | An array of registration pricing. See example below for format. | Optional |
| renew | array | An array of renewal pricing. See example below for format. The maximum renewal period for any extension is 9 years. | Optional |
| transfer | array | An array of transfer pricing. See example below for format. Only transfers for the minimum register period can be defined. | Optional |
| display_after | string | Can be used to modify TLD display order. Specify the existing TLD that this TLD should follow. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| extension | string | The extension that has been created or updated |
| id | int | The unique id of the extension in the database. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'CreateOrUpdateTLD',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'extension' => '.com',
            'id_protection' => true,
            'dns_management' => true,
            'email_forwarding' => true,
            'epp_required' => true,
            'auto_registrar' => 'enom',
            'currency_code' => 'USD',
            'grace_period_days' => '0',
            'grace_period_fee' => '-1',
            'redemption_period_fee' => '75.00',
            'register' => array(1 => '10.00', 2 => '20.00', 3 => '30.00', 4 => '40.00', 5 => '50.00', 6 => '60.00', 7 => '70.00', 8 => '80.00', 9 => '90.00', 10 => '100.00'),
            'renew' => array(1 => '10.00', 2 => '20.00', 3 => '30.00', 4 => '40.00', 5 => '50.00', 6 => '60.00', 7 => '70.00', 8 => '80.00', 9 => '90.00'),
            'transfer' => array(1 => '10.00'),
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
$command = 'CreateOrUpdateTLD';
$postData = array(
    'extension' => '.com',
    'id_protection' => true,
    'dns_management' => true,
    'email_forwarding' => true,
    'epp_required' => true,
    'auto_registrar' => 'enom',
    'currency_code' => 'USD',
    'grace_period_days' => '0',
    'grace_period_fee' => '-1',
    'redemption_period_fee' => '75.00',
    'register' => array(1 => '10.00', 2 => '20.00', 3 => '30.00', 4 => '40.00', 5 => '50.00', 6 => '60.00', 7 => '70.00', 8 => '80.00', 9 => '90.00', 10 => '100.00'),
    'renew' => array(1 => '10.00', 2 => '20.00', 3 => '30.00', 4 => '40.00', 5 => '50.00', 6 => '60.00', 7 => '70.00', 8 => '80.00', 9 => '90.00'),
    'transfer' => array(1 => '10.00'),
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "extension": ".com",
    "id": "1"
}
```


### Error Responses

Possible error condition responses include:

* Extension is required
* No Active Registrars - auto_registrar value cannot be defined
* Invalid auto_registrar value. Must be empty or one of: enom, resellerclub...
* Variable currency_code is required when defining pricing
* Provided currency_code value does not exist. Must be one of: USD, GBP...
* Parameters register, renew and transfer must be arrays
* The maximum register period is 10 years
* The maximum renew period is 9 years
* Only one transfer period can be defined
* The maximum transfer period is 10 years
* Invalid group parameter: GROUP. Should be one of HOT, NEW, SALE


### Version History

| Version | Changelog |
| ------- | --------- |
| 7.10.0 | Initial Version |
