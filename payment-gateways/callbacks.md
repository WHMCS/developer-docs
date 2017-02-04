+++
next = "/payment-gateways/3d-secure"
prev = "/payment-gateways/merchant-gateway"
title = "Callback Files"
toc = true
weight = 40

+++

If a gateway provider supports notifying when a payment is successful, WHMCS uses a callback file to receive those.
A callback will process the response and apply a payment as required.
An included sample callback file is in the dev kit for this purpose named **callback.php**.

1. Rename it to match the gateway module.
2. Modify the variables within it, as per the comments in the code.
3. Modify it to match the variables that the specific gateway returns.

## Helper Functions <a id="helper-functions"></a>

Included in the sample file are a number of helper functions.

`$GATEWAY = getGatewayVariables(‘yourgatewayname’);`

This function can be used to retrieve the configuration data for a module as specified in the **_config** array.
For example, it might be needed to get a gateway username or secret key to validate a callback.

`$invoiceid = checkCbInvoiceID($invoiceid, $GATEWAY[‘name’]);`

Use this function can to check that the invoice ID received back is valid.
Pass the $invoiceid and the gateway name into the function.
If the invoice number is valid, the script will continue executing.
Otherwise, the script will halt and an appropriate gateway log entry created.

`checkCbTransID($transid);`

Use this function can to check for any existing transactions for a given transaction ID.
This protects against duplicate callbacks.
If the transaction ID is already in the database, the callback script execution will halt.

`logTransaction($GATEWAY[‘name’], $_POST, "Successful");`

Use this function can to create a gateway log entry.
The first variable needs to be the name of the gateway module.
The second should be an array of data, such as the **$_POST** or **$_REQUEST** super globals.
The last variable should be the result or status to show in the log.
