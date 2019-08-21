+++
prev = "/payment-gateways/getting-started"
next = "/payment-gateways/configuration"
title = "Meta Data Parameters"
toc = true
weight = 15

+++

The meta data function allows you to define module related capabilities and settings.

Payment Gateway Modules support the following meta data configuration parameters.

| Name | Type | Supported As Of | Default | Description |
| ---- | ---- | --------------- | ------- | ----------- |
| DisplayName | Text | 6.0 | Module Name | An alternate display name that will be used instead of the filename if defined |
| APIVersion | Text | 5.2 | 1.1 | Defines API Version the module uses. Use `1.1` unless you have a need specific to use `1.0` |
| failedEmail | String | 7.7 | Credit Card Payment Failed | The name of an email template to send should a payment capture fail |
| successEmail | String | 7.7 | Credit Card Payment Confirmation | The name of an email template to send should a payment capture be successful |
| pendingEmail | String | 7.7 | Credit Card Payment Pending | The name of an email template to send should a payment capture be pending |
