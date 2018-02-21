+++
title = "GetEmailTemplates"
toc = true
+++

Obtain a list of email templates from the system

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetEmailTemplates" | Required |
| type | string | The type of email template to retrieve | Optional |
| language | string | The language of the email template to retrieve, if none provided will return default language templates. | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results returned |
| emailtemplates | array | The email templates entries returned |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetEmailTemplates',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'type' => 'general',
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
$command = 'GetEmailTemplates';
$postData = array(
    'type' => 'general',
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "totalresults": "2",
    "emailtemplates[emailtemplate][0][id]": "38",
    "emailtemplates[emailtemplate][0][name]": "Automated Password Reset",
    "emailtemplates[emailtemplate][0][subject]": "Your new password for {$company_name}",
    "emailtemplates[emailtemplate][0][custom]": "0",
    "emailtemplates[emailtemplate][1][id]": "64",
    "emailtemplates[emailtemplate][1][name]": "Client Email Address Verification",
    "emailtemplates[emailtemplate][1][subject]": "Confirm Your Registration",
    "emailtemplates[emailtemplate][1][custom]": "0"
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
