+++
title = "UpdatePayMethod"
toc = true
+++

Update a Credit Card Pay Method.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdatePayMethod" | Required |
| clientid | int | The id of the client matching the Pay Method | Required |
| paymethodid | int | The id of the payment method to update | Required |
| card_number | string | Credit Card Number. The card number to update for a CreditCard or RemoteCreditCard Pay Method. Optional. Only provide if you wish to make an update | Optional |
| card_expiry | string | The expiry date to update for a CreditCard or RemoteCreditCard Pay Method. Format 'MMYY' eg 0122. Optional. Only provide if you wish to make an update | Optional |
| card_start | string | The start date to update for a CreditCard or RemoteCreditCard Pay Method. Format 'MMYY' 'eg' 0122. Optional. Only provide if you wish to make an update | Optional |
| card_issue_number | int | The issue_number to update for a CreditCard or RemoteCreditCard Pay Method. Optional. Only provide if you wish to make an update | Optional |
| bank_name | string | The name of the bank. Optional. Only provide if you wish to make an update | Optional |
| bank_account_type | string | The type of bank account (checking, credit etc). Optional. Only provide if you wish to make an update | Optional |
| bank_code | string | The bank code. Also called sort code or routing number. Optional. Only provide if you wish to make an update | Optional |
| bank_account | string | The account number. Required for BankAccount type. Optional. Only provide if you wish to make an update | Optional |
| set_as_default | bool | Should the new Pay Method be the client default | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| paymethodid | int | The id of the updated Pay Method |
| clientid | int | The id of the client |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'UpdatePayMethod',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'paymethodid' => '1',
            'clientid' => '1',
            'card_expiry' => '1025',
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
$command = 'UpdatePayMethod';
$postData = array(
    'paymethodid' => '1',
    'clientid' => '1',
    'card_expiry' => '1025',
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

* Pay Method ID is Required
* Client ID is Required
* Invalid Pay Method ID
* Pay Method does not belong to passed Client ID
* Unsupported Gateway Type for Update
* No Details Provided for Update
* Unable to Update Card Number for Assisted Gateway
* Expiry Date is invalid
* Start Date is invalid
* Issue Number is invalid
* Error Updating Remote Pay Method: xxx (message from gateway)


### Version History

| Version | Changelog |
| ------- | --------- |
| 7.8.0 | Initial Version |
