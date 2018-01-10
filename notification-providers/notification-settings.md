+++
next = "/notification-providers/dynamic-fields"
prev = "/notification-providers/provider-settings"
title = "Notification Settings"
toc = true
weight = 40

+++

Notification Settings are configured on a per notification rule basis.

Notification Settings should be used for user configurable settings that are specific to an individual notification. For settings that are the same for all notification rules, [Provider Settings](/notification-providers/provider-settings) should be used instead.

In the case of our HipChat and Slack notification providers, examples of Notification Settings are fields for defining the Channel/Room to notify, as well as the ability to customise the notification message body.

The field definitions you return from this method are used to build a form in the admin notification rule user interface.

Supported field types are: text, password, yesno, dropdown, radio, textarea and dynamic.

```
public function notificationSettings()
{
    return [
        'priority' => [
            'FriendlyName' => 'Notification Priority',
            'Type' => 'dropdown',
            'Options' => [
                'Low',
                'Medium',
                'High',
            ],
            'Description' => 'Choose the notification priority for the alert.',
        ],
    ];
}
```

See also [Dynamic Fields](/notification-providers/dynamic-fields)
