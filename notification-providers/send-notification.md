+++
prev = "/notification-providers/dynamic-fields"
title = "Send Notification"
toc = true
weight = 60

+++

The `sendNotification` method is responsible for delivering a notification to the end user.

This method will be called by WHMCS when a notification rule is triggered and all conditions for it are met.

In this method, you should craft an appropriately formatted message and transmit it to the messaging service.

The method receives 3 input arguments:

1. *$notification* - A notification to send. This will be an instance of the [NotificationInterface](https://docs.whmcs.com/classes/7.4/WHMCS/Notification/Contracts/NotificationInterface.html) class.
2. *$moduleSettings* - An array containing all the provider settings defined for your notification module in the Provider Settings method.
3. *$notificationSettings* - An array containing all the notification settings defined for the currently triggered notification rule.

```
public function sendNotification(NotificationInterface $notification, $moduleSettings, $notificationSettings)
{
    $api_username = $moduleSettings['api_username'];
    $api_password = $moduleSettings['api_password'];

    $priority = $notificationSettings['priority'];
    $channel = $notificationSettings['channel'];

    // Build API Request to remote service

    $postData = [
        'username' => $api_username,
        'password' => $api_password,
        'priority' => $priority,
        'channel' => $channel,
        'title' => $notification->getTitle(),
        'message' => $notification->getMessage(),
        'url' => $notification->getUrl(),
        'attributes' => [],
    ];

    // Attributes vary depending on the event trigger. Loop through as necessary.
    foreach ($notification->getAttributes() as $attribute) {
        $postData['attributes'][] = [
            'label' => $attribute->getLabel(),
            'value' => $attribute->getValue(),
            'url' => $attribute->getUrl(),
            'style' => $attribute->getStyle(),
            'icon' => $attribute->getIcon(),
        ];
    }

    // Call the remote API
    $response = file_get_contents('https://www.example.com/?' . http_build_query($postData));

    if (!$response) {
        // Throw a human friendly exception on error
        throw new Exception('No response received from API');
    }
}
```
