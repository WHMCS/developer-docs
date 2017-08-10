+++
next = "/addon-modules/admin-area-output"
prev = "/addon-modules/configuration"
title = "Installation & Uninstallation"
toc = true
weight = 30

+++

Modules can contain both activate and deactivate functions.
These functions run when an admin user activates or deactivates the module in the Addon Modules configuration area.

These functions can be used run any code required when activating or deactivating the module.
For example, to create custom tables, database entries, or perform license checks.
They can also be used to return messages, or errors to a user.
So, if you want to fail the process due to a problem, or want to notify the user of a missing requirement or license issue.

The deactivation function should undo everything that the activation function does to remove the module from the users system.

There will already be an active database connection when the module is run, so to access the WHMCS database you won’t need to reconnect to the database.

For example, the activate and deactivate functions could create and drop a table for use by the custom module as below:

## Example Activate Function <a id="example-activate-function"></a>

```
function demo_activate() {

    # Create Custom DB Table
    $query = "CREATE TABLE `mod_addonexample` (`id` INT( 1 ) NOT NULL AUTO_INCREMENT ... ";
	$result = full_query($query);

    # Return Result
    return array('status'=>'success','description'=>'This is an demo module only. In a real
           module you might instruct a user how to get started with it here...');
    return array('status'=>'error','description'=>'You can use the error status return to
           indicate there was a problem activating the module');
    return array('status'=>'info','description'=>'You can use the info status return to display
           a message to the user');

}
```

## Example Deactivate Function <a id="example-deactivate-function"></a>

```
function demo_deactivate() {

    # Remove Custom DB Table
    $query = "DROP TABLE `mod_addonexample`";
	$result = full_query($query);

    # Return Result
    return array('status'=>'success','description'=>'If successful, you can return a message
           to show the user here');
    return array('status'=>'error','description'=>'If an error occurs you can return an error
           message for display here');
    return array('status'=>'info','description'=>'If you want to give an info message to a user
           you can return it here');

}
```
