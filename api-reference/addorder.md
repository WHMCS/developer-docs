+++
title = "AddOrder"
toc = true
+++

Adds an order to a client.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AddOrder" | Required |
| clientid | int |  | Required |
| paymentmethod | string | The payment method for the order in the system format. eg. paypal, mailin | Required |
| pid | int[] | The array of product ids to add the order for | Optional |
| domain | string[] | The array of domain names associated with the products/domains | Optional |
| billingcycle | string[] | The array of billing cycles for the products | Optional |
| domaintype | string[] | For domain registrations, an array of register or transfer values | Optional |
| regperiod | int[] | For domain registrations, the registration periods for the domains in the order | Optional |
| eppcode | string[] | For domain transfers. The epp codes for the domains being transferred in the order | Optional |
| nameserver1 | string | The first nameserver to apply to all domains in the order | Optional |
| nameserver2 | string | The second nameserver to apply to all domains in the order | Optional |
| nameserver3 | string | The third nameserver to apply to all domains in the order | Optional |
| nameserver4 | string | The fourth nameserver to apply to all domains in the order | Optional |
| nameserver5 | string | The fifth nameserver to apply to all domains in the order | Optional |
| customfields | string[] | an array of base64 encoded serialized array of product custom field values | Optional |
| configoptions | string[] | an array of base64 encoded serialized array of product configurable options values | Optional |
| priceoverride | float[] | Override the price of the product being ordered | Optional |
| promocode | string | The promotion code to apply to the order | Optional |
| promooverride | bool | Should the promotion apply to the order even without matching promotional products | Optional |
| affid | int | The affiliate id to associate with the order | Optional |
| noinvoice | bool | Set to true to suppress the invoice generating for the whole order | Optional |
| noinvoiceemail | bool | Set to try to suppress the Invoice Created email being sent for the order | Optional |
| noemail | bool | Set to true to suppress the Order Confirmation email being sent | Optional |
| addons | string[] | A comma separated list of addons to create on order with the products | Optional |
| hostname | string[] | The hostname of the server for VPS/Dedicated Server orders | Optional |
| ns1prefix | string[] | The first nameserver prefix for the VPS/Dedicated server. Eg. ns1 in ns1.hostname.com | Optional |
| ns2prefix | string[] | The second nameserver prefix for the VPS/Dedicated server. Eg. ns2 in ns2.hostname.com | Optional |
| rootpw | string[] | The second nameserver prefix for the VPS/Dedicated server. Eg. ns2 in ns2.hostname.com | Optional |
| contactid | int | The id of the contact, associated with the client, that should apply to all domains in the order | Optional |
| dnsmanagement | bool[] | Add DNS Management to the Domain Order | Optional |
| domainfields | string[] | an array of base64 encoded serialized array of TLD Specific Field Values | Optional |
| emailforwarding | bool[] | Add Email Forwarding to the Domain Order | Optional |
| idprotection | bool[] | Add ID Protection to the Domain Order | Optional |
| domainpriceoverride | float[] | Override the price of the registration price on the domain being ordered | Optional |
| domainrenewoverride | float[] | Override the price of the renewal price on the domain being ordered | Optional |
| domainrenewals | array | A name -> value array of $domainName -> $renewalPeriod renewals to add an order for | Optional |
| clientip | string | The ip address to associate with the order | Optional |
| addonid | int | The Addon ID for an Addon Only Order | Optional |
| serviceid | int | The service ID for the addon only order | Optional |
| addonids | int[] | An Array of addon ids for an Addon Only Order | Optional |
| serviceids | int[] | An array of service ids to associate the addons for an Addon Only order | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| orderid | int | The Order ID for the created order |
| productids | string | The Product/Service ID(s) created by the order |
| addonids | string | The Addon ID(s) created by the order |
| domainids | string | The Domain ID(s) created by the order |
| invoiceid | int | The Invoice ID created for the order |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'AddOrder',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'clientid' => '1',
            'pid[0]' => '1',
            'domain[0]' => 'domain1.com',
            'billingcycle[0]' => 'monthly',
            'addons[0]' => '1,3,9',
            'customfields[0]' => base64_encode(serialize(array(1 => 'Google'))),
            'configoptions[0]' => base64_encode(serialize(array(1 => 999))),
            'domaintype[0]' => 'register',
            'regperiod[0]' => '1',
            'domain[1]' => 'domain2.com',
            'domaintype[1]' => 'register',
            'regperiod[1]' => '1',
            'dnsmanagement[1]' => true,
            'nameserver1' => 'ns1.demo.com',
            'nameserver2' => 'ns2.demo.com',
            'addonid' => '1',
            'serviceid' => '1',
            'addonids[0]' => '3',
            'serviceids[0]' => '1',
            'addonids[1]' => '9',
            'serviceids[1]' => '1',
            'domainrenewals[domain3.com]' => '1',
            'domainrenewals[domain4.com]' => '2',
            'paymentmethod' => 'mailin',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'AddOrder';
$postData = array(
    'clientid' => '1',
    'pid[0]' => '1',
    'domain[0]' => 'domain1.com',
    'billingcycle[0]' => 'monthly',
    'addons[0]' => '1,3,9',
    'customfields[0]' => base64_encode(serialize(array(1 => 'Google'))),
    'configoptions[0]' => base64_encode(serialize(array(1 => 999))),
    'domaintype[0]' => 'register',
    'regperiod[0]' => '1',
    'domain[1]' => 'domain2.com',
    'domaintype[1]' => 'register',
    'regperiod[1]' => '1',
    'dnsmanagement[1]' => true,
    'nameserver1' => 'ns1.demo.com',
    'nameserver2' => 'ns2.demo.com',
    'addonid' => '1',
    'serviceid' => '1',
    'addonids[0]' => '3',
    'serviceids[0]' => '1',
    'addonids[1]' => '9',
    'serviceids[1]' => '1',
    'domainrenewals[domain3.com]' => '1',
    'domainrenewals[domain4.com]' => '2',
    'paymentmethod' => 'mailin',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "orderid": "1",
    "productids": "2",
    "addonids": "1,2,3,4,5,6",
    "domainids": "3,4",
    "invoiceid": "1"
}
```


### Error Responses

Possible error condition responses include:

* Client ID Not Found
* Unable to add order when client status is Closed
* Invalid Payment Method. Valid options include
* Addon ID invalid
* Service ID not owned by Client ID provided
* Domain status is set to 'Pending|Cancelled|Pending Transfer|Transferred|Fraud' and cannot be renewed
* Domain not owned by Client ID provided
* No items added to cart so order cannot proceed


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
