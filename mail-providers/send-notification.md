+++
prev = "/mail-providers/provider-settings"
title = "Send Notification"
toc = true
weight = 10

+++

The `send` method is responsible for delivering mail to the mail provider.

In this method, you should craft an appropriately formatted message and transmit it to the messaging service.

The method receives two input arguments:

1. `$params` — An array of configuration parameters for the mail provider.
2. `$message` — The `WHMCS\Mail\Message` object.

```
public function send(array $params, Message $message)
{
    $host = $params['host'];
    $username = $params['username'];
    $password = $params['password'];

    $subject = $message->getSubject();
    $body = $message->getBody();
    $plainTextBody = $message->getPlainText();

    $replyTo = '';
    if ($message->getReplyTo()) {
        $replyTo = $message->getReplyTo();
    }

    // Retrieve recipients.
    foreach ($message->getRecipients('to') as $to) {
        $recipients['to'] = [
            'emailAddress' => $to[0],
            'name' => $to[1],
        ];
    }
    foreach ($message->getRecipients('cc') as $to) {
        $recipients['cc'] = [
            'emailAddress' => $to[0],
            'name' => $to[1],
        ];
    }
    foreach ($message->getRecipients('bcc') as $to) {
        $recipients['bcc'] = [
            'emailAddress' => $to[0],
            'name' => $to[1],
        ];
    }

    // Retrieve attachments
    $attachments = [];
    foreach ($message->getAttachments() as $attachment) {
        if (array_key_exists('data', $attachment)) {
            $attachments[] = [
                'data' => $attachment['data'],
                'fileName' => $attachment['filename'],
            ];
        } else {
            $attachments[] = [
                'filePath' => $attachment['filepath'],
                'fileName' => $attachment['filename'],
            ];
        }
    }

    // If a filename is provided. Retrieve the attachment
    // data as required by your Mail Provider.

    // Build API request to remote service
    $postData = [
        'username' => $username,
        'password' => $password,
        'subject' => $subject,
        'body-html' => $body,
        'plaintext-body' => $plainTextbody,
        'to' => $recipients['to'],
        'cc' => $recipients['cc'],
        'bcc' => $recipients['bcc'],
        'reply-to' => $replyTo,
        'attachments' => $attachments,
    ];

    $ch = curl_init();
    curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/send');
    curl_setopt($ch, CURLOPT_POST, 1);
    curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($postData));
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    $response = curl_exec($ch);
    curl_close($ch);

    if (!$response) {
        // Throw a human friendly exception on error
        throw new Exception('No response received from API');
    }
}
```
