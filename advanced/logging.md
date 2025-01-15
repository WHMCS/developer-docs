+++
next = "/advanced/widgets/"
prev = "/advanced/currency-formatting/"
title = "Logging"
weight = 50

+++

The following logging helper methods are made available in WHMCS.

## Log Activity

A helper method is available for adding entries to the activity log.

This function is available to all hooks, modules and template files throughout the WHMCS system.

```
/**
 * Log activity.
 *
 * @param string $message The message to log
 * @param int $clientId An optional client id to which the log entry relates
 */
logActivity('Message goes here', 0);
```

## Log Module Call

We recommend making use of the module log to record all external API calls and requests.

This makes debugging the external API calls your modules make easier and consistent with other modules.

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
