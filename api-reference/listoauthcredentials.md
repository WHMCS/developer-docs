+++
title = "ListOAuthCredentials"
toc = true
+++

List OAuth Credentials matching passed criteria

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "ListOAuthCredentials" | Required |
| grantType | string | Find credentials for a specific grant type | Optional |
| sortField | string | Sort the response using the passed field | Optional |
| sortOrder | string | The direction of the sort order ('ASC', 'DESC') | Optional |
| limit | int | To limit the number of returned credentials | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| clients | array | An array of client oAuth credentials |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'ListOAuthCredentials',
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
$command = 'ListOAuthCredentials';
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
    "clients": [
        {
            "credentialId": 1,
            "name": "",
            "description": "",
            "grantTypes": "single_sign_on",
            "scope": "clientarea:sso clientarea:profile clientarea:billing_info clientarea:emails clientarea:announcements clientarea:downloads clientarea:knowledgebase clientarea:network_status clientarea:product_details clientarea:invoices clientarea:tickets clientarea:submit_ticket clientarea:shopping_cart_addons clientarea:shopping_cart_domain_register clientarea:shopping_cart_domain_transfer",
            "clientIdentifier": "COMPANY-NAME.+ddPpB4+MVU5jeacL\/iEiw==",
            "clientSecret": "cl\/1zwMst0mtoAFLrTL\/3PAneaOXJ51ipoY86sKkapZM3WPKEwUK\/jhxXOAn2ErqXZNTJFnv2isNyYE0fgjgqQ==",
            "uuid": null,
            "serviceId": 1,
            "logoUri": "",
            "redirectUri": [],
            "rsaKeyPairId": 0,
            "createdAt": "18th November 2016 9:32:24am",
            "updatedAt": "18th November 2016 9:32:24am"
        },
        {
            "credentialId": 2,
            "name": "",
            "description": "",
            "grantTypes": "single_sign_on",
            "scope": "clientarea:sso clientarea:profile clientarea:billing_info clientarea:emails clientarea:announcements clientarea:downloads clientarea:knowledgebase clientarea:network_status clientarea:product_details clientarea:invoices clientarea:tickets clientarea:submit_ticket clientarea:shopping_cart_addons clientarea:shopping_cart_domain_register clientarea:shopping_cart_domain_transfer",
            "clientIdentifier": "COMPANY-NAME.98x4Dkq4JXjj3SpAqn14+Q==",
            "clientSecret": "uKw1nmFF9XOHUynCHIcAGBmFsrlMHrD\/5GyUyY\/Ghw4toDI8wQ63XqY6maAtF5Vb02SgI6tqyNbd1BmPzPd9AQ==",
            "uuid": null,
            "serviceId": 1,
            "logoUri": "",
            "redirectUri": [],
            "rsaKeyPairId": 0,
            "createdAt": "18th November 2016 9:33:01am",
            "updatedAt": "18th November 2016 9:33:01am"
        },
        {
            "credentialId": 3,
            "name": "",
            "description": "",
            "grantTypes": "single_sign_on",
            "scope": "clientarea:sso clientarea:profile clientarea:billing_info clientarea:emails clientarea:announcements clientarea:downloads clientarea:knowledgebase clientarea:network_status clientarea:product_details clientarea:invoices clientarea:tickets clientarea:submit_ticket clientarea:shopping_cart_addons clientarea:shopping_cart_domain_register clientarea:shopping_cart_domain_transfer",
            "clientIdentifier": "COMPANY-NAME.mY7l7Iz9NuXOeUleDM8rpQ==",
            "clientSecret": "O12n9lVX5OMv2SgMJ3u+p7q\/RVhuXybwdNbNOnDBdAci4U3kD3X8H1M9WRr4NuUb9fPTMbD3ySxUan9qf8gsdQ==",
            "uuid": null,
            "serviceId": 1,
            "logoUri": "",
            "redirectUri": [],
            "rsaKeyPairId": 0,
            "createdAt": "18th November 2016 9:35:20am",
            "updatedAt": "18th November 2016 9:35:20am"
        }
    ]
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
