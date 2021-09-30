+++
prev = "/provisioning-modules/supported-functions"
next = "/provisioning-modules/core-module-functions"
title = "Module Parameters"
toc = true
weight = 30

+++

The module parameters are the data/values passed into each function when called.
Every provisioning module function receives the same parameters.
These parameters provide information about the specific product/service the module command runs for.
The parameters also contains the settings from the product itself.

| Variable Name | Description |
|---|---|
| serviceid | The unique ID of the service.<br />Database Field: tblhosting.id
| userid | The unique ID of the account that owns the service.<br />Database Field: tblclients.id<br />This variable uses naming conventions that originated prior to WHMCS 8.0. |
| pid | The product ID for the service.<br />Database Field: tblproducts.id |
| serverid | The assigned server ID for the service.<br />Database Field: tblservers.id |
| domain | The domain entered by the customer when ordering.<br />Database Field: tblhosting.domain |
| username | Username generated for the service. (defaults to first 8 letters of the domain)<br />Database Field: tblhosting.username |
| password | Password generated for the service. (10 char generated on first creation consisting of letters & numbers, both upper & lowercase).  <br />Database Field: tblhosting.password |
| producttype | The product type which can be one of hostingaccount, reselleraccount, server or other. |
| moduletype | The module name (will match filename of module). |
| configoptionX | with X being from 1 to 24. <br />These fields contain the module settings for the product defined in the ConfigOptions function. |
| clientsdetails | Contains an array of all client details service owner. This contains things like firstname, lastname, email, address1, country, etc… |
| customfields | Contains an array of all custom fields defined on the product.  <br />The key is the custom field name - $params\['customfields']\['Field Name']. |
| configoptions | Contains an array of all the configurable options defined on the product.  <br />Again the key being the option name in this case - $params\['configoptions']\['Option Name Here']. |
| server | true/false - Is the product assigned to a server. |
| serverip | The IP Address of the selected server. |
| serverhostname | The Hostname of the selected server. |
| serverusername | The Username of the selected server. |
| serverpassword | The Password of the selected server. |
| serveraccesshash | The Access Hash of the selected server. |
| serversecure | true/false - Is an SSL connection enabled in the Server Configuration. |
| serverport | The server port if module supports override with custom port |

## Config Options <a id="config-options"></a>

[Config Options][product-config-options] (do not confuse with Configurable Options) are the module's settings.
These are defined in the ConfigOptions function of the module.
Config Options are set on a per product basis.
Supplied as a numbered list: $params\[‘configoption1’], $params\[‘configoption2’], etc.
Defined by the order specified in the ConfigOptions function of the module.

**Note:** Every module function except the \_ConfigOptions function receives the $params array. The \_ConfigOptions function is unique because it is the only function that is not called in relation to a specific client instance of a product or service.

## Custom Fields & Configurable Options <a id="custom-fields-configurable-options"></a>

Values from any custom fields & configurable options are passed into modules as parameters.
Passed as an array with the key being the name of the field or option.

For example for a custom field called “Username”, would become $params\[‘customfields’]\[‘Username’].
Likewise, a configurable option named “Disk Space”, would become $params\[‘configoptions’]\[‘Disk Space’].


[product-config-options]: /provisioning-modules/getting-started#product-configuration-options "Product Configuration Options"
