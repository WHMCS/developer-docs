+++
next = "/domain-registrars/module-parameters/"
prev = "/domain-registrars/function-index/"
title = "Domain Syncronisation"
weight = 40

+++

The domain syncronisation functions allow you to propogate any domain expiry date and status changes at the registry level to WHMCS.  This is particularly useful for domain transfers where completion of the transfer and expiry dates can not be known by WHMCS automatically without it.

## Domain Syncing

Domains are only checked when they are in Active or Pendin Transfer status. A domain will never transfer to Cancelled status if a domain is subsequently deleted. 

Expired is ultimately the last status a domain will reach on Expiry. WHMCS never sets the domain to cancelled after it is deleted from the registry.

Domain syncing is performed in batches. When defined in your module, the Sync function will be called for 50 domains on a rolling basis each time the domain sync cron is invoked. Once all domains assigned to your module have been synced it will start from the beginning again.

The below example shows the supported return values for the function.

```
function modulename_Sync($params) {

    /**
     * Available parameters include the following.
     * Any settings defined in your Config Options method will also be available.
     */

    $params['domainid'];
    $params['domain'];
    $params['sld'];
    $params['tld'];
    $params['registrar'];
    $params['regperiod'];
    $params['status'];
    $params['dnsmanagement'];
    $params['emailforwarding'];
    $params['idprotection'];

    // Perform code to fetch domain status here

    // Return your result.
    // If 'error' is returned, all other values will be ignored. It is important to ensure 'error' is not returned in this array
    // unless the sync should not be completed. The error message will be provided in the "Domain Synchronisation Report" email.
    
    return array(
        'active' => true, // Return true if the domain is active
        'cancelled' => false, // Return true if the domain has been cancelled 
        'transferredAway' => false, // Return true if the domain has been transferred away from this registrar
        'expirydate' => '2018-09-28', // Return the current expiry date for the domain
        'error' => 'Error message goes here.' // The error message returned here will be returned within the Domain Synchronisation Report Email
    );
}
```

{{% notice tip %}}
Settings relating to domain syncing are in the **Setup > General Settings > Domains** area. There are 3 key settings:
* ***Domain Sync Enabled*** - Check to allow the domain sync cron to actually run.
* ***Sync Next Due Date*** - Enable this setting to update next due date to match the expiry field as part of the sync.
* ***Domain Sync Notify Only*** - Enable this to allow WHMCS to run the sync checks and report any inconsistencies. But, no changes to the domains will occur. With this enabled you receive an email report listing any discrepancies between the registrar and WHMCS.
{{% /notice %}}

## Transfer Syncing

Transfer syncing works in a similar way to domain syncing. When defined in your module, this function will be called for every domain in the Pending Transfer status when the domain sync cron runs.

The Transfer Sync method supports a number of return values.  A completed status indicator, the expiry date, a failed state, and a failure reason.  The below code example demonstrates the use of these.

```
function modulename_TransferSync($params) {

    /**
     * Available parameters include the following.
     * Any settings defined in your Config Options method will also be available.
     */

    $params['domainid'];
    $params['domain'];
    $params['sld'];
    $params['tld'];
    $params['registrar'];
    $params['regperiod'];
    $params['status'];
    $params['dnsmanagement'];
    $params['emailforwarding'];
    $params['idprotection'];

    // Perform code to fetch transfer status here

    return array(
        'completed' => true, // Return as true upon successful completion of the transfer
        'expirydate' => '2017-10-15', // The expiry date of the domain
        'failed' => false, // Return as true when transfer fails permenantly
        'reason' => 'Reason message can go here', // Reason for the transfer failure if available
        'error' => 'Error message goes here', // If the check fails, an error message string can be provided here
    );
}
```
