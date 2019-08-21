+++
title = "GetAnnouncements"
toc = true
+++

Obtain an array of announcements

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetAnnouncements" | Required |
| limitstart | int | The offset for the returned announcement data (default: 0) | Optional |
| limitnum | int | The number of records to return (default: 25) | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| startnumber | int | The starting number for the returned results |
| numreturned | int | The number of results returned |
| announcements | array | The announcement entries returned |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetAnnouncements',
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
$command = 'GetAnnouncements';
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
    "totalresults": "1",
    "startnumber": "0",
    "numreturned": "1",
    "announcements[announcement][0][id]": "1",
    "announcements[announcement][0][date]": "2016-02-24 21:27:04",
    "announcements[announcement][0][title]": "Thank you for choosing WHMCS!",
    "announcements[announcement][0][announcement]": "<p>Welcome to <a title=\"WHMCS\" href=\"https:\/\/whmcs.com\" target=\"_blank\">WHMCS<\/a>! You have made a great choice and we want to help you get up and running as quickly as possible.<\/p><p>This is a sample announcement. Announcements are a great way to keep your customers informed about news and special offers. You can edit or delete this announcement by logging into the admin area and navigating to <em>Support &gt; Announcements<\/em>.<\/p><p>If at any point you get stuck, our support team is available 24x7 to assist you. Simply visit <a title=\"www.whmcs.com\/support\" href=\"https:\/\/www.whmcs.com\/support\" target=\"_blank\">www.whmcs.com\/support<\/a> to request assistance.<\/p>",
    "announcements[announcement][0][published]": "1",
    "announcements[announcement][0][parentid]": "0",
    "announcements[announcement][0][language]": "",
    "announcements[announcement][0][created_at]": "0000-00-00 00:00:00",
    "announcements[announcement][0][updated_at]": "0000-00-00 00:00:00"
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
