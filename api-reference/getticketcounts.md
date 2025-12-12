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
| includeCountsByStatus | bool | Pass as true to include detailed counts by statuses | Optional |

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
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'ignoreDepartmentAssignments' => false,
            'includeCountsByStatus' => true,
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
$command = 'GetTicketCounts';
$postData = array(
    'ignoreDepartmentAssignments' => false,
    'includeCountsByStatus' => true,
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "filteredDepartments": [
        1,
        2,
        3
    ],
    "allActive": 123,
    "awaitingReply": 100,
    "flaggedTickets": 15,
    "status": {
        "open": {
            "title": "Open",
            "count": 60
        },
        "answered": {
            "title": "Answered",
            "count": 23
        },
        "customerreply": {
            "title": "Customer-Reply",
            "count": 40
        },
        "closed": {
            "title": "Closed",
            "count": 4220
        },
        "onhold": {
            "title": "On Hold",
            "count": 10
        },
        "inprogress": {
            "title": "In Progress",
            "count": 0
        }
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 9.0 | Return only ticket counts assigned to the same support department as the logged-in admin, unless $ignoreDepartmentAssignments is set to true |
