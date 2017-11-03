+++
next = "/notification-providers/send-notification"
prev = "/notification-providers/provider-settings"
title = "Dynamic Fields"
toc = true
weight = 50

+++

Dynamic fields are a special type of notification setting.

A dynamic field is rendered as a dropdown menu and is recommended for settings where the list of options and choices need to be populated with a poll or fetch from a remote service or API.

An example use case is demonstrated in our HipChat and Slack notification providers, where Dynamic Fields are used to provide a list of Channels and Rooms that are fetched in real-time from the respective APIs.

Below is an example of a "channel" dynamic field.

```
public function notificationSettings()
{
    return [
        'channel' => [
            'FriendlyName' => 'Notification Channel',
            'Type' => 'dynamic',
            'Description' => 'Choose the notification channel for the alert.',
        ],
    ];
}

public function getDynamicField($fieldName, $settings)
{
    $values = [];

    if ($fieldName == 'channel') {

        // Perform remote API call, query or database fetch and build an array:
        //
        // $values[] = [
        //     'id' => '123',
        //     'name' => 'Demo Room',
        //     'description' => 'Room ID',
        // ];

    } elseif ($fieldName == '...') {
        // ....
    }

    return [
        'values' => $values,
    ];
}
```
