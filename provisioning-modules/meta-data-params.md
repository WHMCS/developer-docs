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
| DefaultSSLPort | Integer | 6.0 | N/A | *If specified, will display by default when configuring a server with the module when `Use SSL` is disabled and will allow a user to override it should they wish.  Use this if your API can operate on varying port numbers.* |
| ServiceSingleSignOnLabel | Text | 6.0 | N/A | *For use with Single Sign-On, define here what you want to show as the text label for the Single Sign-On option for an instance of a service under a client.* |
| AdminSingleSignOnLabel | Text | 6.0 | N/A | *For use with Single Sign-On, define here what you want to show as the text label for the Single Sign-On option for a server assigned to the module within the admin area.* |

[provisioning-modules]: /provisioning-modules "Provisioning Modules"
