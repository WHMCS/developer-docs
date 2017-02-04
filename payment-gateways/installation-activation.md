+++
next = "/payment-gateways/errors"
prev = "/payment-gateways/tokenised-remote-storage"
title = "Installation & Activation"
toc = true
weight = 70

+++

To install the new module, upload it to the `/modules/gateways/` folder.
Once uploaded, go to **Setup** > **Payment Gateways** to activate.
If there is a callback file, that should be uploaded to the `/modules/gateways/callback/` folder.
**Important**: It is important that the gateway is not activated until step 1 is complete for either the third party or merchant gateway modules.
This is because the type of module created is stored in the database upon activation.
