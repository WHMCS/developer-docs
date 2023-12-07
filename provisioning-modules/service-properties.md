+++
prev = "/provisioning-modules/server-sync"
title = "Service Properties"
toc = true
weight = 70

+++

<div class="notice info">This page describes a feature available in version 7.2 and above. WHMCS 7.2 introduced the ability to associate product addons with provisioning modules.</div>

Many provisioning modules require you to store additional information relating to a product. To make it easier to work with this extra data and to aid module developers, WHMCS 7.2 introduced the concept of Service Properties.

A service property is a key/value pair relating to a given instance of a product or addon. Stored in custom fields, service properties allow module developers to interact with these fields in a simple programmatic way that is consistent for both products and addons.

## Using Service Properties <a id="using-service-properties"></a>

A model instance (see [Interacting with the Database][db-interaction] ) that represents the target service or addon is passed to all module function invocations as part of the module parameters.

For example:

```
/**
 * @param array $params
 *
 * @return string
 */
function samplemodule_CreateAccount(array $params)
{
    try {
        // Perform actions to provision service and receive back an order number
        $orderNumber = '12345';

        // Save order number to Service Properties
        $params['model']->serviceProperties->save(['Order Number' => $orderNumber]);

        return 'success';
    } catch (\Exception $e) {
        return $e->getMessage();
    }
}

function samplemodule_SuspendAccount(array $params)
{
	try {
		// Utilise Service Properties to retrieve the Order Number
		$orderNumber = $params['model']->serviceProperties->get('Order Number');

		// Perform actions using order number here

		return 'success';
        } catch (\Exception $e) {
            return $e->getMessage();
        }
}
```
The 'save' method will look up a custom field with the given name. If no existing field is found, a new custom field will be created to store the value.

## Supported Fields <a id="supported-fields"></a>

When using Service Properties against a service (for example, a directly-created product rather than an addon), sometimes a dedicated core field will be used instead of a custom field. This occurs for the following field names:

* Username
* Password
* Domain
* License Key
* Dedicated IP
* Disk Usage
* Disk Limit
* Bandwidth Usage
* Bandwidth Limit
* Last Update

Using these field names with an addon will create a custom field.

[db-interaction]: https://developers.whmcs.com/advanced/db-interaction/ "Interacting with the Database"
