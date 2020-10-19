+++
prev = "/domain-registrars/premium-domains/"
next = "/domain-registrars/tld-pricing-sync/"
title = "Transfer Policy (IRTP) Management"
weight = 100

+++

The Inter Registry Transfer Policy, (also commonly referred to as IRTP), states that any time a material change is made to a domain's registrant, organization or email address, a new Change of Registrant process should be triggered.

In WHMCS 7.6 and later, registrar modules can incorporate support for Transfer Policy related messaging as follows.

## WHOIS Contact Verification

WHMCS supports display of informational banners and messaging when contact verification is required, either due to a newly registered domain or a change in WHOIS contact information being requested.

For these informational alerts to be displayed, the appropriate attributes need to be set via the `GetDomainInformation` method within a registrar module.

A description of the methods used in WHOIS Contact Verification messaging are provided below:

| Function | Type | Description |
| --------- | ----------- | ------ |
| setIsIrtpEnabled | Boolean | Must be set to true to enable Transfer Policy functionality. |
| setIrtpOptOutStatus | Boolean | True or false depending on the current opt-out status for the Inter Registry Transfer Policy (optional) |
| setIrtpTransferLock | Boolean | True or false depending on the current IRTP Transfer Lock status for the given domain (optional) |
| setIrtpTransferLockExpiryDate | Date | The expiry date of the transfer lock (optional) |
| setDomainContactChangePending | Boolean | True if a WHOIS Contact Verification process is in progress |
| setPendingSuspension | Boolean | True if failure to complete the current WHOIS Contact Verification process will result in domain suspension (typically for new registrations) |
| setDomainContactChangeExpiryDate | Date | The date by which the current WHOIS Contact Verification process must be completed by |
| setIrtpVerificationTriggerFields | Array | The fields of WHOIS that when changed will trigger a new WHOIS Contact Verification process |

### Example Usage

```
use WHMCS\Carbon;
use WHMCS\Domain\Registrar\Domain;

function modulename_GetDomainInformation(array $params) {
	// Perform API call to retrieve domain information

	return (new Domain)
        ->setIsIrtpEnabled(true)
        ->setIrtpOptOutStatus(false)
        ->setIrtpTransferLock(true)
        ->setIrtpTransferLockExpiryDate(Carbon::createFromFormat('Y-m-d', '2019-06-15'))
        ->setDomainContactChangePending(true)
        ->setPendingSuspension(true)
        ->setDomainContactChangeExpiryDate(Carbon::createFromFormat('Y-m-d', '2018-08-20'))
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

Other attributes relating to a domain are supported. More information on these can be found in the [Domain Information](/domain-registrars/domain-information/) documentation.

## Resend Contact Verification Email

If supported by a registrar API, the `ResendIRTPVerificationEmail` function can be defined within a registrar module to allow end users and administrators to request the WHOIS Contact Verification emails be resent.

The standard registrar module parameters are passed to this function, errors are supported using the standard array based return as in other registrar module functions.

### Example Usage

```
function modulename_ResendIRTPVerificationEmail(array $params) {
	// Perform API call to initiate resending of the IRTP Verification Email
	$success = true;
	$errorMessage = '';

	if ($success) {
		return ['success' => true];
	} else {
		return ['error' => $errorMessage];
	}
}
```
