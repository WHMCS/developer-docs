+++
title = "GetInvoices"
toc = true
+++

Retrieve a specific invoice

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetInvoices" | Required |
| limitstart | int | The offset for the returned invoice data (default: 0) | Optional |
| limitnum | int | The number of records to return (default: 25) | Optional |
| userid | int | Find invoices for a specific client id | Optional |
| status | string | Find invoices for a specific status. Standard Invoice statuses plus Overdue | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| startnumber | int | The starting number for the returned results |
| numreturned | int | The number of results returned |
| invoices | array | An array of invoices matching the criteria passed |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetInvoices',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'userid' => '1',
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
$command = 'GetInvoices';
$postData = array(
    'userid' => '1',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "totalresults": "1",
    "startnumber": "0",
    "numreturned": "1",
    "invoices[invoice][0][id]": "1",
    "invoices[invoice][0][userid]": "1",
    "invoices[invoice][0][firstname]": "Test",
    "invoices[invoice][0][lastname]": "Client",
    "invoices[invoice][0][companyname]": "",
    "invoices[invoice][0][invoicenum]": "",
    "invoices[invoice][0][date]": "2016-01-01",
    "invoices[invoice][0][duedate]": "2016-01-08",
    "invoices[invoice][0][datepaid]": "0000-00-00 00:00:00",
    "invoices[invoice][0][subtotal]": "15.95",
    "invoices[invoice][0][credit]": "0.00",
    "invoices[invoice][0][tax]": "0.00",
    "invoices[invoice][0][tax2]": "0.00",
    "invoices[invoice][0][total]": "15.95",
    "invoices[invoice][0][taxrate]": "0.00",
    "invoices[invoice][0][taxrate2]": "0.00",
    "invoices[invoice][0][status]": "Unpaid",
    "invoices[invoice][0][paymentmethod]": "authorize",
    "invoices[invoice][0][notes]": "",
    "invoices[invoice][0][currencycode]": "USD",
    "invoices[invoice][0][currencyprefix]": "$",
    "invoices[invoice][0][currencysuffix]": "USD"
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
