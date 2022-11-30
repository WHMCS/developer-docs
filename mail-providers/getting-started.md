+++
next = "/mail-providers/provider-settings"
prev = "/mail-providers"
title = "Getting Started"
toc = true
weight = 10

+++

Mail providers determine how WHMCS transmits email to admins and their customers.

## Sample Module

The `SenderModuleInterface` interface for mail providers ships with WHMCS. The class that you create must be in the `WHMCS\Module\Mail` namespace.

## Choosing A Name

Mail provider modules are in the `modules/mail` directory. Each module has its own subdirectory, which you should use to store the files relating to the module.

Mail provider modules are PHP files that contain a class that implements the `SenderModuleInterface` interface.

To create a new mail provider module, perform these steps:

1. Choose a name for your module. Module names must be a single string that consists of only alphanumeric characters (no spaces or other characters). Names must begin with a letter and must be unique.
2. Create a new directory using your desired module name.
3. Create a new file within the directory, using your module name as the filename and the `.php` extension.
4. Add the following code to the file, replacing `YourModuleName` with the name of your module:

```
<?php

namespace WHMCS\Module\Mail;

use WHMCS\Authentication\CurrentUser;
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
     * Provider settings.
     *
     * @return array
     */
    public function settings()
    {
        return [
            'username' => [
                'FriendlyName' => 'Username',
                'Type' => 'text',
                'Description' => 'The Your Module Name username.',
            ],
            'password' => [
                'FriendlyName' => 'Password',
                'Type' => 'password',
                'Description' => 'The Your Module Name password.',
            ],
        ];
    }

    /**
     * Module name used internally
     *
     * @return string
     */
    public function getName()
    {
        return 'Yourmodulename';
    }

    /**
     * Module name shown in the Admin Area
     *
     * @return string
     */
    public function getDisplayName()
    {
        return 'Your Module Name';
    }

    /**
     * Test connection.
     *
     * @param array $settings
     *
     * @return array
     */
    public function testConnection(array $settings)
    {
        $currentAdmin = (new CurrentUser)->admin();

        try {
            $ch = curl_init();
            curl_setopt($ch, CURLOPT_HTTPAUTH, CURLAUTH_BASIC);
            curl_setopt($ch, CURLOPT_USERPWD, $settings['username'] . ':' . $settings['password']);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);

            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, 'POST');
            curl_setopt($ch, CURLOPT_URL, 'https://example.com/api/messages');
            curl_setopt($ch, CURLOPT_POSTFIELDS, [
                'from' => 'test@example.com',
                'to' => $currentAdmin->email,
                'subject' => 'Your Module Name Test',
                'html' => 'This email was sent to test the new mail configuration. If you received this message, '
                    . 'it confirms that email is sending correctly. You do not need to take any further action.'
            ]);

            curl_exec($ch);
            curl_close($ch);
        } catch (Exception $e) {
            throw new Exception("Unable to send a Test Message: " . $e->getMessage());
        }
    }

    /**
     * This is responsible for delivering mail to the mail provider.
     *
     * @param array $settings
     * @param Message $message
     */
    public function send(array $settings, Message $message)
    {
        try {

            $postFields = [
                'from' => $message->getFromName(),
                'fromEmail' => $message->getFromEmail(),
                'subject' => $message->getSubject(),
            ];

            // Retrieve recipients.
            foreach ($message->getRecipients('to') as $to) {
                $postFields['toEmail'][] = $to[0];
                $postFields['toName'][] = $to[1];
            }
            foreach ($message->getRecipients('cc') as $cc) {
                $postFields['ccEmail'][] = $cc[0];
                $postFields['ccName'][] = $cc[1];
            }
            foreach ($message->getRecipients('bcc') as $bcc) {
                $postFields['bccEmail'][] = $bcc[0];
                $postFields['bccName'][] = $bcc[1];
            }

            $replyTo = $message->getReplyTo();
            if ($replyTo) {
                $postFields['replyToName'] = $replyTo['name'];
                $postFields['replyToEmail'] = $replyTo['email'];
            }

            // Build body
            $body = $message->getBody();
            $plainText = $message->getPlainText();
            if ($body) {
                $postFields['html'] = $body;
                if (empty($plainText)) {
                    $plainText = ' ';
                }
                $postFields['text'] = $plainText;
            } else {
                $postFields['text'] = $plainText;
            }

            //Prepare attachments
            $attachments = [];
            foreach ($message->getAttachments() as $attachment) {
                if (array_key_exists('data', $attachment)) {
                    $filename = $attachment['filename'];
                    $data = $attachment['data'];
                } else {
                    $filename = $attachment['filename'];
                    $data = file_get_contents($attachment['filepath']);
                }
                $attachments[] = ['filename' => $filename, 'data' => $data];
            }

            $postFields['attachments'] = $attachments;

            $ch = curl_init();
            curl_setopt($ch, CURLOPT_HTTPAUTH, CURLAUTH_BASIC);
            curl_setopt($ch, CURLOPT_USERPWD, $settings['username'] . ':' . $settings['password']);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);

            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, 'POST');
            curl_setopt($ch, CURLOPT_URL, 'https://example.com/api/messages');
            curl_setopt($ch, CURLOPT_POSTFIELDS, $postFields);

            curl_exec($ch);
            curl_close($ch);
        } catch (Exception $e) {
            throw new Exception("Unable to send a Test Message: " . $e->getMessage());
        }
    }
}
```

For more information on the `SenderModuleInterface` and `Message` class, see [our additional documentation](https://classdocs.whmcs.com/8.1/WHMCS/Mail_ns.html).
