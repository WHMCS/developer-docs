+++
next = "/api/response-types/"
prev = "/api/authentication/"
title = "Access Control"
toc = true
weight = 30

+++

Access to the API by default is restricted by IP.

For situations where IP access control is not feasible, an Access Key can also be configured.

## Managing Allowed IPs

To configure the Allowed IPs, login to the WHMCS admin area and navigate to <em>Setup > General Settings > Security</em>.

There you can add and remove IPs, along with a note referencing.

## Configuring an Access Key

Alternatively an access key can be configured to allow IP restrictions to be bypassed.

It works by defining a secret key/passphrase in the WHMCS configuration.php file which is then passed into all API calls.  To configure it, add a line as follows to your `configuration.php` file in the root WHMCS directory.

```
$api_access_key = 'secret_key_passphrase_goes_here';
```

An API Access Key can contain letters, numbers, and the following special characters only:

```
! @ # $ % . ( ) * [ ] - _
```

Following the introduction of an API Access Key, you can then include it in your API requests as follows:

```
?action=xxxx&username=xxx&password=xxx&accesskey=secret_key_passphrase_goes_here
```
