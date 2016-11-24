+++
next = "/next/path"
prev = "/prev/path"
title = "Module Parameters"
weight = 50

+++

The module parameters are the data values passed into each registrar module function when called.

Every registrar module function receives the same parameters. These parameters provide information about the specific domain the module command is being invoked for. The parameters also contain the settings from the registrar itself. Additional variables specific to the action may be available depending upon the function running.

| Variable | Description |
| --------- | ----------- |
| configvalues | the settings defined in your modules configuration function - names as defined
| domainid | the unique ID of the domain (Database Field: tbldomains.id)
| sld | the second level domain being managed (eg. google)
| tld | the top level domain being managed (eg. .com)
| regperiod | the registration period requested for the domain
| nsX | the nameserver values for a domain - where X = 1 to 5
