+++
next = "/notification-providers/provider-settings"
prev = "/notification-providers/getting-started"
title = "Initialisation"
toc = true
weight = 20

+++

Notification modules require a display name and logo to be defined for them.

It is recommended to set these values during object instantiation.

A [DescriptionTrait](https://docs.whmcs.com/classes/7.4/WHMCS/Module/Notification/DescriptionTrait.html) is made available which provides methods to fulfill this requirement.

```
use DescriptionTrait;

/**
 * Constructor
 */
public function __construct()
{
    $this->setDisplayName('Your Friendly Display Name')
        ->setLogoFileName('logo.png');
}
```

* The display name should be a human friendly version of your module name.
* The logo filename should be a path relative to the base directory of the module.

For more information on the description trait, please refer to https://docs.whmcs.com/classes/7.4/WHMCS/Module/Notification/DescriptionTrait.html
