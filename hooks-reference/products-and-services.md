+++
title = "Products and Services"
weight = 10

+++

The following hooks are provided for Products and Services related events.

## AfterProductUpgrade

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| upgradeid | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterProductUpgrade', 1, function($vars) {
    // Perform hook code here...
});
```

## ProductDelete

Executes a product is being deleted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| pid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ProductDelete', 1, function($vars) {
    // Perform hook code here...
});
```

## ProductEdit

Executes as a Product is being edited.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| pid | int | The id of the product being saved. |
| type | string |  |
| gid | int | The group id the product belongs to |
| name | string |  |
| description | string |  |
| welcomeemail | int | The id of the welcome email |
| showdomainoptions | bool |  |
| stockcontrol | bool |  |
| qty | int |  |
| tax | bool |  |
| is_featured | bool |  |
| hidden | bool |  |
| retired | bool |  |
| paytype | string |  |
| allowqty | bool |  |
| recurringcycles | int |  |
| autoterminatedays | int |  |
| autoterminateemail | int |  |
| proratabilling | bool |  |
| proratadate | int |  |
| proratachargenextmonth | int |  |
| servertype | string |  |
| servergroup | int |  |
| autosetup | string |  |
| configoptionsupgrade | bool |  |
| upgradeemail | int |  |
| freedomain | string |  |
| freedomainpaymentterms | string |  |
| freedomaintlds | string |  |
| affiliatepaytype | string |  |
| affiliatepayamount | float |  |
| affiliateonetime | bool |  |
| subdomain | string |  |
| overagesenabled | bool |  |
| overagesdisklimit | int |  |
| overagesbwlimit | int |  |
| overagesdiskprice | float |  |
| overagesbwprice | float |  |
| ondemandrenewalconfigurationoverride | string |  |
| ondemandrenewalsenabled | int |  |
| ondemandrenewalperiodmonthly | int |  |
| ondemandrenewalperiodquarterly | int |  |
| ondemandrenewalperiodsemiannually | int |  |
| ondemandrenewalperiodannually | int |  |
| ondemandrenewalperiodbiennially | int |  |
| ondemandrenewalperiodtriennially | int |  |
| configoptionX | string|int|float|bool|mixed | X is 1 to 24 |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ProductEdit', 1, function($vars) {
    // Perform hook code here...
});
```

## ServerAdd

Executes as a server is created

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| serverid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ServerAdd', 1, function($vars) {
    // Perform hook code here...
});
```

## ServerDelete

Executes as a server is being deleted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| serverid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ServerDelete', 1, function($vars) {
    // Perform hook code here...
});
```

## ServerEdit

Executes as a server is being edited.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| serverid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ServerEdit', 1, function($vars) {
    // Perform hook code here...
});
```

