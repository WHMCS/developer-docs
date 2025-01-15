+++
prev = "/provisioning-modules/admin-dashboard-widgets"
next = "/provisioning-modules/server-sync"
title = "Module Logging"
toc = true
weight = 110

+++

To make reviewing and debugging module calls easier, WHMCS has a built in logging function.
This allows the record of the request and response strings for every call the module makes.
This becomes available in an accessible way via the WHMCS admin interface.
If you plan to release the module, this allows end users to troubleshoot and debug issues experienced using the module.
This also allows you to be able to debug issues experienced while using it.

Logging is not something that is always enabled.
This is to avoid logs growing too large, so it's something that needs enabling for the logging to occur.
To toggle logging, goto **Configuration** > **System Logs** > **Module Log**.
This is the same place to review the logs.

To utilise this functionality, the module needs to make a call as follows:

```
/**
 * Log module call.
 *
 * @param string $module The name of the module
 * @param string $action The name of the action being performed
 * @param string|array $requestString The input parameters for the API call
 * @param string|array $responseData The response data from the API call
 * @param string|array $processedData The resulting data after any post processing (eg. json decode, xml decode, etc...)
 * @param array $replaceVars An array of strings for replacement
 */
logModuleCall($module, $action, $requestString, $responseData, $processedData, $replaceVars);
```

We recommend passing data strings such as usernames and passwords into the `$replaceVars` parameter to allow them to be automatically scrubbed and omitted from module log entries.
