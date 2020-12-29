+++
title = "GetInvoices"
toc = true
+++

Retrieve a list of invoices.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetInvoices" | Required |
| limitstart | int | The offset for the returned invoice data (default: 0) | Optional |
| limitnum | int | The number of records to return (default: 25) | Optional |
| userid | int | Find invoices for a specific client id | Optional |
| status | string | Find invoices for a specific status. Standard Invoice statuses plus Overdue | Optional |
| orderby | string | The field to sort results by. Accepted values are: id, invoicenumber, date, duedate, total, status | Optional |
| order | string | Order sort attribute. Accepted values are: asc or desc. | Optional |

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
            'orderby' => 'invoicenumber',
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
    'orderby' => 'invoicenumber',
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
    "startnumber": 0,
    "numreturned": 1,
    "invoices": {
        "invoice": [
            {
                "id": 1,
                "userid": 1,
                "firstname": "Test",
                "lastname": "Client",
                "companyname": "",
                "invoicenum": "",
                "date": "2016-01-01",
                "duedate": "2016-01-08",
                "datepaid": "0000-00-00 00:00:00",
                "last_capture_attempt": "0000-00-00 00:00:00",
                "date_refunded": "0000-00-00 00:00:00",
                "date_cancelled": "0000-00-00 00:00:00",
                "subtotal": "15.95",
                "credit": "0.00",
                "tax": "0.00",
                "tax2": "0.00",
                "total": "15.95",
                "taxrate": "0.000",
                "taxrate2": "0.000",
                "status": "Unpaid",
                "paymentmethod": "paypalcheckout",
                "paymethodid": null,
                "notes": "",
                "created_at": "2016-01-08 14:06:34",
                "updated_at": "2016-01-08 14:07:17",
                "currencycode": "USD",
                "currencyprefix": "$",
                "currencysuffix": " USD"
            }
        ]
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 7.7 | Added `orderby` and `order` parameters to control returned sorting. |
