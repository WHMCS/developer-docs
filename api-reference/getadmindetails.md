+++
title = "GetAdminDetails"
toc = true
+++

Obtain the details for the current Admin User

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetAdminDetails" | Required |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| adminid | int | The current admin ID. |
| name | string | The full name of the admin user. |
| notes | string | The current notes for the admin user. |
| signature | string | The support ticket signature. |
| allowedpermissions | string | A comma-separated list of all of the permissions available for the admin user. |
| departments | string | A comma-separated list of all support departments the admin user belongs to. |
| requesttime | string | The date and time of the request. |
| whmcs | array | The version details of the current WHMCS installation |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetAdminDetails',
            // See https://developers.whmcs.com/api/authentication
            'username' => 'IDENTIFIER_OR_ADMIN_USERNAME',
            'password' => 'SECRET_OR_HASHED_PASSWORD',
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
$command = 'GetAdminDetails';
$postData = array(
);
$adminUsername = 'ADMIN_USERNAME'; // Optional for WHMCS 7.2 and later

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "adminid": "1",
    "name": "Site Admin",
    "notes": "Welcome to WHMCS!  Please ensure you have setup the cron job to automate tasks",
    "signature": "",
    "allowedpermissions": "Main Homepage,My Account,List Clients,List Services,List Addons,List Domains,Add New Client,Edit Clients Details,Manage Pay Methods,View Clients Products\/Services,Edit Clients Products\/Services,Delete Clients Products\/Services,Perform Server Operations,View Clients Domains,Edit Clients Domains,Delete Clients Domains,View Clients Notes,Add\/Edit Client Notes,Delete Client,Mass Mail,View Cancellation Requests,Manage Affiliates,View Orders,Delete Order,View Order Details,Add New Order,List Transactions,Add Transaction,Edit Transaction,Delete Transaction,View Gateway Log,List Invoices,Create Invoice,Manage Invoice,Delete Invoice,Offline Credit Card Processing,Support Center Overview,Manage Announcements,Manage Knowledgebase,Manage Downloads,List Support Tickets,Open New Ticket,Manage Predefined Replies,View Reports,Addon Modules,Link Tracking,Calendar,To-Do List,WHOIS Lookups,Domain Resolver Checker,View Integration Code,WHM Import Script,Database Status,System Cleanup Operations,View PHP Info,View Activity Log,View Admin Log,View Email Message Log,View Ticket Mail Import Log,View WHOIS Lookup Log,Configure General Settings,Configure Administrators,Configure Admin Roles,Configure Servers,Configure Automation Settings,Configure Payment Gateways,Tax Configuration,View Email Templates,View Products\/Services,Configure Product Addons,View Promotions,Configure Domain Pricing,Configure Support Departments,Configure Spam Control,Configure Banned Emails,Configure Domain Registrars,Configure Fraud Protection,Configure Custom Client Fields,API Access,View Flagged Tickets,Configure Database Backups,Manage Network Issues,Manage Quotes,Configure Currencies,Configure Security Questions,Client Data Export,Mass Data Export,View Billable Items,Manage Billable Items,Configure Client Groups,Refund Invoice Payments,Delete Ticket,View Income Totals,Manage Clients Files,Configure Ticket Statuses,Delete Client Notes,Perform Registrar Operations,Create Upgrade\/Downgrade Orders,Configure Addon Modules,Email Marketer,Configure Product Bundles,View Module Debug Log,View Clients Summary,View Support Ticket,Decrypt Full Credit Card Number,Update\/Delete Stored Credit Card,Create\/Edit Promotions,Delete Promotions,View Banned IPs,Add Banned IP,Unban Banned IP,Create\/Edit Email Templates,Delete Email Templates,Manage Email Template Languages,Create New Products\/Services,Edit Products\/Services,Delete Products\/Services,Manage Product Groups,Allow Login as Owner,Configure Order Statuses,Attempts CC Captures,Generate Due Invoices,Create Predefined Replies,Create Predefined Replies,Delete Predefined Replies,Delete Predefined Replies,Configure Two-Factor Authentication,View Credit Log,Manage Credits,WHMCSConnect,Health and Updates,Configure Application Links,Configure OpenID Connect,Update WHMCS,Modify Update Configuration",
    "departments": ",1,",
    "whmcs": {
        "version": "7.10.2",
        "canonicalversion": "7.10.2-release.1"
    }
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
