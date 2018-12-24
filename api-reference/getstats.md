+++
title = "GetStats"
toc = true
+++

Get business performance metrics and statistics.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetStats" | Required |
| timeline_days | int | (Optional) The number of days to retrieve timeline values for (max 90). | Optional |

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
| timeline_data | int | The historic daily counts for various metrics if `$timeline_days` was specified in call. |


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
            'timeline_days' => '7',
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
    'timeline_days' => '7',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "income_today": "$5.95 USD",
    "income_thismonth": "$101.45 USD",
    "income_thisyear": "$485.21 USD",
    "income_alltime": "$2485.25 USD",
    "orders_pending": 7,
    "orders_today_cancelled": 1,
    "orders_today_pending": 2,
    "orders_today_fraud": 1,
    "orders_today_active": 4,
    "orders_today_total": 8,
    "orders_yesterday_cancelled": 1,
    "orders_yesterday_pending": 2,
    "orders_yesterday_fraud": 0,
    "orders_yesterday_active": 2,
    "orders_yesterday_total": 4,
    "orders_thismonth_total": 18,
    "orders_thisyear_total": 124,
    "tickets_allactive": 60,
    "tickets_awaitingreply": 5,
    "tickets_flaggedtickets": 3,
    "tickets_open": 3,
    "tickets_answered": 25,
    "tickets_customerreply": 2,
    "tickets_closed": 245,
    "tickets_onhold": 30,
    "tickets_inprogress": 0,
    "cancellations_pending": 1,
    "todoitems_due": 5,
    "networkissues_open": 0,
    "billableitems_uninvoiced": 1,
    "quotes_valid": 2,
    "staff_online": 1,
    "timeline_data": {
        "new_orders": {
            "2018-11-30": 8,
            "2018-11-29": 4,
            "2018-11-28": 3,
            "2018-11-27": 5,
            "2018-11-26": 7,
            "2018-11-25": 9,
            "2018-11-24": 2
        },
        "accepted_orders": {
            "2018-11-30": 4,
            "2018-11-29": 2,
            "2018-11-28": 3,
            "2018-11-27": 4,
            "2018-11-26": 5,
            "2018-11-25": 8,
            "2018-11-24": 2
        },
        "income": {
            "2018-11-30": "5.95",
            "2018-11-29": "10.17",
            "2018-11-28": "15.30",
            "2018-11-27": "18.90",
            "2018-11-26": "17.45",
            "2018-11-25": "10.28",
            "2018-11-24": "5.18"
        },
        "expenditure": {
            "2018-11-30": "0.00",
            "2018-11-29": "0.00",
            "2018-11-28": "0.00",
            "2018-11-27": "0.00",
            "2018-11-26": "0.00",
            "2018-11-25": "0.00",
            "2018-11-24": "0.00"
        },
        "new_tickets": {
            "2018-11-30": 5,
            "2018-11-29": 7,
            "2018-11-28": 10,
            "2018-11-27": 8,
            "2018-11-26": 4,
            "2018-11-25": 9,
            "2018-11-24": 12
        }
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 7.7 | Added `timeline_data` parameter. |
