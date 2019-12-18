+++
prev = "/payment-gateways/tokenised-remote-storage"
title = "Installation & Activation"
toc = true
weight = 120

+++

To install the new module, upload it to the `/modules/gateways/` folder of your WHMCS installation.

If the module includes a callback file, that should be uploaded to the `/modules/gateways/callback/` folder.

Once uploaded, navigate to **Setup > Payment Gateways** to activate and configure the new module.

{{% notice info %}}
**Important Note** The process of activating a module detects the type of module that has been created. Therefore if you experience unexpected behaviours, please try deactivating and reactivating your module before continuing.
{{% /notice %}}

## Troubleshooting errors during activation

If you receive a blank page or error message within the **Setup > Payment Gateways** page upon uploading your new payment gateway module, this indicates there could be a syntax error within the new code.

To debug this, you can turn on error reporting.  To do this, navigate to **Setup > General Settings > Other** and check the **Display Errors** setting.

This enables PHP error reporting and should show the cause of any issues. Once resolved, remember to disable Display Errors again.
