+++
title = "GetPayMethods"
toc = true
+++

Obtain the Pay Methods associated with a provided client id.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetPayMethods" | Required |
| clientid | int | The id of the client to obtain the Pay Methods for | Required |
| paymethodid | int | The id of a specific Pay Method to retrieve | Optional |
| type | string | The type of Pay Methods to return. 'BankAccount' or 'CreditCard' | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| clientid | int | The id of the client the Pay Methods are being returned for |
| paymethods | array | The Pay Methods matching the criteria |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetPayMethods',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'clientid' => '1',
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
$command = 'GetPayMethods';
$postData = array(
    'clientid' => '1',
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
    "paymethods": [
        {
            "id": 1,
            "type": "RemoteCreditCard",
            "description": "Default Card",
            "gateway_name": "stripe",
            "contact_type": "Client",
            "contact_id": 1,
            "card_last_four": "4242",
            "expiry_date": "02\/25",
            "start_date": "",
            "issue_number": "",
            "card_type": "Visa",
            "remote_token": "{\"customer\":\"xxx\",\"method\":\"xxx\"}",
            "last_updated": "17\/05\/2019 10:01"
        },
        {
            "id": 2,
            "type": "CreditCard",
            "description": "A Second Card Stored Locally",
            "gateway_name": "",
            "contact_type": "Client",
            "contact_id": 1,
            "card_last_four": "4242",
            "expiry_date": "11\/22",
            "start_date": "",
            "issue_number": "",
            "card_type": "Visa",
            "remote_token": "",
            "last_updated": "17\/05\/2019 10:21"
        },
        {
            "id": 3,
            "type": "BankAccount",
            "description": "A Bank Account",
            "gateway_name": "",
            "contact_type": "Client",
            "contact_id": 1,
            "bank_name": "Bank of America",
            "remote_token": "",
            "last_updated": "17\/05\/2019 10:01"
        },
        {
            "id": 4,
            "type": "RemoteBankAccount",
            "description": "A Remote Bank Account",
            "gateway_name": "gocardless",
            "contact_type": "Client",
            "contact_id": 1,
            "bank_name": "",
            "remote_token": "MD123456789",
            "last_updated": "17\/05\/2019 10:01"
        }
    ]
}
```


### Error Responses

Possible error condition responses include:

* Client ID Is Required
* Invalid Pay Method Type. Should be 'BankAccount' or 'CreditCard'
* Client Not Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 7.8.0 | Initial Version |
