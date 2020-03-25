+++
title = "GetModuleQueue"
toc = true
+++

Obtains the Module Queue for Incomplete Failed Actions

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetModuleQueue" | Required |
| relatedId | int | The id of the service to load. Used in conjunction with $serviceType | Optional |
| serviceType | string | The type of service to load ('domain', 'service', 'addon' or '')) | Optional |
| moduleName | string | The module name to obtain the queue for in system format. eg cpanel | Optional |
| moduleAction | string | The module action to obtain the queue for. eg CreateAccount, SuspendAccount | Optional |
| since | string | The date/time since to obtain the items. Format Y-m-d Can include H:i:s | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| count | int | The count of queue items returned |
| queue | \Queue[] | A collection for queue items |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetModuleQueue',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'serviceType' => 'service',
            'moduleName' => 'cpanel',
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
$command = 'GetModuleQueue';
$postData = array(
    'serviceType' => 'service',
    'moduleName' => 'cpanel',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "count": "1",
    "queue[0][id]": "1",
    "queue[0][serviceType]": "service",
    "queue[0][serviceId]": "1",
    "queue[0][moduleName]": "cpanel",
    "queue[0][moduleAction]": "CreateAccount",
    "queue[0][lastAttempt]": "2016-11-01 09:00:02",
    "queue[0][lastAttemptError]": "Product attribute Package Name \"this_package_is_made_up\" not found on server",
    "queue[0][numRetries]": "0",
    "queue[0][completed]": "0",
    "queue[0][createdAt]": "2016-11-01 09:00:02",
    "queue[0][updatedAt]": "2016-11-01 09:00:02"
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 7.1.0-beta.1 | Initial Version |
| 7.10 | Added `relatedId` parameter. Added `addon` serviceType |
