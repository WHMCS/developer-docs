+++
title = "AddPayMethod"
toc = true
+++

Add a Pay Method to a given client. Supports the creation of credit card and bank account pay methods. Note that some tokenised payment gateways cannot be utilised via the API. Please refer to individual payment gateway documentation for specifics about supported functionality.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AddPayMethod" | Required |
| clientid | int | The id of the client to add the Pay Method | Required |
| type | string | The type of Pay Method to add. One of 'BankAccount', 'CreditCard', or 'RemoteCreditCard'. Defaults to 'CreditCard' | Optional |
| description | string | The description for the new Pay Method | Optional |
| gateway_module_name | string | Required for use with tokenised payment gateways eg. authorizecim, sagepaytokens, etc... | Optional |
| card_number | string | Credit Card Number. Required for CreditCard and RemoteCreditCard types | Optional |
| card_expiry | string | The expiry date for the card. Required for cc type. Format 'MMYY' eg 0122 | Optional |
| card_start | string | The start date for the card. Not required. Format 'MMYY' eg 0122 | Optional |
| card_issue_number | int | The issue_number for the card. Not required | Optional |
| bank_name | string | The name of the bank. Not required | Optional |
| bank_account_type | string | The type of bank account (checking, credit etc). Not required | Optional |
| bank_code | string | The bank code. Also called sort code or routing number. Required for BankAccount type | Optional |
| bank_account | string | The account number. Required for BankAccount type | Optional |
| set_as_default | bool | Should the new Pay Method be the client default | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| clientid | int | The id of the client the Pay Method has been added to |
| paymethodid | int | The id of the newly created Pay Method |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'AddPayMethod',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'clientid' => '1',
            'type' => 'CreditCard',
            'description' => 'New Card',
            'card_number' => '4242424242424242',
            'card_expiry' => '0423',
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
$command = 'AddPayMethod';
$postData = array(
    'clientid' => '1',
    'type' => 'CreditCard',
    'description' => 'New Card',
    'card_number' => '4242424242424242',
    'card_expiry' => '0423',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "clientid": "1",
    "paymethodid": "1"
}
```


### Error Responses

Possible error condition responses include:

* Client ID Is Required
* Invalid Client ID
* Invalid Pay Method Type. Type should be one of 'BankAccount', 'CreditCard', or 'RemoteCreditCard'
* Gateway is Required for RemoteCreditCard type
* No Local Credit Card Payment Gateways Enabled
* Card Number is required for 'CreditCard' or 'RemoteCreditCard' type
* Expiry Date is required for 'CreditCard' or 'RemoteCreditCard' type
* Expiry Date is invalid
* Start Date is invalid
* Issue Number is invalid
* Invalid Gateway Module Name. Must be one of: xxx (list of active gateways)
* Unsupported Gateway Type for Storage
* Error Creating Remote Token: xxx (error from module)
* Routing number is required
* Account number is required
* Gateway is Required for Bank Account Storage


### Version History

| Version | Changelog |
| ------- | --------- |
| 7.8.0 | Initial Version |
