+++
title = "Domain"
weight = 10

+++

The following hooks are provided for Domain related events.

## PreRegistrarRegisterDomain

Executes prior to the registrar function being executed for a domain. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |

#### Response

Accepts an optional array return. Return `abortWithSuccess=true` to abort the action and treat it as successful. Return `abortWithError=Error messages goes here` to abort the action and treat it as failed.

#### Example Code

```
<?php
add_hook('PreRegistrarRegisterDomain', 1, function($vars)
    {
        $domainName = $vars['params']['sld'] . '.' . $vars['params']['tld'];

        return array(
            'abortWithError' => 'Error message to display goes here',
        );

        //return array(
        //    'abortWithSuccess' => true,
        //);
    }
);
```

## PreRegistrarRenewDomain

Executes prior to the registrar function being executed for a domain. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |

#### Response

Accepts an optional array return. Return `abortWithSuccess=true` to abort the action and treat it as successful. Return `abortWithError=Error messages goes here` to abort the action and treat it as failed.

#### Example Code

```
<?php
add_hook('PreRegistrarRenewDomain', 1, function($vars) {
    // Perform hook code here...
});
```

## PreRegistrarTransferDomain

Executes prior to the registrar function being executed for a domain. Allows the action to be aborted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Array of common module parameters. See https://developers.whmcs.com/domain-registrars/module-parameters/ |

#### Response

Accepts an optional array return. Return `abortWithSuccess=true` to abort the action and treat it as successful. Return `abortWithError=Error messages goes here` to abort the action and treat it as failed.

#### Example Code

```
<?php
add_hook('PreRegistrarTransferDomain', 1, function($vars) {
    // Perform hook code here...
});
```

