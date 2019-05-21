+++
next = "/notification-providers/initialisation"
prev = "/notification-providers/index"
title = "Getting Started"
toc = true
weight = 10

+++

## Sample Module

The `Email` notification module that ships with WHMCS is not encoded so the source code is viewable. We recommend using this as a starting point for a custom module. This module can be found in the `/modules/notifications/Email` directory.

## Choosing a Name

Notification Modules are stored in the `/modules/notifications/` directory.

Each module has its own subdirectory within which all files relating to that module should be stored.

At its simplest, a notification module is a PHP file containing a class that implements the [NotificationModuleInterface](https://docs.whmcs.com/classes/7.4/WHMCS/Module/Contracts/NotificationModuleInterface.html).

To get started creating a new notification module, follow the steps below.

1. *Choose a name* for your module. Module names should be a single word, consisting of only letters and numbers. Names must begin with a letter, and must be unique.
2. *Create a new directory* using your desired module name.
3. *Create a new file* within the directory with the filename `Yourmodulename.php`
4. *Add the following code* to the file, replacing all instances of `Yourmodulename` with the name of your module as appropriate.

```
<?php

namespace WHMCS\Module\Notification\Yourmodulename;

use WHMCS\Module\Contracts\NotificationModuleInterface;

/**
 * Yourmodulename
 *
 * @copyright Copyright (c) WHMCS Limited 2005-2017
 * @license http://www.example.com/
 */
class Yourmodulename implements NotificationModuleInterface
{
}
```

For more information on the NotificationModuleInterface, please refer to https://docs.whmcs.com/classes/7.4/WHMCS/Module/Contracts/NotificationModuleInterface.html
