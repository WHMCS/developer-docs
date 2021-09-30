+++
prev = "/provisioning-modules/loader-functions"
next = "/provisioning-modules/supported-functions"
title = "Meta Data Parameters"
toc = true
weight = 20

+++

[Provisioning Modules][provisioning-modules] support a number of meta data configuration parameters.

They include:

| Name | Type | Supported As Of | Default | Description |
| ---- | ---- | --------------- | ------- | ----------- |
| DisplayName | Text | 6.0 | Module Name | *An alternate display name that will be used instead of the filename if defined* |
| APIVersion | Text | 5.2 | 1.1 | *Defines API Version the module uses. Use `1.1` unless you have a need specific to use `1.0`* |
| RequiresServer | Boolean | 6.0 | | *Defines whether the module requires servers to function. A lot of modules these days don't require servers be configured so setting this to false prevents users from creating servers assigned to it.* |
| DefaultNonSSLPort | Integer | 6.0 | N/A | *If specified, will display by default when configuring a server with the module when `Use SSL` is disabled and will allow a user to override it should they wish.  Use this if your API can operate on varying port numbers.* |
| DefaultSSLPort | Integer | 6.0 | N/A | *If specified, will display by default when configuring a server with the module when `Use SSL` is enabled and will allow a user to override it should they wish.  Use this if your API can operate on varying port numbers.* |
| ServiceSingleSignOnLabel | Text | 6.0 | N/A | *For use with Single Sign-On, define here what you want to show as the text label for the Single Sign-On option for an instance of a service under a client.* |
| AdminSingleSignOnLabel | Text | 6.0 | N/A | *For use with Single Sign-On, define here what you want to show as the text label for the Single Sign-On option for a server assigned to the module within the admin area.* |
| ListAccountsProductField | Text | 7.10 | N/A | *For use with Server Sync, define the config option indexed field, from the _ConfigOptions function, that identifies the product on the remote system.* |
| ListAccountsUniqueIdentifierDisplayName | Text | 7.10 | Domain | *For use with Server Sync, define the display name of the unique identifier to be displayed on the table output.* |
| ListAccountsUniqueIdentifierField | Text | 7.10 | N/A | *For use with Server Sync and Usage Metrics, define the field in the return that matches the unique identifier. The following values are supported: `domain`, `username`, `customfield.yourFieldName`. If using the `customfield.yourFieldName` value, replace `yourFieldName` with the name of the custom field to be used.* |

These parameters are defined by a function which is responsible for returning an associative array containing the defined meta data configuration parameters and their values.

The following example illustrates how one might make a simple MetaData function.

## Example MetaData Function <a id="example-function"></a>

```
function mymodule_MetaData() {
    return array(
        'DisplayName' => 'myModule',
        'APIVersion' => '1.1',
        'DefaultNonSSLPort' => '1234',
        'DefaultSSLPort' => '4321',
        'ServiceSingleSignOnLabel' => 'Login to myModule Client',
        'AdminSingleSignOnLabel' => 'Login to myModule Admin',
        'ListAccountsUniqueIdentifierDisplayName' => 'Domain',
        'ListAccountsUniqueIdentifierField' => 'domain',
        'ListAccountsProductField' => 'configoption1',
    );
}
```

[provisioning-modules]: /provisioning-modules "Provisioning Modules"
