+++
prev = "/payment-gateways/getting-started"
next = "/payment-gateways/configuration"
title = "Metadata Parameters"
toc = true
weight = 20

+++

The metadata function allows you to define module related capabilities and settings.

Payment Gateway Modules support the following metadata configuration parameters.

| Name | Type | Supported As Of | Default | Description |
| ---- | ---- | --------------- | ------- | ----------- |
| DisplayName | String | 6.0 | Module Name | An alternate display name that will be used instead of the filename if defined |
| APIVersion | String | 5.2 | 1.1 | Defines API Version the module uses. Use `1.1` unless you have a need specific to use `1.0` |
| gatewayType | String | 8.0 | *undefined* | This should be set to 'Bank' if the module is a Bank module, or the metadata should be omitted. |
| failedEmail | String | 7.7 | Credit Card Payment Failed | The name of an email template to send should a payment capture fail |
| successEmail | String | 7.7 | Credit Card Payment Confirmation | The name of an email template to send should a payment capture be successful |
| pendingEmail | String | 7.7 | Credit Card Payment Pending | The name of an email template to send should a payment capture be pending |

### Example

```
function yourmodulename_MetaData()
{
    return [
        'DisplayName' => 'Your Module Name',
        'gatewayType' => 'Bank', // Only set if the module is a Bank Module
        'failedEmail' => 'Credit Card Payment Failed',
        'successEmail' => 'Custom Credit Card Payment Template', // You can utilise custom templates here
        'pendingEmail' => 'Custom Credit Card Pending Template',
        'APIVersion' => '1.1', // Use API Version 1.1
    ];
}

```
