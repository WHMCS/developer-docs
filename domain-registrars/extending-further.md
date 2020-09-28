+++
next = "/domain-registrars/hooks/"
prev = "/domain-registrars/tld-pricing-sync/"
title = "Extending Further"
weight = 120

+++

## Custom Functions

Custom functions allow you to define extra operations that can be performed using the module. The custom functions can perform actions, or define extra client area pages/output. Permissions can be granted for who can use each custom function, be it just clients, just admins, or both.

The convention for custom function names follow the same as any other function of a module. It must begin with `yourmodulename_`, and then the custom function name.

The easiest way to show this is with an example. So let's take an example of a Push Function that will use a template, `pushdomain.tpl`:

```
function yourmodulename_push($params) {

    $domainid = $params['domainid'];
    $sld = $params['sld'];
    $tld = $params['tld'];

    return array(
        'templatefile' => 'pushdomain',
        'breadcrumb' => array(
            'clientarea.php?action=domaindetails&domainid='.$domainid.'&modop=custom&a=push' => 'Push Domain',
        ),
        'vars' => array(
            'var1' => 'valuehere',
            'var2' => 'anothervaluehere',
        ),
    );
}
```

The above shows how to define custom functions, use the parameters passed, and return an array response. The response can either be a simple empty array/error for an action function, or a complex array return like the above to define an extra client area page for extra domain management functionality.

Now we need to allow clients to use this. The following function defines that clients are allowed to invoke the push function, and will add a menu option to the **Domain Actions** dropdown within the client area for it.

```
function yourmodulename_ClientAreaCustomButtonArray() {
    return array(
        "Push Domain" => "push",
    );
}
```

The key value of the array is what is displayed to admins/clients on the button or menu options for the commands, and the value is the custom function name excluding the `modulename_` prefix.

If you want to provide clients with a custom button or way to invoke a function, then this can be done as follows within a `.tpl` file described in the previous Client Area Output section:

```
<form method="post" action="clientarea.php?action=domaindetails">
<input type="hidden" name="domainid" value="{$domainid}" />
<input type="hidden" name="modop" value="custom" />
<input type="hidden" name="a" value="reboot" />
<input type="submit" value="Reboot VPS Server" />
</form>
```

## IDN Domains

If you wish to support registration and management of IDN domain names via a registrar module, the domain object can be
used to access various parameters related to the domain. A domain name is considered IDN if it contains at least one character that is in a language-specific script or alphabet. IDN is supported for second level domain names but not top level at this time.

The following options are available:

```
$domainObj = $params['original']['domainObj'];
$fullDomainUnicode = $domainObj->toPunycode(); // The full domain name as stored in the database.
$isIdn = $domainObj->isIdn(); // Returns true if domain is an IDN domain.
$fullDomainPunycode = $domainObj->toUnicode(); // The full domain name in Unicode.
$secondLevelUnicode = $domainObj->getUnicodeSecondLevel(); // The domain name (excluding TLD) in Unicode.
$secondLevelPunycode = $domainObj->getPunycodeSecondLevel(); // The domain name (excluding TLD) converted to Punycode.
$tld = $domainObj->getTopLevel(); // The Top Level Domain for the given domain.
```
