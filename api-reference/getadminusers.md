+++
title = "GetAdminUsers"
toc = true
+++

Retrieve a list of administrator user accounts.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetAdminUsers" | Required |
| roleid | int | An administrative role ID to filter for. | Optional |
| email | string | An email address to filter for. Partial matching supported. | Optional |
| include_disabled | bool | Pass as true to include disabled administrator user accounts in response. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| count | int | Total number of administrative users matching supplied criteria. |
| admin_users | array | An array of administrator users and their attributes. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetAdminUsers',
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
$command = 'GetAdminUsers';
$postData = array(
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "count": 2,
    "admin_users": [
        {
            "id": 1,
            "uuid": "41dac92c-2f1a-474b-bef8-5e9a7e46e101",
            "roleId": 1,
            "username": "Admin",
            "twoFactorAuthModule": "",
            "firstname": "Demo",
            "lastname": "User",
            "email": "demo@whmcs.com",
            "signature": "",
            "notes": "",
            "template": "blend",
            "language": "english",
            "isDisabled": 0,
            "loginAttempts": 0,
            "supportDepartmentIds": [
                "1",
                "2",
                "3"
            ],
            "receivesTicketNotifications": [
                "1",
                "2"
            ],
            "homepageWidgetsConfig": "",
            "hiddenHomepageWidgets": "",
            "created_at": "2018-01-01 00:00:00",
            "updated_at": "2018-09-04 09:51:26",
            "fullName": "Demo User",
            "gravatarHash": "56487cdd284a735449d029e062d654d7"
        },
        {
            "id": 2,
            "uuid": "",
            "roleId": 2,
            "username": "Georgina",
            "twoFactorAuthModule": "",
            "firstname": "Georgina",
            "lastname": "Williams",
            "email": "georgina.williams@whmcs.com",
            "signature": "",
            "notes": "",
            "template": "blend",
            "language": "english",
            "isDisabled": 0,
            "loginAttempts": 0,
            "supportDepartmentIds": [
                "2",
                "3"
            ],
            "receivesTicketNotifications": [
                ""
            ],
            "homepageWidgetsConfig": "",
            "hiddenHomepageWidgets": "",
            "created_at": "2018-01-01 00:00:00",
            "updated_at": "2018-05-01 12:54:16",
            "fullName": "Georgina Williams",
            "gravatarHash": "f8c28cf89551c390ae43938167d35cb8"
        }
    ]
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 7.7 | Initial Version |
