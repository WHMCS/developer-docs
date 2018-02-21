+++
title = "GetClientsDomains"
toc = true
+++

Obtain a list of Client Purchased Domains matching the provided criteria

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetClientsDomains" | Required |
| limitstart | int | The offset for the returned log data (default: 0) | Optional |
| limitnum | int | The number of records to return (default: 25) | Optional |
| clientid | int | The client id to obtain the details for. | Optional |
| domainid | int | The specific domain id to obtain the details for | Optional |
| domain | string | The specific domain to obtain the details for | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| clientid | int | The specific client id searched for |
| domainid | int | The specific domain id searched for |
| totalresults | int | The total number of results available |
| startnumber | int | The starting number for the returned results |
| numreturned | int | The total number of results returned |
| domains | array | The domains that match the criteria passed |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetClientsDomains',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'clientid' => '1',
            'stats' => true,
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
$command = 'GetClientsDomains';
$postData = array(
    'clientid' => '1',
    'stats' => true,
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "clientid": "1",
    "domainid": "",
    "totalresults": "2",
    "startnumber": "0",
    "numreturned": "2",
    "domains[domain][0][id]": "1",
    "domains[domain][0][userid]": "1",
    "domains[domain][0][orderid]": "1",
    "domains[domain][0][regtype]": "Register",
    "domains[domain][0][domainname]": "whmcs.rocks",
    "domains[domain][0][registrar]": "enom",
    "domains[domain][0][regperiod]": "1",
    "domains[domain][0][firstpaymentamount]": "12.95",
    "domains[domain][0][recurringamount]": "12.95",
    "domains[domain][0][paymentmethod]": "authorize",
    "domains[domain][0][paymentmethodname]": "Credit Card",
    "domains[domain][0][regdate]": "2016-01-01",
    "domains[domain][0][expirydate]": "2017-01-01",
    "domains[domain][0][nextduedate]": "2016-01-01",
    "domains[domain][0][status]": "Active",
    "domains[domain][0][subscriptionid]": "",
    "domains[domain][0][promoid]": "0",
    "domains[domain][0][dnsmanagement]": "0",
    "domains[domain][0][emailforwarding]": "0",
    "domains[domain][0][idprotection]": "0",
    "domains[domain][0][donotrenew]": "0",
    "domains[domain][0][notes]": "",
    "domains[domain][1][id]": "2",
    "domains[domain][1][userid]": "1",
    "domains[domain][1][orderid]": "2",
    "domains[domain][1][regtype]": "Register",
    "domains[domain][1][domainname]": "whmcs.info",
    "domains[domain][1][registrar]": "enom",
    "domains[domain][1][regperiod]": "1",
    "domains[domain][1][firstpaymentamount]": "12.95",
    "domains[domain][1][recurringamount]": "12.95",
    "domains[domain][1][paymentmethod]": "authorize",
    "domains[domain][1][paymentmethodname]": "Credit Card",
    "domains[domain][1][regdate]": "2016-01-01",
    "domains[domain][1][expirydate]": "2017-01-01",
    "domains[domain][1][nextduedate]": "2016-01-01",
    "domains[domain][1][status]": "Active",
    "domains[domain][1][subscriptionid]": "",
    "domains[domain][1][promoid]": "0",
    "domains[domain][1][dnsmanagement]": "0",
    "domains[domain][1][emailforwarding]": "0",
    "domains[domain][1][idprotection]": "0",
    "domains[domain][1][donotrenew]": "0",
    "domains[domain][1][notes]": ""
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
