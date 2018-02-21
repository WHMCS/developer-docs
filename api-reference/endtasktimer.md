+++
title = "EndTaskTimer"
toc = true
+++

Ends a started timer for a project

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "EndTaskTimer" | Required |
| timerid | int | The id of the task to be ended | Required |
| projectid | int | The id of the project for the task timer | Optional |
| adminid | int | The admin id to associate the timer with | Optional |
| end_time | int | The end time as a unix time stamp. Defaults to time() if not provided | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| message | string | 'Timer Has Ended' |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'EndTaskTimer',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'projectid' => '1',
            'timerid' => '1',
            'adminid' => '2',
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
$command = 'EndTaskTimer';
$postData = array(
    'projectid' => '1',
    'timerid' => '1',
    'adminid' => '2',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "message": "Timer Has Ended"
}
```


### Error Responses

Possible error condition responses include:

* Project ID Not Found
* Timer ID Not Set
* Timer ID Not Found
* Admin ID Not Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
