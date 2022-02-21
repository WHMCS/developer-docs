+++
next = "/hooks/hook-index"
prev = "/hooks/module-hooks"
title = "Sample Hook"
toc = true
weight = 20

+++

`/includes/hooks/samplehook.php`

The hook below will execute whenever the `ClientAdd` event occurs:

```
<?php

/**
 * Register hook function call.
 *
 * @param string $hookPoint The hook point to call.
 * @param integer $priority The priority for the hook function.
 * @param string|function The function name to call or the anonymous function.
 *
 * @return This depends on the hook function point.
 */

 if (!defined('WHMCS'))
     die('You cannot access this file directly.');

 function create_forum_account($vars) {

     $firstname = $vars['firstname'];
     $lastname = $vars['lastname'];
     $email = $vars['email'];

     // Add the code to create a remote forum account here.

 }

 add_hook('ClientAdd', 1, 'create_forum_account');
```

{{% notice note %}}
For a full list of available hooks, see [Hooks Index](/hooks/hook-index/).
{{% /notice %}}
