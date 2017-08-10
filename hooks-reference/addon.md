+++
title = "Addon"
weight = 10

+++

The following hooks are provided for Addon related events.

## AddonActivated

Executes when an addon is activated.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | The addon ID (tblhostingaddons) |
| userid | int |  |
| serviceid | int |  |
| addonid | int | The predefined addon ID (tbladdons) |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonActivated', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonActivation

Executes when a product addon is being automatically activated as part of an invoice payment or order acceptance. Runs following the welcome email having been sent.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | The addon ID (tblhostingaddons) |
| userid | int |  |
| serviceid | int |  |
| addonid | int | The predefined addon ID (tbladdons) |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonActivation', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonAdd

Executes when an addon is added to a product/service.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | The addon ID (tblhostingaddons) |
| userid | int |  |
| serviceid | int |  |
| addonid | int | The predefined addon ID (tbladdons) |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonAdd', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonCancelled

Executes when an addon is cancelled.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | The addon ID (tblhostingaddons) |
| userid | int |  |
| serviceid | int |  |
| addonid | int | The predefined addon ID (tbladdons) |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonCancelled', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonConfig

Executes as an addon is being displayed.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | The id of the created addon (tbladdons). |

#### Response

an array of key -> value pairs to be displayed on the addon configuration.

#### Example Code

```
<?php

add_hook('AddonConfig', 1, function($vars) {
    return [
        'Additional Field 1' => '<input type="text" name="additionalFieldOne" class="form-control input-150" />',
        'Additional Field 2' => '<input type="text" name="additionalFieldTwo" class="form-control input-150" />',
    ];
});
```

## AddonConfigSave

Executes as an addon is being saved.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | The id of the created addon (tbladdons). |

#### Response

No response supported

#### Example Code

```
<?php

//Obtain the values defined in the AddonConfig hook point and save them as required
add_hook('AddonConfigSave', 1, function($vars) {
    $addonId = $vars['id'];
    $additionalFieldOne = App::getFromRequest('additionalFieldOne');
    $additionalFieldTwo = App::getFromRequest('additionalFieldTwo');

    //Save the data here
});
```

## AddonDeleted

Executes when an addon is being deleted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | the id of the addon being removed. tblhostingaddons |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonDeleted', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonEdit

Executes when an addon is modified or updated.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | The addon ID (tblhostingaddons) |
| userid | int |  |
| serviceid | int |  |
| addonid | int | The predefined addon ID (tbladdons) |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonEdit', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonSuspended

Executes when an addon is suspended.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | The addon ID (tblhostingaddons) |
| userid | int |  |
| serviceid | int |  |
| addonid | int | The predefined addon ID (tbladdons) |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonSuspended', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonTerminated

Executes when an addon is terminated.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | The addon ID (tblhostingaddons) |
| userid | int |  |
| serviceid | int |  |
| addonid | int | The predefined addon ID (tbladdons) |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonTerminated', 1, function($vars) {
    // Perform hook code here...
});
```

## AddonUnsuspended

Executes when an addon is unsuspended.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | The addon ID (tblhostingaddons) |
| userid | int |  |
| serviceid | int |  |
| addonid | int | The predefined addon ID (tbladdons) |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AddonUnsuspended', 1, function($vars) {
    // Perform hook code here...
});
```

## LicensingAddonReissue

Executes as a license is being reissued

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| licenseid | int |  |
| serviceid | int |  |
| addon_id | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('LicensingAddonReissue', 1, function($vars) {
    // Perform hook code here...
});
```

## LicensingAddonVerify

Executes as a license remote check is being completed

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| licenseid | int |  |
| serviceid | int |  |
| xmlresponse | string | The current XML response |

#### Response

Return key value pairs of additional items to be returned with the response.

#### Example Code

```
<?php

add_hook('LicensingAddonVerify', 1, function($vars) {
    return [
        'myExtraVariable' => 'Yes',
        'myOtherVariable' => 'Sure',
    ];
});
```

