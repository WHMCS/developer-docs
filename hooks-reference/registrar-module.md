+++
title = "Registrar Module"
weight = 10

+++

The following hooks are provided for Registrar Module related events.

## AfterRegistrar

Executes after any standard registrar module function call. Hook name is updated as appropriate. AfterRegistrarGetNameservers, AfterRegistrarSaveNameservers, AfterRegistrarGetRegistrarLock, AfterRegistrarSaveRegistrarLock, AfterRegistrarGetURLForwarding, AfterRegistrarSaveURLForwarding, AfterRegistrarGetEmailForwarding, AfterRegistrarSaveEmailForwarding, AfterRegistrarGetDNS, AfterRegistrarSaveDNS, AfterRegistrarRenewDomain, AfterRegistrarRegisterDomain, AfterRegistrarTransferDomain, AfterRegistrarGetContactDetails, AfterRegistrarSaveContactDetails, AfterRegistrarGetEPPCode, AfterRegistrarRequestDelete, AfterRegistrarReleaseDomain, AfterRegistrarRegisterNameserver, AfterRegistrarModifyNameserver, AfterRegistrarDeleteNameserver, AfterRegistrarIDProtectToggle, AfterRegistrarGetRegistrantContactEmailAddress

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Common domain registrar parameters. See http://developers.whmcs.com/domain-registrars/module-parameters/ |
| results | array |  |
| functionExists | bool |  |
| functionSuccessful | bool |  |

#### Response

Return boolean to 'abortWithSuccess' or string 'abortWithError'. Eg: return array('abortWithSuccess' => true,); return array('abortWithError' => 'This is an error',);

#### Example Code

```
<?php

add_hook('AfterRegistrarGetNameservers', 1, function($vars)
{
    if (
        $vars['functionExists']
        && !$vars['functionSuccessful']
    ) {
        //do something on function existing and failure
        $domainName = $vars['params']['sld'] . '.' . $vars['params']['tld'];

        if ($domainName == 'whmcs.com') {
            return array(
                'abortWithError' => 'Show this message as an error',
            );
        }
    }
    return array();
});
```

## AfterRegistrarRegistration

Executes after a successful domain register command

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Common domain registrar parameters. See http://developers.whmcs.com/domain-registrars/module-parameters/ |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarRegistration', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarRegistrationFailed

Executes after a failed domain register command

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Common domain registrar parameters. See http://developers.whmcs.com/domain-registrars/module-parameters/ |
| error | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarRegistrationFailed', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarRenewal

Executes after a successful domain renewal command

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Common domain registrar parameters. See http://developers.whmcs.com/domain-registrars/module-parameters/ |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarRenewal', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarRenewalFailed

Executes after a failed domain renewal command

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Common domain registrar parameters. See http://developers.whmcs.com/domain-registrars/module-parameters/ |
| error | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarRenewalFailed', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarTransfer

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarTransfer', 1, function($vars) {
    // Perform hook code here...
});
```

## AfterRegistrarTransferFailed

Executes after a failed domain transfer command

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Common domain registrar parameters. See http://developers.whmcs.com/domain-registrars/module-parameters/ |
| error | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterRegistrarTransferFailed', 1, function($vars) {
    // Perform hook code here...
});
```

## PreRegistrar

Executes before any standard registrar module function call. Hook name is updated as appropriate. PreRegistrarGetNameservers, PreRegistrarSaveNameservers, PreRegistrarGetRegistrarLock, PreRegistrarSaveRegistrarLock, PreRegistrarGetURLForwarding, PreRegistrarSaveURLForwarding, PreRegistrarGetEmailForwarding, PreRegistrarSaveEmailForwarding, PreRegistrarGetDNS, PreRegistrarSaveDNS, PreRegistrarRenewDomain, PreRegistrarRegisterDomain, PreRegistrarTransferDomain, PreRegistrarGetContactDetails, PreRegistrarSaveContactDetails, PreRegistrarGetEPPCode, PreRegistrarRequestDelete, PreRegistrarReleaseDomain, PreRegistrarRegisterNameserver, PreRegistrarModifyNameserver, PreRegistrarDeleteNameserver, PreRegistrarIDProtectToggle, PreRegistrarGetRegistrantContactEmailAddress

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| params | array | Common domain registrar parameters. See http://developers.whmcs.com/domain-registrars/module-parameters/ |

#### Response

Return boolean to 'abortWithSuccess' or string 'abortWithError'. Eg: return array('abortWithSuccess' => true,); return array('abortWithError' => 'This is an error',);

#### Example Code

```
<?php

add_hook('PreRegistrarGetNameservers', 1, function($vars)
    {
        $domainName = $vars['params']['sld'] . '.' . $vars['params']['tld'];
        return array(
            'abortWithError' => 'Show this message as an error',
        );
        //return array('abortWithSuccess' => true);
    }
);
```

