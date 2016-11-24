+++
title = "GetTicketCounts"
toc = true
+++

Get ticket counts.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetTicketCounts" | Required |
| ignoreDepartmentAssignments | bool | Pass as true to not adhere to the departments the API user is a member of. | Optional |
| includeCountsByStatus | bool | Pass as true to not adhere to the departments the API user is a member of. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetTicketCounts',
            'username' => 'ADMIN_USERNAME',
            'password' => 'ADMIN_PASSWORD',
            'ignoreDepartmentAssignments' => 'false',
            'IncludeCountsByStatus' => 'true',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'GetTicketCounts';
$postData = array(
    'ignoreDepartmentAssignments' => 'false',
    'IncludeCountsByStatus' => 'true',
);
$adminUsername = 'ADMIN_USERNAME';

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "filteredDepartments": "[1, 2, 3]",
    "allActive": "123",
    "awaitingReply": "100",
    "flaggedTickets": "15",
    "status": "[{\"title\": \"Open\", \"count\": \"60\"}, {\"title\": \"Answered\", \"count\": \"23\"}, {\"title\": \"Customer-Reply\", \"count\": \"40\"}]"
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
