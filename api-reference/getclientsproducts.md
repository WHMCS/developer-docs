+++
title = "GetClientsProducts"
toc = true
+++

Obtain a list of Client Purchased Products matching the provided criteria

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetClientsDomains" | Required |
| limitstart | int | The offset for the returned log data (default: 0) | Optional |
| limitnum | int | The number of records to return (default: 25) | Optional |
| clientid | int | The client id to obtain the details for. | Optional |
| serviceid | int | The specific service id to obtain the details for | Optional |
| pid | int | The specific product id to obtain the details for | Optional |
| domain | string | The specific domain to obtain the service details for | Optional |
| username2 | string | The specific username to obtain the details for | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| clientid | int | The specific client id searched for |
| serviceid | int | The specific service id searched for |
| pid | int | The specific product id searched for |
| domain | string | The specific domain searched for |
| totalresults | int | The total number of results available |
| startnumber | int | The starting number for the returned results |
| numreturned | int | The total number of results returned |
| products | array | The products returned matching the criteria passed |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetClientsProducts',
            'username' => 'ADMIN_USERNAME',
            'password' => 'ADMIN_PASSWORD',
            'clientid' => '1',
            'stats' => 'true',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'GetClientsProducts';
$postData = array(
    'clientid' => '1',
    'stats' => 'true',
);
$adminUsername = 'ADMIN_USERNAME';

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "clientid": "1",
    "domainid": "",
    "totalresults": "1",
    "startnumber": "0",
    "numreturned": "1",
    "products[product][0][id]": "1",
    "products[product][0][clientid]": "1",
    "products[product][0][orderid]": "1",
    "products[product][0][pid]": "1",
    "products[product][0][regdate]": "2016-01-01",
    "products[product][0][name]": "Intel Xeon Dual Core 2.3Ghz",
    "products[product][0][translated_name]": "Intel Xeon Dual Core 2.3Ghz",
    "products[product][0][groupname]": "Dedicated Servers",
    "products[product][0][translated_groupname]": "Dedicated Servers",
    "products[product][0][domain]": "whmcs.rocks",
    "products[product][0][dedicatedip]": "",
    "products[product][0][serverid]": "0",
    "products[product][0][servername]": "",
    "products[product][0][serverip]": "",
    "products[product][0][serverhostname]": "",
    "products[product][0][suspensionreason]": "",
    "products[product][0][firstpaymentamount]": "174.00",
    "products[product][0][recurringamount]": "174.00",
    "products[product][0][paymentmethod]": "authorize",
    "products[product][0][paymentmethodname]": "Credit Card",
    "products[product][0][billingcycle]": "Monthly",
    "products[product][0][nextduedate]": "2016-02-01",
    "products[product][0][status]": "Active",
    "products[product][0][username]": "",
    "products[product][0][password]": "",
    "products[product][0][subscriptionid]": "",
    "products[product][0][promoid]": "0",
    "products[product][0][overideautosuspend]": "0",
    "products[product][0][overidesuspenduntil]": "0000-00-00",
    "products[product][0][ns1]": "",
    "products[product][0][ns2]": "",
    "products[product][0][assignedips]": "",
    "products[product][0][notes]": "",
    "products[product][0][diskusage]": "0",
    "products[product][0][disklimit]": "0",
    "products[product][0][bwusage]": "0",
    "products[product][0][bwlimit]": "0",
    "products[product][0][lastupdate]": "0000-00-00 00:00:00",
    "products[product][0][customfields][customfield]": "",
    "products[product][0][configoptions][configoption]": ""
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
