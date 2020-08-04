+++
title = "UpdateUser"
toc = true
+++

Update a user.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateUser" | Required |
| user_id | int | The ID of the user to update | Required |
| firstname | string |  | Optional |
| lastname | string |  | Optional |
| email | string |  | Optional |
| language | string | Default language setting. Provide full name: 'english', 'french', etc... | Optional |

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
            'action' => 'UpdateUser',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'user_id' => '1',
            'firstname' => 'John',
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
$command = 'UpdateUser';
$postData = array(
    'user_id' => '1',
    'firstname' => 'John',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "user_id": "1"
}
```


### Error Responses

Possible error condition responses include:

* Invalid User ID requested
* One of `email`, `firstname`, `lastname`, or `language` is required
* The email address entered is not valid
* A user already exists with that email address


### Version History

| Version | Changelog |
| ------- | --------- |
| 8.0.0 | Initial Version |
