+++
next = "/domain-registrars/domain-syncing/"
prev = "/domain-registrars/config-options/"
title = "Function Index"
weight = 30

+++

The following is an index of all prescribed supported functions for a registrar module.

Your registrar module should only define the functions that your module supports.

Remember, all functions should have the prefix `yourmodulename_` and then the function name.

| Parameter | Description |
| --------- | ----------- |
| RegisterDomain | Called when the registration of a new domain is initiated within WHMCS. |
| TransferDomain | Called when a domain transfer request is initiated within WHMCS. |
| RenewDomain | Called when a request to renew a domain is initiated within WHMCS. |
| GetDomainInformation | Called when a domain is viewed within WHMCS. Recommended instead of GetNameservers and GetRegistrarLock in WHMCS 7.6 and later. |
| GetEmailForwarding | Called when Email Forwarding is displayed within WHMCS. |
| SaveEmailForwarding | Called when changes to Email Forwarding are submitted. |
| GetNameservers | Called when a domain is viewed within WHMCS. It can return up to 5 nameservers that are set for the domain. |
| SaveNameservers | Called when a change is submitted for a domains nameservers. |
| GetRegistrarLock | Called when a domains details are viewed within WHMCS. It should return the current lock status of a domain. |
| SaveRegistrarLock | Called when the lock status setting is toggled within WHMCS. |
| GetContactDetails | Called when the WHOIS information is displayed within WHMCS. |
| SaveContactDetails | Called when revised WHOIS information is submitted. |
| ResendIRTPVerificationEmail | Called when a request is made to resend the IRTP contact verification emails. |
| GetDNS | Called when the DNS Host Records are requested to be viewed within WHMCS. |
| SaveDNS | Called when any changes to DNS Host Records information is submitted. |
| IDProtectToggle | Called when the ID Protection setting is toggled on or off. |
| GetEPPCode | Called when the EPP Code is requested for a transfer out. |
| ReleaseDomain | Called when a domain release is requested (eg. UK IPSTag Changes). |
| RegisterNameserver | Called when a child nameserver registration request comes from WHMCS. |
| ModifyNameserver | Called when a child nameserver modification request comes from WHMCS. |
| DeleteNameserver | Called when a child nameserver deletion request comes from WHMCS. |
| RequestDelete | Called when a domain deletion request comes from WHMCS. |
| ClientArea | Used to define module specific client area output. It accepts a return of HTML for display on the domain details page of the client area. Output via a template file within the module folder named "clientarea.tpl" is also possible. This function is discussed in more detail later on in the docs. |
| ClientAreaCustomButtonArray | Used to define custom functions that the module supports. Customers can invoke and run these from the client area. The functions can perform actions or product page output in the client area. Example usages for this are to provide domain management pages, bandwidth reporting pages, etc... |
| ClientAreaAllowedFunctions | Like the above, used to define custom functions. These are functions that customers can invoke, but are not shown as buttons by default. (i.e. custom client area output will invoke them). |
| Sync | Called when a domain name's expiry date and status change at registry level is requested for propagation into WHMCS. (i.e by the Domain Synchronization feature). |
| TransferSync | Called when the status of a domain transfer at registry level is requested for propagation into WHMCS. (i.e by the Domain Synchronization feature). |
| GetTldPricing | Called when the importation and synchronising of TLD pricing, into WHMCS, from a registrar is requested. (i.e by the Registrar TLD & Pricing Sync Utility). |
