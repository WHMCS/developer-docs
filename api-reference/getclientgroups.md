+++
title = "GetClientGroups"
toc = true
+++

Obtain an array of client groups

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetClientGroups" | Required |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| groups | array | The client group entries returned |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetClientGroups',
            'username' => 'ADMIN_USERNAME',
            'password' => 'ADMIN_PASSWORD',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'GetClientGroups';
$postData = array(
);
$adminUsername = 'ADMIN_USERNAME';

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "totalresults": "2",
    "groups[group][0][id]": "1",
    "groups[group][0][groupname]": "Client Group 1",
    "groups[group][0][groupcolour]": "#28C99B",
    "groups[group][0][discountpercent]": "10.00",
    "groups[group][0][susptermexempt]": "on",
    "groups[group][0][separateinvoices]": "on",
    "groups[group][1][id]": "2",
    "groups[group][1][groupname]": "Client Group 2",
    "groups[group][1][groupcolour]": "#FFFFFF",
    "groups[group][1][discountpercent]": "0.00",
    "groups[group][1][susptermexempt]": "",
    "groups[group][1][separateinvoices]": ""
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
