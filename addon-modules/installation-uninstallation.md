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
function addonmodule_activate()
{
    // Create custom tables and schema required by your module
    try {
        Capsule::schema()
            ->create(
                'mod_addonexample',
                function ($table) {
                    /** @var \Illuminate\Database\Schema\Blueprint $table */
                    $table->increments('id');
                    $table->text('demo');
                }
            );
        return [
            // Supported values here include: success, error or info
            'status' => 'success',
            'description' => 'This is a demo module only. '
                . 'In a real module you might report a success or instruct a '
                    . 'user how to get started with it here.',
        ];
    } catch (\Exception $e) {
        return [
            // Supported values here include: success, error or info
            'status' => "error",
            'description' => 'Unable to create mod_addonexample: ' . $e->getMessage(),
        ];
    }
}
```

## Example Deactivate Function <a id="example-deactivate-function"></a>

```
function addonmodule_deactivate()
{
    // Undo any database and schema modifications made by your module here
    try {
        Capsule::schema()
            ->dropIfExists('mod_addonexample');
        return [
            // Supported values here include: success, error or info
            'status' => 'success',
            'description' => 'This is a demo module only. '
                . 'In a real module you might report a success here.',
        ];
    } catch (\Exception $e) {
        return [
            // Supported values here include: success, error or info
            "status" => "error",
            "description" => "Unable to drop mod_addonexample: {$e->getMessage()}",
        ];
    }
}
```
