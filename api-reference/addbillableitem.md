+++
title = "AddBillableItem"
toc = true
+++

Adds a Billable Item

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AddBillableItem" | Required |
| clientid | int | The client to add the item to. | Required |
| description | string | The description of the Billable Item. This will appear on the invoice. | Required |
| amount | float | The total amount to invoice for. | Required |
| unit | string | Either 'hours' or 'quantity'. | Required |
| quantity | float | The number of units the billable items represents. Defaults to 0. | Optional |
| invoiceaction | string | One of 'noinvoice', 'nextcron', 'nextinvoice', 'duedate', or 'recur'. | Optional |
| recur | int | When `$invoiceaction=recur`. The frequency of the recurrence. | Optional |
| recurcycle | string | How often to recur the Billable Item. Days, Weeks, Months or Years. | Optional |
| recurfor | int | How many times the Billable Item should create an invoice. | Optional |
| duedate | string | Date the invoice should be due (only required for due date and recur invoice actions). YYYY-mm-dd | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| billableid | int | The ID of the newly created billable item. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'AddBillableItem',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'clientid' => '1',
            'description' => 'This is a billable item',
            'amount' => '10.00',
            'invoiceaction' => 'recur',
            'recur' => '1',
            'recurcycle' => 'Months',
            'recurfor' => '12',
            'duedate' => '2021-01-01',
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
$command = 'AddBillableItem';
$postData = array(
    'clientid' => '1',
    'description' => 'This is a billable item',
    'amount' => '10.00',
    'invoiceaction' => 'recur',
    'recur' => '1',
    'recurcycle' => 'Months',
    'recurfor' => '12',
    'duedate' => '2021-01-01',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "status": "success",
    "billableid": 1
}
```


### Error Responses

Possible error condition responses include:

* Client ID not Found
* You must provide a description
* Invalid Invoice Action
* Recurring must have a unit, cycle and limit
* Due date is required
* Invalid Unit, please specify either 'hours' or 'quantity'
* Invalid Date Format - Expected: 'YYYY-mm-dd'


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 8.2 | Renamed 'hours' parameter to `quantity`. Now Required |
| 8.2 | Added `unit` parameter. |
