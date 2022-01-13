+++
prev = "/provisioning-modules/usage-metrics"
next = "/provisioning-modules/client-area-output"
title = "Custom Functions"
toc = true
weight = 70

+++

Custom functions allow you to define operations that run using the module.
The custom functions can perform actions or define additional Client Area pages or output.
Permissions can be granted for who can use each custom function (just clients, just admins, or both).

The convention for custom function names is the same as any other module function.
It must begin with the module filename (`filename_`) and the custom function name.

## Example Custom Function <a id="example-function"></a>

Consider the following example of a reboot and shutdown function in a VM or VPS system:

```
function mymodule_reboot($params) {

	# Code to perform reboot action goes here...

    if ($successful) {
		$result = "success";
	} else {
		$result = "Error Message Goes Here...";
	}
	return $result;

}

function mymodule_shutdown($params) {

	# Code to perform shutdown action goes here...

    if ($successful) {
		$result = "success";
	} else {
		$result = "Error Message Goes Here...";
	}
	return $result;

}
```

The above example defines a custom function and uses the passed variables.
The custom function returns either `success` or an error message to indicate failure.

The following example allows clients to perform reboots but only allows admins to perform a reboot or shutdown:

```
function mymodule_ClientAreaCustomButtonArray() {
    $buttonarray = array(
	 "Reboot Server" => "reboot",
	);
	return $buttonarray;
}

function mymodule_AdminCustomButtonArray() {
    $buttonarray = array(
	 "Reboot Server" => "reboot",
	 "Shutdown Server" => "shutdown",
	);
	return $buttonarray;
}
```

The key value of the array is what displays to admins and clients on the button or menu options for the commands.
The value is the custom function name without the `modulename_` prefix.

A description of how to provide a button or way to invoke a custom function is in the Client Area Output section:

```
<form method="post" action="clientarea.php?action=productdetails">
<input type="hidden" name="id" value="{$serviceid}" />
<input type="hidden" name="modop" value="custom" />
<input type="hidden" name="a" value="reboot" />
<input type="submit" value="Reboot VPS Server" />
</form>
```
