+++
title = "GetOrders"
toc = true
+++

Obtain orders matching the passed criteria

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetOrders" | Required |
| limitstart | int | The offset for the returned order data (default: 0) | Optional |
| limitnum | int | The number of records to return (default: 25) | Optional |
| id | int | Find orders for a specific id | Optional |
| userid | int | Find orders for a specific client id | Optional |
| requestor_id | int | Find orders for a specific requestor id | Optional |
| status | string | Find orders for a specific status | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available |
| startnumber | int | The starting number for the returned results |
| numreturned | int | The number of results returned |
| orders | array | An array of orders matching the criteria passed |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetOrders',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'id' => '1',
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
$command = 'GetOrders';
$postData = array(
    'id' => '1',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "totalresults": 1,
    "startnumber": 0,
    "numreturned": 1,
    "orders": {
        "order": [
            {
                "id": 1,
                "ordernum": 7858259149,
                "userid": 1,
                "contactid": 0,
                "requestor_id": 1,
                "admin_requestor_id": 0,
                "date": "2020-09-23 13:59:35",
                "nameservers": "",
                "transfersecret": "",
                "renewals": "",
                "renewalsByType": {
                    "domains": [],
                    "services": [],
                    "addons": []
                },
                "promocode": "",
                "promotype": "",
                "promovalue": "",
                "orderdata": "}",
                "amount": "8.00",
                "paymentmethod": "stripe",
                "invoiceid": 1,
                "status": "Active",
                "ipaddress": "123.456.789.110",
                "fraudmodule": "fraudlabs",
                "fraudoutput": "{\"is_country_match\":\"Y\",\"is_high_risk_country\":\"N\",\"distance_in_km\":484.990000000000009094947017729282379150390625,\"distance_in_mile\":301.3600000000000136424205265939235687255859375,\"ip_country\":\"US\",\"ip_continent\":\"North America\",\"ip_region\":\"Texas\",\"ip_city\":\"Houston\",\"ip_latitude\":\"29.8284\",\"ip_longitude\":\"-95.4696\",\"ip_timezone\":\"-04:00\",\"ip_elevation\":\"104\",\"ip_domain\":\"whmcs.com\",\"ip_mobile_mnc\":\"NA\",\"ip_mobile_mcc\":\"NA\",\"ip_mobile_brand\":\"NA\",\"ip_netspeed\":\"DSL\",\"ip_isp_name\":\"WHMCS\",\"ip_usage_type\":\"Commercial\",\"is_free_email\":\"Y\",\"is_new_domain_name\":\"N\",\"is_domain_exists\":\"Y\",\"is_proxy_ip_address\":\"N\",\"is_bin_found\":\"NA\",\"is_bin_country_match\":\"NA\",\"is_bin_name_match\":\"NA\",\"is_bin_phone_match\":\"NA\",\"is_bin_prepaid\":\"NA\",\"is_address_ship_forward\":\"N\",\"is_bill_ship_city_match\":\"Y\",\"is_bill_ship_state_match\":\"Y\",\"is_bill_ship_country_match\":\"Y\",\"is_bill_ship_postal_match\":\"Y\",\"is_ship_address_blacklist\":\"N\",\"is_phone_blacklist\":\"N\",\"is_ip_blacklist\":\"N\",\"is_email_blacklist\":\"N\",\"is_credit_card_blacklist\":\"NA\",\"is_device_blacklist\":\"NA\",\"is_user_blacklist\":\"NA\",\"is_high_risk_username\":\"NA\",\"is_export_controlled_country\":\"NA\",\"is_malware_exploit\":\"NA\",\"user_order_id\":\"7858259149\",\"user_order_memo\":\"\",\"fraudlabspro_score\":14,\"fraudlabspro_distribution\":\"57\",\"fraudlabspro_status\":\"APPROVE\",\"fraudlabspro_id\":\"20200923-SAMPLE\",\"fraudlabspro_version\":\"1.5.1\",\"fraudlabspro_error_code\":\"\",\"fraudlabspro_message\":\"\",\"fraudlabspro_credits\":496,\"http_response_code\":200}",
                "notes": "Sample Notes!",
                "paymentmethodname": "Stripe",
                "paymentstatus": "Paid",
                "name": "WHMCS Tester",
                "currencyprefix": "$",
                "currencysuffix": "USD",
                "frauddata": "",
                "validationdata": "",
                "lineitems": {
                    "lineitem": [
                        {
                            "type": "product",
                            "relid": 1,
                            "producttype": "Other Product\/Service",
                            "product": "SSL Certificates - Rapid SSL",
                            "domain": "sampledomain.com",
                            "billingcycle": "One-Time",
                            "amount": "8.00",
                            "status": "Active"
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
