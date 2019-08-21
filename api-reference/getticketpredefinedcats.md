+++
title = "GetTicketPredefinedCats"
toc = true
+++

Obtain the Predefined Ticket Reply Categories

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetTicketPredefinedCats" | Required |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results being returned |
| categories | array | An array of the reply categories |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetTicketPredefinedCats',
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
$command = 'GetTicketPredefinedCats';
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
    "totalresults": "4",
    "categories": {
        "category": [
            {
                "id": "3",
                "parentid": "0",
                "name": "Quick Reference",
                "replycount": "1"
            },
            {
                "id": "1",
                "parentid": "0",
                "name": "Sales",
                "replycount": "1"
            },
            {
                "id": "4",
                "parentid": "2",
                "name": "Sub-Support 1",
                "replycount": "1"
            },
            {
                "id": "2",
                "parentid": "0",
                "name": "Support",
                "replycount": "1"
            }
        ]
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
