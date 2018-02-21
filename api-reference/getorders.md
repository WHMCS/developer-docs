+++
title = "GetOrders"
toc = true
+++

Obtain orders matching the passed criteria

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetOrders" | Required |
| limitstart | int | The offset for the returned order data (default: 0) | Optional |
| limitnum | int | The number of records to return (default: 25) | Optional |
| id | int | Find orders for a specific id | Optional |
| userid | int | Find orders for a specific client id | Optional |
| status | string | Find orders for a specific status | Optional |

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
            'action' => 'GetOrders',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'id' => '1',
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
$command = 'GetOrders';
$postData = array(
    'id' => '1',
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
    "orders[order][0][id]": "1",
    "orders[order][0][ordernum]": "8549045538",
    "orders[order][0][userid]": "1",
    "orders[order][0][contactid]": "0",
    "orders[order][0][date]": "2016-01-01 17:02:40",
    "orders[order][0][nameservers]": "",
    "orders[order][0][transfersecret]": "",
    "orders[order][0][renewals]": "",
    "orders[order][0][promocode]": "",
    "orders[order][0][promotype]": "",
    "orders[order][0][promovalue]": "",
    "orders[order][0][orderdata]": "a:0:}",
    "orders[order][0][amount]": "15.95",
    "orders[order][0][paymentmethod]": "paypal",
    "orders[order][0][invoiceid]": "1",
    "orders[order][0][status]": "Active",
    "orders[order][0][ipaddress]": "",
    "orders[order][0][fraudmodule]": "",
    "orders[order][0][fraudoutput]": "",
    "orders[order][0][notes]": "",
    "orders[order][0][paymentmethodname]": "PayPal",
    "orders[order][0][paymentstatus]": "Unpaid",
    "orders[order][0][name]": "Test Client",
    "orders[order][0][currencyprefix]": "$",
    "orders[order][0][currencysuffix]": " USD",
    "orders[order][0][frauddata]": "",
    "orders[order][0][lineitems][lineitem][0][type]": "product",
    "orders[order][0][lineitems][lineitem][0][relid]": "1",
    "orders[order][0][lineitems][lineitem][0][producttype]": "Other Product\/Service",
    "orders[order][0][lineitems][lineitem][0][product]": "SSL Certificates - Rapid SSL",
    "orders[order][0][lineitems][lineitem][0][domain] ": ">",
    "orders[order][0][lineitems][lineitem][0][billingcycle]": "Monthly",
    "orders[order][0][lineitems][lineitem][0][amount]": "$15.95 USD",
    "orders[order][0][lineitems][lineitem][0][status]": "Active"
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
