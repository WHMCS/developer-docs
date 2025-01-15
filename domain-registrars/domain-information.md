+++
prev = "/domain-registrars/module-functions/"
next = "/domain-registrars/availability-checks/"
title = "Domain Information"
weight = 70

+++

This function allows you to build and return an object representing a given domain.  The attributes of the object can include data including nameservers, expiry date, registrar and transfer lock status, domain contact verification status and more.

{{% notice success %}}
In WHMCS 7.6 and later, it is recommended to use the `GetDomainInformation` function in place of the individual `GetNameservers` and `GetRegistrarLock` functions in scenarios where a single API call can retrieve both nameservers and registrar lock status for best performance.
{{% /notice %}}

Note this function is only available in WHMCS 7.6.0 and later.

## Example Usage

The function expects a return of a [WHMCS Registrar Domain object](https://docs.whmcs.com/classes/7.6/WHMCS/Domain/Registrar/Domain.html).

The example below demonstrates setting all supported domain attributes at the time of writing.


```
use WHMCS\Carbon;
use WHMCS\Domain\Registrar\Domain;

function modulename_GetDomainInformation($params) {
	/**
     * Perform API call to retrieve domain information. This example assumes
     * $response is populated with an array of data returned by the Registrar's API.
     */
	$response = [];

	return (new Domain)
        ->setDomain($response['domain'])
        ->setNameservers($response['nameservers'])
        ->setRegistrationStatus($response['status'])
        ->setTransferLock($response['transferlock'])
        ->setTransferLockExpiryDate(null)
        ->setExpiryDate(Carbon::createFromFormat('Y-m-d', $response['expirydate'])) // $response['expirydate'] = YYYY-MM-DD
        ->setRestorable(false)
        ->setIdProtectionStatus($response['addons']['hasidprotect'])
        ->setDnsManagementStatus($response['addons']['hasdnsmanagement'])
        ->setEmailForwardingStatus($response['addons']['hasemailforwarding'])
        ->setIsIrtpEnabled(in_array($response['tld'], ['.com']))
        ->setIrtpOptOutStatus($response['irtp']['optoutstatus'])
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

If an error is encountered while attempting to fetch the domain information, you should throw an exception. All exceptions will be caught by WHMCS and the exception message displayed to the end user.

Method signatures for the `WHMCS\Domain\Registrar\Domain` class can be found in the
[WHMCS Class Documentation](https://docs.whmcs.com/classes/7.6/WHMCS/Domain/Registrar/Domain.html).
