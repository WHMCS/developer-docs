+++
title = "UpdateInvoice"
toc = true
+++

Update an invoice using the provided parameters.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateInvoice" | Required |
| invoiceid | int | The ID of the invoice to update. | Required |
| status | string | The status of the invoice being updated. | Optional |
| paymentmethod | string | The payment method of the invoice in system format. | Optional |
| taxrate | float | The first-level tax rate to apply to the invoice to override the system default. | Optional |
| taxrate2 | float | The second-level tax rate to apply to the invoice to override the system default. | Optional |
| credit | float | Update the credit applied to the invoice. | Optional |
| date | string | The date that the invoice should show as its creation date. Format: YYYY-mm-dd | Optional |
| duedate | string | The due date of the invoice. Format: YYYY-mm-dd | Optional |
| datepaid | string | The date paid for the invoice. Format: YYYY-mm-dd | Optional |
| notes | string | The notes to appear on the invoice. | Optional |
| itemdescription | string[] | An array of lineItemId => Description of items to change. The lineItemId is the ID of the item from the GetInvoice API command. | Optional |
| itemamount | float[] | An array of lineItemId => amount of items to change. Required if itemdescription is provided. | Optional |
| itemtaxed | bool[] | An array of lineItemId => taxed of items to change Required if itemdescription is provided. | Optional |
| newitemdescription | string[] | The line items description. This should be a numerically indexed array of new line item descriptions. | Optional |
| newitemamount | float[] | The line items amount. This should be a numerically indexed array of new line item amounts. | Optional |
| newitemtaxed | bool[] | Should the new line items be taxed. This should be a numerically indexed array of new line item taxed values. | Optional |
| deletelineids | int[] | An array of line item IDs to remove from the invoice. This is the ID of the line item, from GetInvoice API command. | Optional |
| publish | bool | Whether to publish the invoice. | Optional |
| publishandsendemail | bool | Whether to publish and email the invoice. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| invoiceid | int | The ID of the update invoice. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'UpdateInvoice',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'invoiceid' => '1',
            'status' => 'Unpaid',
            'itemdescription' => array(13 => 'Sample Updated Invoice Item'),
            'itemamount' => array(13 => 16.95),
            'itemtaxed' => array(13 => false),
            'newitemdescription' => array(0 => 'New Line Item 1', 1 => 'New Line Item 2'),
            'newitemamount' => array(0 => 10.00, 1 => 2.95),
            'newitemtaxed' => array(0 => true, 1 => false),
            'deletelineids' => array(11, 12),
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
$command = 'UpdateInvoice';
$postData = array(
    'invoiceid' => '1',
    'status' => 'Unpaid',
    'itemdescription' => array(13 => 'Sample Updated Invoice Item'),
    'itemamount' => array(13 => 16.95),
    'itemtaxed' => array(13 => false),
    'newitemdescription' => array(0 => 'New Line Item 1', 1 => 'New Line Item 2'),
    'newitemamount' => array(0 => 10.00, 1 => 2.95),
    'newitemtaxed' => array(0 => true, 1 => false),
    'deletelineids' => array(11, 12),
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

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
* Invoice must be in Draft status to be published
* Missing Variables: itemdescription, itemamount and itemtaxed are required for each item being changed
* Invalid status $status


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 7.8 | Removed `total`, `tax`, `tax2` and `subtotal` parameters. Adjust invoice items and tax rates to adjust these. |
