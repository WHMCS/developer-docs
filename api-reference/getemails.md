+++
title = "GetEmails"
toc = true
+++

Obtain a list of emails sent to a specific Client ID

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetEmails" | Required |
| clientid | int | The client ID to retrieve the emails for. | Required |
| limitstart | int | The offset for the returned log data (default: `0`). | Optional |
| limitnum | int | The number of records to return (default: `25`). | Optional |
| date | string | The date to retrieve emails for. Format: Y-m-d H:i:s | Optional |
| subject | string | The subject to retrieve emails for (uses approximate string matching). | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| totalresults | int | The total number of results available. |
| startnumber | int | The starting number for the returned results. |
| numreturned | int | The total number of results returned. |
| emails | array | The activity log entries returned. |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetEmails',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
            'clientid' => '1',
            'subject' => 'elcom',
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
$command = 'GetEmails';
$postData = array(
    'clientid' => '1',
    'subject' => 'elcom',
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
    "emails": {
        "email": [
            {
                "id": 16,
                "userid": 7,
                "subject": "Five great years with Hosting Company, Inc.!",
                "message": "<!DOCTYPE html PUBLIC \"-\/\/W3C\/\/DTD XHTML 1.0 Transitional\/\/EN\" \"http:\/\/www.w3.org\/TR\/xhtml1\/DTD\/xhtml1-transitional.dtd\">\n<html xmlns=\"http:\/\/www.w3.org\/1999\/xhtml\">\n    <head>\n        <meta http-equiv=\"Content-Type\" content=\"text\/html; charset=utf-8\" \/>\n        <meta name=\"viewport\" content=\"width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no\">\n        <style type=\"text\/css\">\n            .ExternalClass,.ExternalClass div,.ExternalClass font,.ExternalClass p,.ExternalClass span,.ExternalClass td,h1,img{line-height:100%}h1,h2{display:block;font-family:Helvetica;font-style:normal;font-weight:700}#outlook a{padding:0}.ExternalClass,.ReadMsgBody{width:100%}a,blockquote,body,li,p,table,td{-webkit-text-size-adjust:100%;-ms-text-size-adjust:100%}table,td{mso-table-lspace:0;mso-table-rspace:0}img{-ms-interpolation-mode:bicubic;border:0;height:auto;outline:0;text-decoration:none}table{border-collapse:collapse!important}#bodyCell,#bodyTable,body{height:100%!important;margin:0;padding:0;width:100%!important}#bodyCell{padding:20px;}#templateContainer{width:600px;border:1px solid #ddd;background-color:#fff}#bodyTable,body{background-color:#FAFAFA}h1{color:#202020!important;font-size:26px;letter-spacing:normal;text-align:left;margin:0 0 10px}h2{color:#404040!important;font-size:20px;line-height:100%;letter-spacing:normal;text-align:left;margin:0 0 10px}h3,h4{display:block;font-style:italic;font-weight:400;letter-spacing:normal;text-align:left;margin:0 0 10px;font-family:Helvetica;line-height:100%}h3{color:#606060!important;font-size:16px}h4{color:grey!important;font-size:14px}.headerContent{background-color:#f8f8f8;border-bottom:1px solid #ddd;color:#505050;font-family:Helvetica;font-size:20px;font-weight:700;line-height:100%;text-align:left;vertical-align:middle;padding:0}.bodyContent,.footerContent{font-family:Helvetica;line-height:150%;text-align:left;}.footerContent{text-align:center}.bodyContent pre{padding:15px;background-color:#444;color:#f8f8f8;border:0}.bodyContent pre code{white-space:pre;word-break:normal;word-wrap:normal}.bodyContent table{margin:10px 0;background-color:#fff;border:1px solid #ddd}.bodyContent table th{padding:4px 10px;background-color:#f8f8f8;border:1px solid #ddd;font-weight:700;text-align:center}.bodyContent table td{padding:3px 8px;border:1px solid #ddd}.table-responsive{border:0}.bodyContent a{word-break:break-all}.headerContent a .yshortcuts,.headerContent a:link,.headerContent a:visited{color:#1f5d8c;font-weight:400;text-decoration:underline}#headerImage{height:auto;max-width:600px;padding:20px}#templateBody{background-color:#fff}.bodyContent{color:#505050;font-size:14px;padding:20px}.bodyContent a .yshortcuts,.bodyContent a:link,.bodyContent a:visited{color:#1f5d8c;font-weight:400;text-decoration:underline}.bodyContent a:hover{text-decoration:none}.bodyContent img{display:inline;height:auto;max-width:560px}.footerContent{color:grey;font-size:12px;padding:20px}.footerContent a .yshortcuts,.footerContent a span,.footerContent a:link,.footerContent a:visited{color:#606060;font-weight:400;text-decoration:underline}@media only screen and (max-width:640px){h1,h2,h3,h4{line-height:100%!important}#templateContainer{max-width:600px!important;width:100%!important}#templateContainer,body{width:100%!important}a,blockquote,body,li,p,table,td{-webkit-text-size-adjust:none!important}body{min-width:100%!important}#bodyCell{padding:10px!important}h1{font-size:24px!important}h2{font-size:20px!important}h3{font-size:18px!important}h4{font-size:16px!important}#templatePreheader{display:none!important}.headerContent{font-size:20px!important;line-height:125%!important}.footerContent{font-size:14px!important;line-height:115%!important}.footerContent a{display:block!important}.hide-mobile{display:none;}}\n        <\/style>\n    <\/head>\n    <body leftmargin=\"0\" marginwidth=\"0\" topmargin=\"0\" marginheight=\"0\" offset=\"0\">\n        <center>\n            <table align=\"center\" border=\"0\" cellpadding=\"0\" cellspacing=\"0\" height=\"100%\" width=\"100%\" id=\"bodyTable\">\n                <tr>\n                    <td align=\"center\" valign=\"top\" id=\"bodyCell\">\n                        <table border=\"0\" cellpadding=\"0\" cellspacing=\"0\" id=\"templateContainer\">\n                            <tr>\n                                <td align=\"center\" valign=\"top\">\n                                    <table border=\"0\" cellpadding=\"0\" cellspacing=\"0\" width=\"100%\" id=\"templateHeader\">\n                                        <tr>\n                                            <td valign=\"top\" class=\"headerContent\">\n                                                <a href=\"http:\/\/example.com\">\n                                                    <img src=\"http:\/\/example.com\/whmcs\/assets\/img\/logo.png\" style=\"max-width:600px;padding:20px 20px 0 20px\" id=\"headerImage\" alt=\"Hosting Company, L.L.C.\" \/>\n                                            <\/td>\n                                        <\/tr>\n                                    <\/table>\n                                <\/td>\n                            <\/tr>\n                            <tr>\n                                <td align=\"center\" valign=\"top\">\n                                    <table border=\"0\" cellpadding=\"0\" cellspacing=\"0\" width=\"100%\" id=\"templateBody\">\n                                        <tr>\n                                            <td valign=\"top\" class=\"bodyContent\">\n<!-- message header end -->            Thanks for being a valued customer for five years. As a reward for your loyalty, you will receive a 25% off code soon!<!-- message footer start -->\n<\/td>\n                                        <\/tr>\n                                    <\/table>\n                                <\/td>\n                            <\/tr>\n                            <tr>\n                                <td align=\"center\" valign=\"top\">\n                                    <table border=\"0\" cellpadding=\"0\" cellspacing=\"0\" width=\"100%\" id=\"templateFooter\">\n                                        <tr>\n                                            <td valign=\"top\" class=\"footerContent\">\n                                                 <a href=\"http:\/\/example.com\">visit our website<\/a>\n                                                <span class=\"hide-mobile\"> | <\/span>\n                                                <a href=\"http:\/\/example.com\/whmcs\/\">log in to your account<\/a>\n                                                <span class=\"hide-mobile\"> | <\/span>\n                                                <a href=\"http:\/\/example.com\/whmcs\/submitticket.php\">get support<\/a> <br \/>\n                                                Copyright \u00a9 Hosting Company, L.L.C., All rights reserved.\n                                            <\/td>\n                                        <\/tr>\n                                    <\/table>\n                                <\/td>\n                            <\/tr>\n                        <\/table>\n                    <\/td>\n                <\/tr>\n            <\/table>\n        <\/center>\n    <\/body>\n<\/html>",
                "date": "2020-06-24 10:42:40",
                "to": "Kalei Kahale (Kahale Web Design) <kahale@example.com>",
                "cc": "",
                "bcc": "",
                "attachments": null,
                "pending": 0,
                "message_data": null,
                "failed": 0,
                "failure_reason": "",
                "retry_count": 0,
                "created_at": null,
                "updated_at": null,
                "campaign_id": 0
            }
        ]
    }
}
```


### Error Responses

Possible error condition responses include:

* Client ID Not Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
