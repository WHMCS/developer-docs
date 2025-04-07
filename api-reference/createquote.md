+++
title = "CreateQuote"
toc = true
+++

Creates a new quote

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "CreateQuote" | Required |
| subject | string | The subject of the new quote | Required |
| stage | string | The current stage of the quote ('Draft','Delivered','On Hold','Accepted','Lost','Dead') | Required |
| validuntil | string | The date the quote is valid until in localised format (eg DD/MM/YYYY) | Required |
| datecreated | string | The date the quote was created in localised format (eg DD/MM/YYYY) | Optional |
| lineitems | array | A base64 encoded serialized array containing the following keys: | Optional |
| lineitems[x][desc] | string | For $lineitems. The description of the line item | Optional |
| lineitems[x][qty] | int | For $lineitems. The quantity of the line item being quoted for | Optional |
| lineitems[x][up] | float | For $lineitems. The Unit Price of the line item | Optional |
| lineitems[x][discount] | float | For $lineitems. The amount of discount to provide on the line items | Optional |
| lineitems[x][taxable] | bool | For $lineitems. Is the line item taxable | Optional |
| userid | int | If the quote is for an existing client, the client ID the quote is for | Optional |
| firstname | string | The first name of the client the quote is for if no $userid | Optional |
| lastname | string | The last name of the client the quote is for if no $userid | Optional |
| companyname | string | The company of the client the quote is for if no $userid | Optional |
| email | string | The email address of the client the quote is for if no $userid | Optional |
| address1 | string | The address1 of the client the quote is for if no $userid | Optional |
| address2 | string | The address2 of the client the quote is for if no $userid | Optional |
| city | string | The city of the client the quote is for if no $userid | Optional |
| state | string | The state of the client the quote is for if no $userid | Optional |
| postcode | string | The post code of the client the quote is for if no $userid | Optional |
| country | string | The country of the client the quote is for if no $userid | Optional |
| phonenumber | string | The phone number of the client (no country code) the quote is for if no $userid. Local format eg 4035551234 | Optional |
| tax_id | string | The tax id of the client | Optional |
| currency | int | The id of the currency for the quote is for if no $userid | Optional |
| proposal | string | The proposal text displayed to the end user | Optional |
| customernotes | string | The notes on the quote displayed to the end user | Optional |
| adminnotes | string | The notes on the quote displayed to the staff only | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| quoteid | int | The id of the newly created quote |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'CreateQuote',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'subject' => 'Test Quote Subject',
            'stage' => 'Draft',
            'userid' => '1',
            'validuntil' => '01/01/2016',
            'lineitems' => base64_encode(serialize(array(array("desc"=>"Test Description 1","qty"=>1,"up"=>"10.00","discount"=>"10.00","taxable"=>true),array("desc"=>"Test Description 2","qty"=>4,"up"=>"15.00","discount"=>"0.00","taxable"=>false)))),
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
$command = 'CreateQuote';
$postData = array(
    'subject' => 'Test Quote Subject',
    'stage' => 'Draft',
    'userid' => '1',
    'validuntil' => '01/01/2016',
    'lineitems' => base64_encode(serialize(array(array("desc"=>"Test Description 1","qty"=>1,"up"=>"10.00","discount"=>"10.00","taxable"=>true),array("desc"=>"Test Description 2","qty"=>4,"up"=>"15.00","discount"=>"0.00","taxable"=>false)))),
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "quoteid": "1"
}
```


### Error Responses

Possible error condition responses include:

* Subject is required
* Invalid Stage
* Valid Until is required


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
| 7.7 | Added `tax_id` parameter. |
