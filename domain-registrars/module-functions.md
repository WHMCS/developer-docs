+++
next = "/domain-registrars/domain-information/"
prev = "/domain-registrars/module-parameters/"
title = "Module Functions"
weight = 60

+++

Registrar module functions are expected to return data and information to WHMCS for rendering to the end user.

The data should be returned as part of a structured array. The exact format varies depending upon the registrar module function being invoked, and the data it returns. For specific details of the expected and supported values, please refer to the sample registrar module.

## Error Handling

Registrar module functions will assume success providing no error message is returned.

In the event of an error or failure, a user friendly error message should be returned in the `error` variable.

```
return array(
    'error' => 'Domain name not found',
);
```
User-friendly error messages are exposed to administrators within the Admin Area. User-friendly error messages are never exposed to clients within the Client Area to protect the potentially sensitive nature of the message being returned.