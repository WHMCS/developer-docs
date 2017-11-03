+++
next = "/notification-providers/notification-settings"
prev = "/notification-providers/initialisation"
title = "Provider Settings"
toc = true
weight = 30

+++

A notification provider can define settings required for the notification module to be activated.

The field definitions you return from this method are used to build a form in the admin user interface that must be filled out in order to activate the notification provider module.

For example, if the module connects to a remote messaging service, this might be a username/password or OAuth token required to authenticate to that service.

Supported field types are: text, password, yesno, dropdown, radio & textarea.

Below is an example of two fields defined, with the names `api_username` and `api_password`.

```
/**
 * Provider settings.
 *
 * @return array
 */
public function settings()
{
    return [
        'api_username' => [
            'FriendlyName' => 'API Username',
            'Type' => 'text',
            'Description' => 'Required username to authenticate with messaging service',
        ],
        'api_password' => [
            'FriendlyName' => 'API Password',
            'Type' => 'password',
            'Description' => 'Required password to authenticate with messaging service',
        ],
    ];
}
```

## Validating User Supplied Setting Values

Upon submission of provider settings, the user provided values can be validated using the `testConnection` method.

If validation fails, simply throw an exception to abort the save action and display an error message to the end user. The error message will be the message provided within the exception so make it user friendly!

```
/**
 * Test connection.
 *
 * @param array $settings
 *
 * @return array
 */
public function testConnection($settings)
{
    $api_username = $settings['api_username'];
    $api_password = $settings['api_password'];

    // Attempt to connect to API service to verify input credentials
    // and upon error, throw an exception.

    throw new \Exception('Unable to authenticate with supplied API username and password');
}
```
