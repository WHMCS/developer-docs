+++
next = "/addon-modules/admin-dashboard-widgets"
prev = "/addon-modules/multi-language"
title = "Hooks"
toc = true
weight = 70

+++

Hooks that the module should define within WHMCS are defined in a file named “hooks.php”.
This should be within your custom module folder.
That will then become detected and any hooks that exist will be loaded on every page of WHMCS.

Module settings are not passed to hook functions. If you require access to the module's settings, they will need to be retrieved from the database. Add this to the top of your hooks.php file under the opening PHP tag: 

```use Illuminate\Database\Capsule\Manager as Capsule;```

Then include the following function and use it to obtain an individual setting:

```
/**
 * Returns:
 * - Associative array containing settings if no settingname provided
 * - value of type stored in DB if settingname is provided 
 */
function getSettings($modulename, $settingname = null){
	
	if ($settingname === null){
		return (array) Capsule::table('tbladdonmodules')->where('module', $modulename)->get();
	}
	else{
		return Capsule::table('tbladdonmodules')->where( array(
				'module' => $modulename, 
				'setting' => $settingname,
			) )->value('value');
	}
		
}
```

The hook functions within that file should be defined in exactly the same way as normal.

Please refer to [Hook Documentation][hook-documentation] for more info on creating and working with hooks in WHMCS.

[hook-documentation]: http://docs.whmcs.com/Hooks "Hooks"
