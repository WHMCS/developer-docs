+++
title = "CreateInvoice"
toc = true
+++

Create an invoice using the provided parameters.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "CreateInvoice" | Required |
| userid | int | The ID of the client to create the invoice for. | Required |
| status | string | The status of the invoice being created. Defaults to `unpaid`. | Optional |
| draft | bool | Whether to create the invoice in draft status. (You do not need to pass `$status` with this.) | Optional |
| sendinvoice | bool | Whether to send the Invoice Created Email to the client. (You can't use this with `$draft`.) | Optional |
| paymentmethod | string | The payment method of the created invoice, in system format. | Optional |
| taxrate | float | The first-level tax rate to apply to the invoice to override the system default. | Optional |
| taxrate2 | float | The second-level tax rate to apply to the invoice to override the system default. | Optional |
| date | string | The creation date that the invoice should display. Format: YYYY-mm-dd | Optional |
| duedate | string | The due date of the newly-created invoice. Format: YYYY-mm-dd | Optional |
| notes | string | The notes to appear on the created invoice. | Optional |
| itemdescriptionx | string | The line item's description. `X` is an integer to add multiple invoice items. | Optional |
| itemamountx | float | The line item's amount. | Optional |
| itemtaxedx | bool | The line item's taxed value. | Optional |
| autoapplycredit | bool | Whether to automatically apply credit from the client account to the invoice. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| invoiceid | int | The ID of the newly-created invoice. |
| status | string | The status of the newly-created invoice. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'CreateInvoice',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'userid' => '1',
            'status' => 'Unpaid',
            'sendinvoice' => '1',
            'paymentmethod' => 'mailin',
            'taxrate' => '10.00',
            'date' => '2016-01-01',
            'duedate' => '2016-01-08',
            'itemdescription1' => 'Sample Invoice Item',
            'itemamount1' => '15.95',
            'itemtaxed1' => '0',
            'itemdescription2' => 'Sample Second Invoice Item',
            'itemamount2' => '1.00',
            'itemtaxed2' => '1',
            'autoapplycredit' => '0',
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
$command = 'CreateInvoice';
$postData = array(
    'userid' => '1',
    'status' => 'Unpaid',
    'sendinvoice' => '1',
    'paymentmethod' => 'mailin',
    'taxrate' => '10.00',
    'date' => '2016-01-01',
    'duedate' => '2016-01-08',
    'itemdescription1' => 'Sample Invoice Item',
    'itemamount1' => '15.95',
    'itemtaxed1' => '0',
    'itemdescription2' => 'Sample Second Invoice Item',
    'itemamount2' => '1.00',
    'itemtaxed2' => '1',
    'autoapplycredit' => '0',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "invoiceid": "1",
    "status": "Unpaid"
}
```


### Error Responses

Possible error condition responses include:

* Client ID Not Found
* Cannot create and send a draft invoice in a single API request. Please create and send separately.


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
