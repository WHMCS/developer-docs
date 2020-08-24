+++
prev = "/provisioning-modules/single-sign-on"
next = "/provisioning-modules/usage-metrics"
title = "Usage Update"
toc = true
weight = 60

+++

The UsageUpdate function performs a daily import of the disk and bandwidth usage for accounts of a server.
The data imported is then used to display the usage stats both within the client and admin areas of WHMCS.
The data is also used in disk and bandwidth overage billing calculations if enabled for a product.

The UsageUpdate function runs via WHMCS Cron, for any active, enabled server.

`Important: Runs per server not per product`

This can only run if your module has a server created in WHMCS for it - products alone do not invoke it.

The function receives the id, ip, hostname, username/hash, & password variables.
The function will query the disk and bandwidth usage for the server, and updates the database.
The database update should be a single call for speed and efficiency.

## Example Usage Update Function <a id="example-function"></a>

```
function mymodule_UsageUpdate($params) {

    $serverid = $params['serverid'];
    $serverhostname = $params['serverhostname'];
    $serverip = $params['serverip'];
    $serverusername = $params['serverusername'];
    $serverpassword = $params['serverpassword'];
    $serveraccesshash = $params['serveraccesshash'];
    $serversecure = $params['serversecure'];

    // Run connection to retrieve usage for all domains/accounts on $serverid

    // Now loop through results and update DB

    foreach ($results AS $domain => $values) {
        try {
            \WHMCS\Database\Capsule::table('tblhosting')
                ->where('server', $serverid)
                ->where('domain', $values['domain'])
                ->update([
                    'diskusage' => $values['diskusage'],
                    'disklimit' => $values['disklimit'],
                    'bwusage' => $values['bandwidth'],
                    'bwlimit' => $values['bwlimit'],
                    'lastupdate' => Capsule::raw('now()'),
                ]);
        } catch (\Exception $e) {
            // Handle any error which may occur
        } 
    }

}
```
