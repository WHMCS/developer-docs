+++
prev = "/domain-registrars/module-functions/"
next = "/domain-registrars/availability-checks/"
title = "Domain Information"
weight = 63

+++

This function allows you to build an object representing a given domain and all attributes relating to it.  These attributes can include things such as nameservers, registrar lock, transfer lock, expiry date, domain contact verification status and more.

{{% notice success %}}
In WHMCS 7.6 and later, it is recommended to use the `GetDomainInformation` function in place of the individual `GetNameservers` and `GetRegistrarLock` functions in scenarios where a single API call can retrieve both values for optimal performance and speed.
{{% /notice %}}

Note this function is only available in WHMCS 7.6.0 and later.

## Example Usage

The function expects a return of a [WHMCS Registrar Domain object](https://docs.whmcs.com/classes/7.4/WHMCS/Domain/Registrar/Domain_ns.html).

The example below demonstrates setting all supported attributes at the time of writing.


```
use WHMCS\Domain\Registrar\Domain;

function modulename_GetDomainInformation($params) {
	// Perform API call to retrieve domain information
    // This example assumes the $response variable is populated with an array
	$response = [];

	return (new Domain)
        ->setDomain($response['domain'])
        ->setNameservers($response['nameservers'])
        ->setRegistrationStatus($response['status'])
        ->setTransferLock($response['transferlock'])
        ->setTransferLockExpiryDate(null)
        ->setExpiryDate($response['expirydate'])
        ->setRestorable(false)
        ->setIdProtectionStatus($response['addons']['hasidprotect'])
        ->getDnsManagementStatus($response['addons']['hasdnsmanagement'])
        ->setEmailForwardingStatus($response['addons']['hasemailforwarding'])
        ->setIsIrtpEnabled(in_array($response['tld'], ['.com']))
        ->setIrtpOptOutStatus($response['irtp']['outoutstatus'])
        ->setIrtpTransferLock($response['irtp']['lockstatus'])
        ->IrtpTransferLockExpiryDate($irtpTransferLockExpiryDate)
        ->setDomainContactChangePending($response['status']['contactpending'])
        ->setPendingSuspension($response['status']['pendingsuspend'])
        ->setDomainContactChangeExpiryDate($response['status']['expires'])
        ->setRegistrantEmailAddress($response['registrant']['email'])
        ->setIrtpVerificationTriggerFields(
            [
                'Registrant' => [
                    'First Name',
                    'Last Name',
                    'Organization Name',
                    'Email',
                ],
            ]
        );
}
```

If any error is encountered while attempting to fetch the domain information, you can throw any exception type. This will be caught and the exception message displayed to the end user.

Method signatures for the `WHMCS\Domain\Registrar\Domain` class can be found in the
[WHMCS Class Documention](https://docs.whmcs.com/classes/7.4/WHMCS/Domain/Registrar/Domain_ns.html).