+++
next = "/domain-registrars/module-functions/"
prev = "/domain-registrars/metadata-params/"
title = "Module Parameters"
weight = 50

+++

The module parameters are the data values passed into each registrar module function when called.

Registrar module functions all receive the same common set of parameters. These parameters provide information about the specific domain the module command is being invoked for. The parameters also contain the settings defined for the module itself.

Additional variables specific to the action being performed such as EPP code, nameservers and WHOIS contact information may be available depending upon the function being called.

| Variable | Description |
| --------- | ----------- |
| userid | The client ID who owns the domain
| domainid | The unique ID of the domain
| sld | eg. `yourdomain`
| tld | eg. `.com`
| regperiod | The registration term for the domain (1-10 years)
| eppcode | Present only for incoming domain transfer orders (Transfers only)
| **Nameservers**
| ns1 | First Nameserver (Registrations, Transfers and Nameserver Updates only)
| ns2 | Second Nameserver
| ns3 | Third Nameserver
| ns4 | Fourth Nameserver
| ns5 | Fifth Nameserver
| **Contact Information**
| firstname |
| lastname |
| fullname | First name and last name combined
| companyname |
| email |
| address1 |
| address2 |
| city |
| state | State code eg. TX
| fullstate | State name eg. Texas
| postcode | Postcode/Zip code
| countrycode | Country code eg. GB
| countryname | Country name eg. United Kingdom
| phonenumber | Phone number as the user provided it
| phonecc | Country code determined based on country
| fullphonenumber | Format: +CC.xxxxxxxxxxxx
| additionalfields | An array of additional registrant information fields and their values
| **Admin/Tech/Billing**
| adminfirstname |
| adminlastname |
| admincompanyname |
| adminemail |
| adminaddress1 |
| adminaddress2 |
| admincity |
| adminstate | State code eg. TX
| adminfullstate | State name eg. Texas
| adminpostcode | Postcode/Zip code
| admincountry | eg. GB
| adminphonenumber | Phone number as the user provided it
| adminfullphonenumber | Format: +CC.xxxxxxxxxxxx
| **Domain Addons**
| dnsmanagement | True/false for if DNS Management add-on is active
| emailforwarding | True/false for if Email Forwarding add-on is active
| idprotection | True/false for if ID Protection add-on is active
| **Premium Parameters**
| premiumEnabled | True if premium domain orders are enabled in WHMCS (Registration/Transfers only)
| premiumCost | The cost price fetched at the time of the order being placed
| **Grace/Redemption Parameters**
| isInGracePeriod | True if domain is within the renewal grace period. Available in the module renewal function only
| isInRedemptionGracePeriod | True if the domain is within the redemption grace period. Available in the module renewal function only
| **IDN Parameters**
| idnlanguage | The language code for the domain.
| domain_punycode | The Punycode version of the domain name.
| sld_punycode | The SLD with the Punycode domain name.
| tld_punycode | The TLD with the Punycode domain name.
| is_idn | Whether the domain is an IDN.
