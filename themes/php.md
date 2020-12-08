+++
prev = "/themes/conditionals/"
next = "/themes/testing/"
title = "PHP Logic"
toc = true
weight = 75

+++

# Using Hooks

We recommend that all custom PHP logic be performed via hooks. Hooks are the **only** future-proof way of performing your own PHP logic at the time of page rendering.

Historically, Smarty has allowed you to define custom PHP logic directly within system theme and order form template files. This has often been used by users and third party developers as a quick and convenient way of performing additional logic and defining additional system theme and order form template output.

However, as of Smarty 3, support for the {php} block has been removed, and we are only providing legacy support to ease the transition for developers and users who work with our platform and rely on this functionality.

{{% notice info %}}
The exposure of the template object via the legacy variable `$template`, available within the deprecated PHP blocks context, is only available if `template_object` is itemized in the `enabled_special_smarty_vars` array as described in our [Smarty Security Policy
](https://docs.whmcs.com/Smarty_Security_Policy#Supported_Policy_Settings_and_Values) documentation.
{{% /notice %}}

## Example

The below example demonstrates how a hook can be used to perform additional PHP logic and define system theme and order form template variables for use in client area template files.

```
<?php
/**
 * Hook sample for defining additional template variables
 *
 * @param array $vars Existing defined template variables
 *
 * @return array
 */
function hook_template_variables_example($vars)
{
    $extraTemplateVariables = array();

    // set a fixed value
    $extraTemplateVariables['fixedValue'] = 'abc';

    // fetch clients data if available
    $clientsData = isset($vars['clientsdetails']) ? $vars['clientsdetails'] : null;

    // determine if client is logged in
    if (is_array($clientsData) && isset($clientsData['id'])) {
        $userId = $clientsData['id'];
        // perform calculation here
        $extraTemplateVariables['userSpecificValue'] = '123';
        $extraTemplateVariables['anotherUserOnlyValue'] = '456';
    }

    // return array of template variables to define
    return $extraTemplateVariables;
}

add_hook('ClientAreaPageViewTicket', 1, 'hook_template_variables_example');
```

{{% notice tip %}}
The example above executes on the **View Ticket** page within the client area. There are hook points available for every page of the WHMCS client area. They allow you to define template variables in this way. For a full list, see the Client Area Interface Hooks Index Listing.
{{% /notice %}}

The above hook defines the `{$fixedValue}` template variable and, in the case of a logged in user, the `{$userSpecificValue}` and `{$anotherUserOnlyValue}` variables. These can then be used inside the associated template file (in this case, `viewticket.tpl`) in the regular way.

```
<p>The fixed value is {$fixedValue}.</p>

{if $userSpecificValue && $anotherUserOnlyValue}
    <p>I also have this {$userSpecificValue} and {$anotherUserOnlyValue} to show you.</p>
{/if}
```
