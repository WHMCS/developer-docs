+++
next = "/hooks/priority"
prev = "/hooks/index"
title = "Getting Started"
toc = true
weight = 5

+++

The following steps demonstrate how to create a hook function in WHMCS.

## Create your Hook File

Hooks live inside files located within the `/includes/hooks/` directory (or as part of a module - see module hooks).

Begin by creating a file named `helloworld.php`:

```
touch ~/includes/hooks/helloworld.php
```

## Add your Hook Function

Hook functions can be either named functions or closures.

Below is an example hook that will execute whenever the ClientAdd event occurs.

```
<?php
/**
 * Register hook function call.
 *
 * @param string $hookPoint The hook point to call
 * @param integer $priority The priority for the given hook function
 * @param string|function Function name to call or anonymous function.
 *
 * @return Depends on hook function point.
 */
add_hook('ClientAdd', 1, function ($vars)
{
    $userid = $vars['userid'];
    $firstname = $vars['firstname'];
    $lastname = $vars['lastname'];
    $email = $vars['email'];
    $password = $vars['password'];

    // Run code to create remote forum account here...
});
```

A selection of variables will be passed into your hook point. The variables you receive will depend upon the action being invoked and the data available to it.

Some hook points will also allow you to return values, and in some cases, the response you provide can alter the program flow to allow you to override default behaviours.

{{% notice info %}}
When using a named function, we recommend you prefix your function name with something unique to you and your code to prevent potential naming conflicts with future code.
{{% /notice %}}
