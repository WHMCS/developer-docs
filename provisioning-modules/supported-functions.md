+++
prev = "/provisioning-modules/meta-data-params"
next = "/provisioning-modules/module-parameters"
title = "Supported Functions"
toc = true
weight = 25

+++

Here is an overview of all functions that a WHMCS provisioning module can contain.
Functions within a module are optional and need not be in the module if they don’t apply.
Remember, all functions should have the prefix **filename_** and then the function name.
The function name is the header below.

## CreateAccount <a id="create-account"></a>

This function runs when a new product provisions.
This can be by WHMCS upon checkout or payment for a new order.
Also, by an admin user from the Products/Services tab in a clients profile of the admin area.


## SuspendAccount <a id="suspend-account"></a>

This function runs when a suspension is requested.
Requested by the WHMCS Cron when a product becomes overdue, or by admin user in the Client Profile.

## UnsuspendAccount <a id="unsuspend-account"></a>

This function runs when an unsuspension is requested.
Requested upon payment of an overdue invoice for a product.

## TerminateAccount <a id="terminate-account"></a>

This function runs when a termination is requested.
Requested by the WHMCS Cron for long overdue products when enabled ([Automation Settings][automation-settings-termination]).
Also requested by an admin user in the Client Profile.

## Renew <a id="renew"></a>

This function runs each time a renewal invoice for a product becomes paid.

## ChangePassword <a id="change-password"></a>

This function runs as a client requests a password change.
The option will not show up if the function is not defined in the module.
The status of the product must also be active.
Admins can also invoke this command from the admin area.

## ChangePackage <a id="change-package"></a>

This function runs for upgrading and downgrading of products.
This function runs when an upgrade or downgrade order placed by the client becomes paid.
Admins can also invoke this from the product management pages.
The same function runs for upgrades and downgrades of both products and configurable options.

## ClientArea <a id="client-area"></a>

This function can be used to define module specific client area output.
It accepts a return of HTML for display on the product details page of the client area.
Output via a template file within the module folder named "clientarea.tpl" is also possible.
Discussion of this function in more detail later on in the docs.

## AdminLink <a id="admin-link"></a>

Used to define HTML code that displays on server configuration page (**Setup** > **Products/Services** > **Servers**).
Used to provide an automated shortcut/login link to the integrated server control panel.

## LoginLink <a id="login-link"></a>

Used to define HTML code to link to the customers account on a server control panel.
Displayed on the product management page of the admin area.
The return must be HTML output or link (no forms).

## ClientAreaCustomButtonArray <a id="client-area-custom-button-array"></a>

Used to define custom functions that your module supports.
Customers can invoke and run these from the client area.
The functions can perform actions or product page output in the client area.
Example usages for this are to provide product management pages, bandwidth reporting pages, etc…

## ClientAreaAllowedFunctions <a id="client-area-allowed-functions"></a>

Like the above, used to define custom functions.
Customers can invoke, but are not shown as buttons by default (i.e. custom client area output will invoke them).

## AdminCustomButtonArray <a id="admin-custom-button-array"></a>

Used to define custom functions in your module for admin users.
This can contain more functions than the client area equivalent.

## UsageUpdate <a id="usage-update"></a>

Used to perform a daily import of the disk and bandwidth usage from a server.
The data imported is then used to display the usage stats both within the client and admin areas of WHMCS.
The data is also used in disk and bandwidth overage billing calculations if enabled for a product.

## MetricProvider <a id="usage-metrics"></a>

Used to list the names of and collect usage for metric stats of a server.
The name data is used for product price configuration within the admin areas of WHMCS.
The usage data is periodically collected and stored in WHMCS for display within
both the client and admin area.  That stored usage is also used for generating
invoice line items, if enabled in the Invoicing section of General Setting. 

## AdminServicesTabFields <a id="admin-services-tab-fields"></a>

Used to define extra fields or output to display within admin product pages.

## AdminServicesTabFieldsSave <a id="admin-servics-tab-fields-save"></a>

Used in conjunction with the above.
This function handles the values submitted in any custom fields when a save occurs.

## MetaData <a id="meta-data"></a>

Used to define a number of meta data configuration parameters.
This function returns an array, consisting key-value pairs, where the key is the parameter name and the value is the parameter value.

## CustomActions <a id="custom-actions"></a>

Used to define a list of items that perform a function and redirect the user to a specified URL. Customers can invoke items from within the Client Area. The defined function can perform actions that need to take place before redirecting the customer. Currently, this supports adding buttons to the "Active Products/Services" panel on the Client Area homepage.

[automation-settings-termination]: http://docs.whmcs.com/Automation_Settings#Enable_Termination "Automation Settings"
