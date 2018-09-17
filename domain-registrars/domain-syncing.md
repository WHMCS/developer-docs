+++
next = "/domain-registrars/module-parameters/"
prev = "/domain-registrars/function-index/"
title = "Domain Syncronisation"
weight = 40

+++

The domain syncronisation functions allow you to propogate any domain expiry date and status changes at the registry level to WHMCS.  This is particularly useful for domain transfers where completion of the transfer and expiry dates can not be known by WHMCS automatically without it.

## Domain Syncing

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

    //If the Sync is successful, return the following:
    return array(
        'active' => true, // Return true if the domain is active
        'expired' => false, // Return true if the domain has expired
        'expirydate' => '2016-11-01', // Return the current expiry date for the domain
    );
    
    //If the Sync is unsuccessful (e.g. a server timeout), return an error to block any changes
    return array(
        'error' => "Could not connect to modulename.", // Return an error message as a string
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
