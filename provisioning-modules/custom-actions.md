+++
prev = "/provisioning-modules/server-sync"
next = ""
title = "Custom Actions"
toc = true
weight = 130
+++

{{% notice info %}}
We added this functionality in WHMCS 8.5.
{{% /notice %}}

Custom actions allow you to define a list of items that perform a function and redirect the user to a specified URL. You can limit access to a custom action based on the user-level `productsso` permission.

Clients can perform actions from within the Client Area. When a client does this, it invokes the defined function. After the function completes and returns the structured response, a browser window will open to the location in that response.

Currently, you can use this to add buttons to the **Active Products/Services** panel on the Client Area homepage and add items to the **Actions** sidebar menu.

## CustomActions Function

The `CustomActions` function is responsible for returning the `WHMCS\Module\Server\CustomActionCollection` object.

This object is a collection of `WHMCS\Module\Server\CustomAction` objects that represent each individual item to display in the Client Area.

For more information on both the `CustomActionCollection` and `CustomAction` classes, see the `WHMCS\Module\Server` namespace at https://classdocs.whmcs.com/.

The following example creates a simple `CustomActions` function that returns a `CustomActionCollection` object.

```
<?php

use WHMCS\Module\Server\CustomAction;
use WHMCS\Module\Server\CustomActionCollection;

/**
 * Define a collection of Custom Action items to be displayed in the Client Area.
 *
 * Called when rendering Custom Action items in the Client Area; currently
 * limited to the "Active Products/Services" Client Area homepage panel.
 *
 * Use to provide authenticated Client Area users with the ability to perform a predefined
 * action at the click of a button. The action can be provided either in the form of a custom
 * module function or an anonymous function. For example, this can be used to provide a
 * Single Sign On button.
 *
 * @param array $params Common module parameters
 *
 * @see https://developers.whmcs.com/provisioning-modules/module-parameters/
 *
 * @return CustomActionCollection
 */
function provisioningmodule_CustomActions(array $params): CustomActionCollection
{
    // Instantiate a new CustomActionCollection to house the CustomAction objects.
    $customActionCollection = new CustomActionCollection();

    // Add a new CustomAction object to the collection.
    $customActionCollection->add(
        CustomAction::factory(
            'provisioningmodule',
            'Log in to Demo Provisioning Module',
            'provisioningmodule_ServiceSingleSignOn',
            [$params],
            ['productsso'],
            true
        )
    );

    // An anonymous function can be used in place of a custom module function.
    $customActionCollection->add(
        CustomAction::factory(
            'provisioningmodule',
            'Visit the WHMCS Website',
            function () {
                return [
                    'success' => true,
                    'redirectTo' => '//www.whmcs.com/',
                ];
            }
        )
    );

    // Return the CustomActionCollection to be used when checking for CustomAction items to render.
    return $customActionCollection;
}
```

## Callable Function

The `CustomAction` object expects you to provide a callable function upon creation. This is the logic that the system will execute when a customer interacts with the item in the Client Area.

The expected return for this function is an array that indicates success and provides either the redirect URL or an error message.

### Success Example
```
[
	'success' => true,
	'redirectTo' => 'https://whmcs.com/',
]
```

### Failure Example
```
[
	'success' => false,
	'errorMsg' => 'This is an error message.',
]
```
