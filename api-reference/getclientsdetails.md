+++
title = "GetClientsDetails"
toc = true
+++

Obtain the Clients Details for a specific client

Note this function returns the client information in the top level array. This information
is deprecated and may be removed in a future version of WHMCS.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetClientsDetails" | Required |
| clientid | int | The client id to obtain the details for. $clientid or $email is required | Optional |
| email | string | The email address of the client to search for | Optional |
| stats | bool | Also return additional client statistics. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| client | array | The information on the client. |
| stats | array | Additional statistics for the client returned. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetClientsDetails',
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
$command = 'GetClientsDetails';
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
    "client[result]": "success",
    "client[userid]": "1",
    "client[id]": "1",
    "client[uuid]": "f08ea4d1-c578-441a-9b0a-aa3aff8b1acf",
    "client[firstname]": "Test",
    "client[lastname]": "Client",
    "client[fullname]": "Test Client",
    "client[companyname]": "",
    "client[email]": "test-client@example.com",
    "client[address1]": "123 Test Street",
    "client[address2]": "",
    "client[city]": "Test",
    "client[fullstate]": "Tester",
    "client[state]": "Tester",
    "client[postcode]": "TE5 5ST",
    "client[countrycode]": "GB",
    "client[country]": "GB",
    "client[phonenumber]": "01234567890",
    "client[password]": "$2y$10$17X1fBPpamALcMA9KMiFneH4FYpMkkmFGDxlkxbjGeSnfH8sLqixa",
    "client[statecode]": "Tester",
    "client[countryname]": "United Kingdom",
    "client[phonecc]": "44",
    "client[phonenumberformatted]": "+44.1234567890",
    "client[billingcid]": "0",
    "client[notes]": "",
    "client[twofaenabled]": "",
    "client[currency]": "1",
    "client[defaultgateway]": "",
    "client[cctype]": "",
    "client[cclastfour]": "",
    "client[securityqid]": "0",
    "client[securityqans]": "",
    "client[groupid]": "0",
    "client[status]": "Active",
    "client[credit]": "0.00",
    "client[taxexempt]": "",
    "client[latefeeoveride]": "",
    "client[overideduenotices]": "",
    "client[separateinvoices]": "",
    "client[disableautocc]": "",
    "client[emailoptout]": "",
    "client[marketing_emails_opt_in]": "",
    "client[overrideautoclose]": "",
    "client[allowSingleSignOn]": "1",
    "client[language]": "",
    "client[lastlogin]": "Date: 03\/10\/2016 10:26<br>IP Address:<br>Host:",
    "client[currency_code]": "USD",
    "stats[numdueinvoices]": "19",
    "stats[dueinvoicesbalance]": "$2645.80 USD",
    "stats[income]": "$0.00 USD",
    "stats[incredit]": "",
    "stats[creditbalance]": "$0.00 USD",
    "stats[numoverdueinvoices]": "19",
    "stats[overdueinvoicesbalance]": "$2645.80 USD",
    "stats[numDraftInvoices]": "0",
    "stats[draftInvoicesBalance]": "$0.00 USD",
    "stats[numpaidinvoices]": "0",
    "stats[paidinvoicesamount]": "$0.00 USD",
    "stats[numunpaidinvoices]": "19",
    "stats[unpaidinvoicesamount]": "$2645.80 USD",
    "stats[numcancelledinvoices]": "0",
    "stats[cancelledinvoicesamount]": "$0.00 USD",
    "stats[numrefundedinvoices]": "0",
    "stats[refundedinvoicesamount]": "$0.00 USD",
    "stats[numcollectionsinvoices]": "0",
    "stats[collectionsinvoicesamount]": "$0.00 USD",
    "stats[productsnumactivehosting]": "0",
    "stats[productsnumhosting]": "0",
    "stats[productsnumactivereseller]": "0",
    "stats[productsnumreseller]": "0",
    "stats[productsnumactiveservers]": "0",
    "stats[productsnumservers]": "0",
    "stats[productsnumactiveother]": "2",
    "stats[productsnumother]": "2",
    "stats[productsnumactive]": "2",
    "stats[productsnumtotal]": "2",
    "stats[numactivedomains]": "2",
    "stats[numdomains]": "2",
    "stats[numacceptedquotes]": "0",
    "stats[numquotes]": "0",
    "stats[numtickets]": "0",
    "stats[numactivetickets]": "0",
    "stats[numaffiliatesignups]": "0",
    "stats[isAffiliate]": ""
}
```


### Error Responses

Possible error condition responses include:

* Either clientid Or email Is Required
* Client Not Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
