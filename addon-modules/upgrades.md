+++
next = "/addon-modules/whmcs-marketplace"
prev = "/addon-modules/admin-dashboard-widgets"
title = "Upgrades"
toc = true
weight = 90

+++

Releasing updates and upgrades to custom modules is likely something that is needed to be done at some point.
If those modules need to modify the database structure or perform other functions that would be handled in the **_activate** function, then you need some way of handling that.

With the Addon Modules system, this is a breeze with the upgrade function.
The upgrade function is called the first time a module is accessed following an update.
The update is detected by a change of version number in the **_config** array of the module.
The upgrade function is passed the previous version number so that the module can then decide what updates to run within that function.
This allows the module to bring it up to date with your latest version.

## Example Upgrade Function <a id="example-function"></a>

An example of how this function can be used is demonstrated below:

```
function demo_upgrade($vars) {

    $version = $vars['version'];

    # Run SQL Updates for V1.0 to V1.1
    if ($version < 1.1) {
        $query = "ALTER `mod_addonexample` ADD `demo2` TEXT NOT NULL ";
    	$result = mysql_query($query);
    }

    # Run SQL Updates for V1.1 to V1.2
    if ($version < 1.2) {
        $query = "ALTER `mod_addonexample` ADD `demo3` TEXT NOT NULL ";
    	$result = mysql_query($query);
    }

}
```
