+++
title = "GetInvoice"
toc = true
+++

Retrieve a specific invoice

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetInvoice" | Required |
| invoiceid | int | The ID of the invoice to retrieve. | Required |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| invoiceid | int | The ID of the invoice. |
| invoicenum | string | The Sequential Invoice Number assigned (if enabled). |
| userid | int | The ID of the user who owns this invoice. |
| date | string | The date of the invoice. Format: `YYYY-MM-DD` |
| duedate | string | The due date of the invoice. Format: `YYYY-MM-DD` |
| datepaid | string | The date the invoice was paid. Format: `YYYY-MM-DD HH:ii:ss` |
| subtotal | float | The subtotal on the invoice. |
| credit | float | The amount of credit assigned to the invoice. |
| tax | float | The amount of first-level tax charged on the invoice. |
| tax2 | float | The amount of second-level tax charged on the invoice. |
| total | float | The total of the invoice. |
| balance | float | The amount left to pay on the invoice. |
| taxrate | float | The rate of the first-level tax. |
| taxrate2 | float | The rate of the second-level tax. |
| status | string | The status of the invoice. |
| paymentmethod | string | The payment method on the invoice, in system format. |
| notes | string | The notes associated with the invoice. |
| ccgateway | bool | Whether the payment method is a credit card gateway that can be submitted to attempt capture. |
| items | array | The items on the invoice. |
| transactions | array | The transactions on the invoice. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetInvoice',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'invoiceid' => '1',
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
$command = 'GetInvoice';
$postData = array(
    'invoiceid' => '1',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "invoiceid": 1,
    "invoicenum": "",
    "userid": 2361,
    "date": "2016-01-01",
    "duedate": "2020-12-30",
    "datepaid": "0000-00-00 00:00:00",
    "lastcaptureattempt": "0000-00-00 00:00:00",
    "subtotal": "15.95",
    "credit": "0.00",
    "tax": "0.00",
    "tax2": "0.00",
    "total": "15.95",
    "balance": "15.95",
    "taxrate": "0.000",
    "taxrate2": "0.000",
    "status": "Unpaid",
    "paymentmethod": "paypalcheckout",
    "notes": "",
    "ccgateway": false,
    "items": {
        "item": [
            {
                "id": 1,
                "type": "Hosting",
                "relid": 1,
                "description": "Sample Monthly Product (01\/01\/2016 - 31\/01\/2016)",
                "amount": "15.95",
                "taxed": 0
            }
        ]
    },
    "transactions": ""
}
```


### Error Responses

Possible error condition responses include:

* Invoice ID Not Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
