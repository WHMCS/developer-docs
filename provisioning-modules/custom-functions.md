+++
prev = "/provisioning-modules/usage-update"
next = "/provisioning-modules/client-area-output"
title = "Custom Functions"
toc = true
weight = 70

+++

Custom functions allow definition of extra operations that run using the module.
The custom functions can perform actions, or define extra client area pages/output.
Permissions can be granted for who can use each custom function, be it just clients, just admins, or both.

The convention for custom function names follow the same as any other function of a module.
It must begin with the module **filename_**, and then the custom function name.

The easiest way to show this is with an example.

## Example Custom Function <a id="example-function"></a>

Let’s take an example of a reboot & shutdown function in a VM/VPS system.

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

The above shows how to define custom functions and to used the passed variables.
The custom function returns either “success” or an error message to show a failure.
If we wanted to allow clients to perform reboots, but only admins to be able to perform a shutdown, that would be defined like:

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

The above allows a clients to run the “reboot” function, and admins “reboot” and “shutdown”.

The key value of the array is what displays to admins/clients on the button or menu options for the commands.
And the value is the custom function name excluding the **modulename_** prefix.

A description of how to provide a button or way to invoke a custom function is in the Client Area Output section:

```
<form method="post" action="clientarea.php?action=productdetails">
<input type="hidden" name="id" value="{$serviceid}" />
<input type="hidden" name="modop" value="custom" />
<input type="hidden" name="a" value="reboot" />
<input type="submit" value="Reboot VPS Server" />
</form>
```
