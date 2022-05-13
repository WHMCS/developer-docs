+++
prev = "/provisioning-modules/module-logging"
next = "/provisioning-modules/custom-actions"
title = "Server Sync"
toc = true
weight = 120
+++

{{% notice info %}}As of WHMCS 7.8, modules can implement the List Accounts functionality to offer sync functionality to administrative users ([Server Sync Tool](https://docs.whmcs.com/Server_Sync_Tool)).{{% /notice %}}
Implementing this functionality into a provisioning module enables WHMCS to compare a list of accounts returned by a remote system against service records stored within WHMCS, and provides admin users with the ability to perform import and sync operations.

## Server Sync Tool <a id="product-details-output"></a>

To allow WHMCS to import accounts from a remote system, meta data fields, and a new function must be included in the module files.
 
```
use WHMCS\Service\Status;

...

function mymodule_MetaData()
{
 return array(
     // The display name of the unique identifier to be displayed on the table output
     'ListAccountsUniqueIdentifierDisplayName' => 'Domain',
     // The field in the return that matches the unique identifier
     'ListAccountsUniqueIdentifierField' => 'domain',
     // The config option indexed field from the _ConfigOptions function that identifies the product on the remote system
     'ListAccountsProductField' => 'configoption1',
 );
}
 
function mymodule_ListAccounts(array $params)
{
    $accounts = [];
    try {
        // Call the remote api to obtain the list of accounts. Use the values provided by
        // WHMCS in `$params`. (https://developers.whmcs.com/provisioning-modules/module-parameters/)
        //$data = mymodule_call($params, 'listaccounts');
        
        foreach ($data as $account) {
            $accounts[] = [
                // The remote accounts email address
                'email' => 'john@example.net', 
                // The remote accounts username
                'username' => 'john', 
                // The remote accounts primary domain name
                'domain' => 'example.net', 
                // This can be one of the above fields or something different.
                // In this example, the unique identifier is the domain name
                'uniqueIdentifier' => 'example.net', 
                // The accounts package on the remote server
                'product' => 'Basic', 
                // The remote accounts primary IP Address
                'primaryip' => '1.2.3.4', 
                // The remote accounts creation date (Format: Y-m-d H:i:s)
                'created' => '2019-07-02 13:15:00', 
                // The remote accounts status (Status::ACTIVE or Status::SUSPENDED)
                'status' => Status::ACTIVE, 
            ];
        }
        // When returning the accounts, ensure that you return a success as a boolean
        // and accounts as an array.
        return [
            'success'  => true, // Boolean value
            'accounts' => $accounts,
        ];
    } catch (Exception $e) {
        return [
            'success'  => false, // Boolean value
            'error' => $e->getMessage(),
        ];
    }
}
```

## Parameters <a id="meta-data"></a>

A list of [Module Parameters][module-parameters] passed to this function can be found [here][module-parameters].

WHMCS expects the following parameters returned for each account:

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| email | string | The remote accounts email address. |
| username | string | The remote accounts username. |
| domain | string | The remote accounts primary domain name. |
| uniqueIdentifier | string | If one is not provided by the remote server, we recommend setting this to the domain name. |
| product | string | The accounts package on the remote server. |
| primaryip | string | The remote accounts primary IP Address. |
| created | string | The remote accounts creation date. (Format: Y-m-d H:i:s) |
| status | string | The remote accounts status. (WHMCS\Service\Status::ACTIVE or WHMCS\Service\Status::SUSPENDED) |

[module-parameters]: /provisioning-modules/module-parameters "Module Parameters"
