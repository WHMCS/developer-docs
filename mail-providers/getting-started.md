+++
next = "/mail-providers/provider-settings"
prev = "/mail-providers"
title = "Getting Started"
toc = true
weight = 10

+++

Mail Providers determine how WHMCS transmits email to admins and their customers.

## Sample Module

The `SenderModuleInterface` interface for Mail Providers ships with WHMCS. The class that you create must be in the `WHMCS\Module\Mail` namespace.

## Choosing A Name

Mail Provider Modules are in the `modules/mail` directory. Each module has its own subdirectory, which you should use to store the files relating to the module.

Mail Provider modules are PHP files that contain a class that implements `SenderModuleInterface`.

To create a new Mail Provider module, perform these steps:

1. Choose a name for your module. Module names must be a single string that consists of only alphanumeric characters (no spaces or other characters). Names must begin with a letter and must be unique.
2. Create a new directory using your desired module name.
3. Create a new file within the directory, using your module name as the filename, with the `.php` extension.
Add the following code to the file, replacing `YourModuleName` with the name of your module:

```
<?php

namespace WHMCS\Module\Mail;

use WHMCS\Exception\Mail\SendFailure;
use WHMCS\Exception\Module\InvalidConfiguration;
use WHMCS\Mail\Message;
use WHMCS\Module\Contracts\SenderModuleInterface;
use WHMCS\Module\MailSender\DescriptionTrait;

/**
* YourModuleName
*
* @copyright Copyright (c) WHMCS Limited 2005-2020
* @license http://www.example.com/
*/
class YourModuleName implements SenderModuleInterface
{
    use DescriptionTrait;
    
    /**
     * Constructor
     *
     * Any instance of a mail module should have the display name at the ready.
     * Therefore it is recommend to ensure these
     * values are set during object instantiation.
     *
     * @see \WHMCS\Module\MailSender\DescriptionTrait::setDisplayName()
     */
    public function __construct()
    {
        $this->setDisplayName('Sample Mail Module');
    }

    /**
     * An array of configuration options for the Mail Provider.
     *
     * @return array
     */
    public function settings()
    {
        //
    }

    /**
     * Test the connection to the Mail Provider.
     *
     * @param array $params Module configuration parameters.
     * @throws InvalidConfiguration On error, InvalidConfiguration will be thrown.
     */
    public function testConnection(array $params)
    {
        //
    }

    /**
     * Send an email.
     *
     * @param array $params Module configuration parameters.
     * @param Message $message The Message object containing details specific to the message.
     *
     * @return void
     * @throws SendFailure
     */
    public function send(array $params, Message $message)
    {
        //
    }
}
```

For more information on the SenderModuleInterface and Message class, see [our additional documentation](https://classdocs.whmcs.com/8.1/WHMCS/Mail_ns.html).
