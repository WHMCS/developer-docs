+++
title = "UpdateInvoice"
toc = true
+++

Create an invoice using the provided parameters.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateInvoice" | Required |
| invoiceid | int | The ID of the invoice to update | Required |
| status | string | The status of the invoice being | Optional |
| paymentmethod | string | The payment method of the invoice in system format | Optional |
| taxrate | float | The first level tax rate to apply to the invoice to override the system default | Optional |
| taxrate2 | float | The second level tax rate to apply to the invoice to override the system default | Optional |
| subtotal | float | Update the subtotal of the invoice | Optional |
| total | float | Update the total of the invoice | Optional |
| credit | float | Update the credit applied to the invoice | Optional |
| date | \Carbon\Carbon | The date that the invoice should show as created YYYY-mm-dd | Optional |
| duedate | \Carbon\Carbon | The due date of the invoice YYYY-mm-dd | Optional |
| datepaid | \Carbon\Carbon | The date paid of the invoice YYYY-mm-dd | Optional |
| notes | string | The notes to appear on the invoice | Optional |
| itemdescription | string[] | An array of lineItemId => Description of items to change | Optional |
| itemamount | float[] | An array of lineItemId => amount of items to change | Optional |
| itemtaxed | bool[] | An array of lineItemId => taxed of items to change | Optional |
| newitemdescription | string[] | The line items description | Optional |
| newitemamount | float[] | The line items amount | Optional |
| newitemtaxed | bool[] | The line items is taxed value | Optional |
| deletelineids | int[] | An array of line item ids to remove from the invoice | Optional |
| publish | bool | Publish the invoice | Optional |
| publishandsendemail | bool | Publish and email the invoice | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| invoiceid | int | The ID of the update invoice |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'UpdateInvoice',
            'username' => 'ADMIN_USERNAME',
            'password' => 'ADMIN_PASSWORD',
            'status' => 'Unpaid',
            'itemdescription[13]' => 'Sample Updated Invoice Item',
            'itemamount[13]' => '16.95',
            'itemtaxed[13]' => '0',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'UpdateInvoice';
$postData = array(
    'status' => 'Unpaid',
    'itemdescription[13]' => 'Sample Updated Invoice Item',
    'itemamount[13]' => '16.95',
    'itemtaxed[13]' => '0',
);
$adminUsername = 'ADMIN_USERNAME';

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "invoiceid": "1"
}
```


### Error Responses

Possible error condition responses include:

* Invoice ID Not Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
