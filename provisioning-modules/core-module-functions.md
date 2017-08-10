+++
prev = "/provisioning-modules/module-parameters"
next = "/provisioning-modules/single-sign-on"
title = "Core Module Functions"
toc = true
weight = 40

+++

The core module functions are **Create**, **Suspend**, **Unsuspend**, **Terminate**, **Renew**, **ChangePassword** and **ChangePackage**.

These 7 functions all operate in a similar manner. They can run both manually and automatically.
Each expected to return either a success or error response.

## Response Handling <a id="response-handling"></a>

Each of these functions after running actions must either return a success or error.

For a successful result the code must actually return the word "_success_" to end the function.
When WHMCS receives "_success_" it knows the function completed and continues on that basis.

Should the function fail, the return should be a user understandable error message, as it will display to staff users.

## Action Events <a id="action-events"></a>

When a function is successful, there are various actions that run as follows:

* **CreateAccount** - Changes status to Active + Sends Product Welcome Email
* **SuspendAccount** - Changes status to Suspended
* **UnsuspendAccount** - Changes status to Active
* **TerminateAccount** - Changes status to Terminated
* **ChangePassword** - Updates password in database

Besides the above actions, admin users receive a confirmation of functions completing, or errors in the case of failure.
Functions invoked through automation, such as payment of a new order, that notification can be via email.
In the case of ChangePassword, any errors returned are also displayed to client users.
