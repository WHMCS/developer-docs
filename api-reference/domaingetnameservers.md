+++
title = "DomainGetNameservers"
toc = true
+++

Obtains the current nameservers for the domain.

Connects to the registrar and obtains the nameservers for the domain

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "DomainGetNameservers" | Required |
| domainid | int | The id of the domain to obtain the nameservers for | Required |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| ns1 | string | The first nameserver on the domain |
| ns2 | string | The second nameserver on the domain |
| ns3 | string | The third nameserver on the domain |
| ns4 | string | The fourth nameserver on the domain |
| ns5 | string | The fifth nameserver on the domain |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'DomainGetNameservers',
            'username' => 'ADMIN_USERNAME',
            'password' => 'ADMIN_PASSWORD',
            'domainid' => '1',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'DomainGetNameservers';
$postData = array(
    'domainid' => '1',
);
$adminUsername = 'ADMIN_USERNAME';

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "ns1": "ns1.example.com",
    "ns2": "ns1.example.com"
}
```


### Error Responses

Possible error condition responses include:

* Domain ID Not Found
* Registrar Function Not Supported
* Registrar Error Message


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
