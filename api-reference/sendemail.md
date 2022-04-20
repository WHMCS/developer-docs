+++
title = "SendEmail"
toc = true
+++

Send a client Email Notification.

The following email templates cannot be sent in this way:

* Order Confirmation
* Password Reset Confirmation
* Password Reset Validation
* Quote Accepted
* Quote Accepted Notification
* Quote Delivery with PDF
* Clients Only Bounce Message
* Replies Only Bounce Message
* Affiliate Monthly Referrals Report

What you must provide for the Related ID depends upon the type of email being sent.
The available options are:

* General Email Type = Client ID (tblclients.id)
* Product Email Type = Service ID (tblhosting.id)
* Domain Email Type = Domain ID (tbldomains.id)
* Invoice Email Type = Invoice ID (tblinvoices.id)
* Support Email Type = Ticket ID (tbltickets.id)
* Affiliate Email Type = Affiliate ID (tblaffiliates.id)

**Sending Failed**

The generic Sending Failed error response can be caused by one of five possible conditions. They are:

* Invalid related ID
* Email template contains no body content after processing (typically a Smarty error)
* Welcome email requested for product which has none set
* Hook aborted the sending
* PHPMailer Sending Error - in this failure condition, an activity log entry will be created recording the error message that occurred

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "SendEmail" | Required |
| messagename | string | The name of the client email template to send | Optional |
| id | int | The related id for the type of email template. Eg this should be the client id for a general type email | Optional |
| customtype | string | The type of custom email template to send ('general', 'product', 'domain', 'invoice', 'support', 'affiliate') | Optional |
| custommessage | string | The HTML message body to send for a custom email | Optional |
| customsubject | string | The subject to send for a custom email | Optional |
| customvars | array | The custom variables to provide to the email template. Can be used for existing and custom emails. | Optional |

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
            'action' => 'SendEmail',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            '//example1' => 'example',
            'messagename' => 'Client Signup Email',
            'id' => '1',
            '//example2' => 'example',
            'customtype' => 'product',
            'customsubject' => 'Product Welcome Email',
            'custommessage' => '<p>Thank you for choosing us</p><p>Your custom is appreciated</p><p>{$custommerge}<br />{$custommerge2}</p>',
            'customvars' => base64_encode(serialize(array("custommerge"=>$populatedvar1, "custommerge2"=>$populatedvar2))),
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
$command = 'SendEmail';
$postData = array(
    '//example1' => 'example',
    'messagename' => 'Client Signup Email',
    'id' => '1',
    '//example2' => 'example',
    'customtype' => 'product',
    'customsubject' => 'Product Welcome Email',
    'custommessage' => '<p>Thank you for choosing us</p><p>Your custom is appreciated</p><p>{$custommerge}<br />{$custommerge2}</p>',
    'customvars' => base64_encode(serialize(array("custommerge"=>$populatedvar1, "custommerge2"=>$populatedvar2))),
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

* You must provide either an existing email template name or a custom message type
* Invalid message type provided
* A subject is required for a custom message
* A message body is required for a custom message
* The custom variables you provided are invalid.
* A related ID is required
* Email Template not found
* Email Template is disabled
* Sending Failed. Please see documentation.


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
