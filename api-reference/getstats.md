+++
title = "GetStats"
toc = true
+++

Obtain system statistics

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetStats" | Required |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| income_today | float | The total income today |
| income_thismonth | float | The total income this month |
| income_thisyear | float | The total income this year |
| income_alltime | float | The total income for all time |
| orders_pending | int | The count of pending orders |
| orders_today_cancelled | int | The count of cancelled orders with todays date |
| orders_today_pending | int | The count of pending orders with todays date |
| orders_today_fraud | int | The count of fraud orders with todays date |
| orders_today_active | int | The count of active orders with todays date |
| orders_today_total | int | The count of orders with todays date |
| orders_yesterday_cancelled | int | The count of cancelled orders with yesterdays date |
| orders_yesterday_pending | int | The count of pending orders with yesterdays date |
| orders_yesterday_fraud | int | The count of fraud orders with yesterdays date |
| orders_yesterday_active | int | The count of active orders with yesterdays date |
| orders_yesterday_total | int | The count of orders with yesterdays date |
| orders_thismonth_total | int | The count of orders for this month |
| orders_thisyear_total | int | The count of orders for this year |
| tickets_allactive | int | The count of active tickets |
| tickets_awaitingreply | int | The count of awaiting reply tickets |
| tickets_flaggedtickets | int | The count of tickets flagged to the admin user making the api call |
| tickets_open | int | The count of tickets in Open status |
| tickets_answered | int | The count of tickets in Answered status |
| tickets_customerreply | int | The count of tickets in Customer Reply status |
| tickets_closed | int | The count of tickets in Closed status |
| tickets_onhold | int | The count of tickets in On Hold status |
| tickets_inprogress | int | The count of tickets in In Progress status |
| cancellations_pending | int | The count of pending cancellations |
| todoitems_due | int | The count of to do items due |
| networkissues_open | int | The count open network issues |
| quotes_valid | int | The count of valid quotes |
| staff_online | int | The count of staff online |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetStats',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
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
$command = 'GetStats';
$postData = array(
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "income_today": "$0.00 USD",
    "income_thismonth": "$1656.35 USD",
    "income_thisyear": "$9028.40 USD",
    "income_alltime": "$9028.40 USD",
    "orders_pending": "0",
    "orders_today_cancelled": 0,
    "orders_today_pending": 0,
    "orders_today_fraud": 0,
    "orders_today_active": 0,
    "orders_today_total": 0,
    "orders_yesterday_cancelled": 0,
    "orders_yesterday_pending": 0,
    "orders_yesterday_fraud": 0,
    "orders_yesterday_active": 0,
    "orders_yesterday_total": 0,
    "orders_thismonth_total": "13",
    "orders_thisyear_total": "71",
    "tickets_allactive": 0,
    "tickets_awaitingreply": 0,
    "tickets_flaggedtickets": 0,
    "tickets_open": 0,
    "tickets_answered": 0,
    "tickets_customerreply": 0,
    "tickets_closed": 0,
    "tickets_onhold": 0,
    "tickets_inprogress": 0,
    "cancellations_pending": "0",
    "todoitems_due": "0",
    "networkissues_open": "0",
    "billableitems_uninvoiced": "0",
    "quotes_valid": "1",
    "staff_online": "1"
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
