+++
next = "/domain-registrars/module-parameters/"
prev = "/domain-registrars/domain-syncing/"
title = "Metadata Parameters"
toc = true
weight = 45

+++

[Registrar Modules][domain-registrars] support a number of metadata configuration parameters.

They include:

| Name | Type | Supported As Of | Default | Description |
| ---- | ---- | --------------- | ------- | ----------- |
| DisplayName | Text | 6.0 | Module Name | *An alternate display name that will be used instead of the filename if defined.* |
| APIVersion | Text | 5.2 | 1.1 | *Defines the API version the module uses. Use `1.1` unless you have a need specific to use `1.0`.* |
| NonLinearRegistrationPricing | Boolean | 8.1 | false | *Indicates that there is a difference between the registration amount and renewal amount when importing TLDs. If you set this to `true`, WHMCS will use a nonlinear equation to calculate the appropriate pricing.* |

The following example illustrates how one might make a simple MetaData function.

## Example MetaData Function <a id="example-function"></a>

```
function mymodule_MetaData() {
    return array(
        'DisplayName' => 'myModule',
        'APIVersion' => '1.1',
        'NonLinearRegistrationPricing' => false,
    );
}
```
