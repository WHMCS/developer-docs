+++
next = "/mail-providers/provider-settings"
prev = "/mail-providers"
title = "Getting Started"
toc = true
weight = 10

+++

Mail Providers determine how WHMCS transmits email to admins and their customers.

## Sample Module

The `SenderModuleInterface` interface for Mail Providers ships with WHMCS. The class that you create must be in the `Mail` namespace.

## Choosing A Name

Mail Provider Modules are in the `modules/mail` directory. Each module has its own subdirectory, which you should use to store the files relating to the module.

Mail Provider modules are PHP files that contain a class that implements `SenderModuleInterface`.

To create a new Mail Provider module, perform these steps:

1. Choose a name for your module. Module names must be a single string that consists of only alphanumeric characters (no spaces or other characters). Names must begin with a letter and must be unique.
2. Create a new directory using your desired module name.
3. Create a new file within the directory, using your module name as the filename, with the `.php` extension.
Add the following code to the file, replacing `Yourmodulename` with the name of your module:

```
<?php
namespace Mail;

use WHMCS\Module\Contracts\SenderModuleInterface;

/**
* Yourmodulename
*
* @copyright Copyright (c) WHMCS Limited 2005-2020
* @license http://www.example.com/
*/
class Yourmodulename implements SenderModuleInterface
```

For more information on the SenderModuleInterface, see [our additional documentation][https://classdocs.whmcs.com/7.10/WHMCS/Mail/Message.html].
