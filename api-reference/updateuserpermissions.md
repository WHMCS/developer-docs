+++
title = "UpdateUserPermissions"
toc = true
+++

Update the permissions of a user for a client.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "UpdateUserPermissions" | Required |
| user_id | int | The id of the user to set the permissions for | Required |
| client_id | int | The id of the client to set the permissions for | Required |
| permissions | string | Comma separated list of permissions | Required |

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
            'action' => 'UpdateUserPermissions',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'user_id' => '1',
            'client_id' => '1',
            'permissions' => 'profile,contacts,products,manageproducts,productsso,domains,managedomains,invoices,quotes,tickets,affiliates,emails,orders',
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
$command = 'UpdateUserPermissions';
$postData = array(
    'user_id' => '1',
    'client_id' => '1',
    'permissions' => 'profile,contacts,products,manageproducts,productsso,domains,managedomains,invoices,quotes,tickets,affiliates,emails,orders',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success"
}
```


### Error Responses

Possible error condition responses include:

* Invalid user id
* Invalid client id
* Permissions cannot be set on a client owner
* Missing permissions definition
* User is not associated with client


### Version History

| Version | Changelog |
| ------- | --------- |
| 8.0.0 | Initial Version |
