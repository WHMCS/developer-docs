+++
next = "/mail-providers/send-notification"
prev = "/mail-providers/getting-started"
title = "Provider Settings"
toc = true
weight = 10

+++

A Mail Provider can define required settings to activate the mail provider module.

The field definitions you return from this method are used to build a form in the admin user interface that must be filled out in order to activate the mail provider module.

For example, if the module connects to a remote messaging service, this might be a username and password or a required OAuth token to authenticate to that service.

Supported field types are `text`, `password`, `yesno`, `dropdown`, `radio`, and `textarea`.

Below is an example of two defined fields, with the names `api_username` and `api_password`.

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
            'Description' => 'The required username to authenticate with messaging service.',
        ],
        'api_password' => [
            'FriendlyName' => 'API Password',
            'Type' => 'password',
            'Description' => 'The required password to authenticate with messaging service.',
        ],
    ];
}
```

## Validating User-Supplied Setting Values

On submission of mail provider settings, you can validate the user-provided values using the `testConnection` method.

If validation fails, throw an exception to abort the save action and display an error message to the end user. The error message will be the message within the exception.

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

    throw new \Exception('The system was unable to authenticate with the supplied API username and password.');
}
```
