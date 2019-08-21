+++
title = "DomainUpdateNameservers"
toc = true
+++

Sends the Save Nameservers command to the registrar for the domain

Connects to the registrar and attempts to update the nameservers with those provided.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "DomainUpdateNameservers" | Required |
| domainid | int | The id of the domain to update the nameservers for *recommended* | Optional |
| domain | string | The domain name to be update the nameservers for. This or $domainid is required | Optional |
| ns1 | string | The first nameserver | Required |
| ns2 | string | The second nameserver | Required |
| ns3 | string | The third nameserver | Optional |
| ns4 | string | The fourth nameserver | Optional |
| ns5 | string | The fifth nameserver | Optional |

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
            'action' => 'DomainUpdateNameservers',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'domainid' => '1',
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
$command = 'DomainUpdateNameservers';
$postData = array(
    'domainid' => '1',
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

* Domain ID Not Found
* ns1 and ns2 required
* Registrar Error Message


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
