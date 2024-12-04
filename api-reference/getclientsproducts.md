+++
title = "GetClientsProducts"
toc = true
+++

Obtain a list of Client Purchased Products matching the provided criteria

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetClientsProducts" | Required |
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
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'clientid' => '1',
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
$command = 'GetClientsProducts';
$postData = array(
    'clientid' => '1',
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
    "serviceid": null,
    "pid": null,
    "domain": null,
    "totalresults": "2",
    "startnumber": 0,
    "numreturned": 2,
    "products": {
        "product": [
            {
                "id": "1",
                "qty": "1",
                "clientid": "1",
                "orderid": "1",
                "ordernumber": "456789",
                "pid": "1",
                "regdate": "2015-01-01",
                "name": "Starter",
                "translated_name": "Starter",
                "groupname": "Shared Hosting",
                "translated_groupname": "Shared Hosting",
                "domain": "demodomain.com",
                "dedicatedip": "",
                "serverid": "1",
                "servername": "Saturn",
                "serverip": "1.2.3.4",
                "serverhostname": "saturn.example.com",
                "suspensionreason": "",
                "firstpaymentamount": "12.95",
                "recurringamount": "12.95",
                "paymentmethod": "authorize",
                "paymentmethodname": "Credit Card",
                "billingcycle": "Monthly",
                "nextduedate": "2016-11-25",
                "status": "Terminated",
                "username": "demodoma",
                "password": "xxxxxxxx",
                "subscriptionid": "",
                "promoid": "0",
                "overideautosuspend": "",
                "overidesuspenduntil": "0000-00-00",
                "ns1": "",
                "ns2": "",
                "assignedips": "",
                "notes": "",
                "diskusage": "0",
                "disklimit": "0",
                "bwusage": "0",
                "bwlimit": "0",
                "lastupdate": "0000-00-00 00:00:00",
                "customfields": {
                    "customfield": []
                },
                "configoptions": {
                    "configoption": []
                }
            },
            {
                "id": "2",
                "qty": "2",
                "clientid": "1",
                "orderid": "2",
                "pid": "3",
                "regdate": "2015-05-20",
                "name": "Plus",
                "translated_name": "Plus",
                "groupname": "Shared Hosting",
                "translated_groupname": "Shared Hosting",
                "domain": "demodomain2.net",
                "dedicatedip": "",
                "serverid": "2",
                "servername": "Pluto",
                "serverip": "2.3.4.5",
                "serverhostname": "pluto.example.com",
                "suspensionreason": "",
                "firstpaymentamount": "24.95",
                "recurringamount": "24.95",
                "paymentmethod": "paypal",
                "paymentmethodname": "PayPal",
                "billingcycle": "Monthly",
                "nextduedate": "2017-01-20",
                "status": "Active",
                "username": "demodom2",
                "password": "xxxxxxxx",
                "subscriptionid": "",
                "promoid": "0",
                "overideautosuspend": "",
                "overidesuspenduntil": "0000-00-00",
                "ns1": "",
                "ns2": "",
                "assignedips": "",
                "notes": "",
                "diskusage": "0",
                "disklimit": "0",
                "bwusage": "0",
                "bwlimit": "0",
                "lastupdate": "0000-00-00 00:00:00",
                "customfields": {
                    "customfield": []
                },
                "configoptions": {
                    "configoption": [
                        {
                            "id": "1",
                            "option": "Sample Config Option",
                            "type": "dropdown",
                            "value": "Selected option value"
                        }
                    ]
                }
            }
        ]
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 8.12 | Added `qty` parameter |
