+++
title = "GetAffiliates"
toc = true
+++

Obtain an array of affiliates

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetAffiliates" | Required |
| limitstart | int | The offset for the returned affiliate data (default: 0) | Optional |
| limitnum | int | The number of records to return (default: 25) | Optional |
| userid | int | Obtain affiliate data for a specific client account | Optional |
| visitors | int | Provide affiliates that match a specific visitor count | Optional |
| paytype | string | Provide affiliates matching the paytype provided. One of '', 'percentage', 'fixedamount' | Optional |
| payamount | float | Provide affiliates matching a specific overridden payout amount | Optional |
| onetime | int | Provide affiliates configured to receive one time affiliates | Optional |
| balance | float | Provide affiliates that have this balance | Optional |
| withdrawn | float | Provide affiliates that have withdrawn this amount | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| startnumber | int | The starting number for the returned results |
| numreturned | int | The number of results returned |
| affiliates | array | The affiliates entries returned |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetAffiliates',
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
$command = 'GetAffiliates';
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
    "totalresults": "2",
    "startnumber": "0",
    "numreturned": "2",
    "affiliates[affiliate][0][id]": "1",
    "affiliates[affiliate][0][date]": "2016-01-01",
    "affiliates[affiliate][0][clientid]": "1",
    "affiliates[affiliate][0][visitors]": "145",
    "affiliates[affiliate][0][paytype]": "percentage",
    "affiliates[affiliate][0][payamount]": "15.00",
    "affiliates[affiliate][0][onetime]": "1",
    "affiliates[affiliate][0][balance]": "15.00",
    "affiliates[affiliate][0][withdrawn]": "0.00",
    "affiliates[affiliate][0][created_at]": "0000-00-00 00:00:00",
    "affiliates[affiliate][0][updated_at]": "0000-00-00 00:00:00",
    "affiliates[affiliate][1][id]": "1",
    "affiliates[affiliate][1][date]": "2016-01-08",
    "affiliates[affiliate][1][clientid]": "4",
    "affiliates[affiliate][1][visitors]": "0",
    "affiliates[affiliate][1][paytype]": "",
    "affiliates[affiliate][1][payamount]": "0.00",
    "affiliates[affiliate][1][onetime]": "1",
    "affiliates[affiliate][1][balance]": "0.00",
    "affiliates[affiliate][1][withdrawn]": "0.00",
    "affiliates[affiliate][1][created_at]": "0000-00-00 00:00:00",
    "affiliates[affiliate][1][updated_at]": "0000-00-00 00:00:00"
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
