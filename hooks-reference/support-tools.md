+++
title = "Support Tools"
weight = 10

+++

The following hooks are provided for Support Tools related events.

## AnnouncementAdd

Executes as an announcement is being added.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| announcementid | int |  |
| date | string |  |
| title | string |  |
| announcement | string |  |
| published | bool |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AnnouncementAdd', 1, function($vars) {
    // Perform hook code here...
});
```

## AnnouncementEdit

Executes as an announcement is being added.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| announcementid | int |  |
| date | string |  |
| title | string |  |
| announcement | string |  |
| published | bool |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AnnouncementEdit', 1, function($vars) {
    // Perform hook code here...
});
```

## FileDownload

Executes when a file is being downloaded.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| No input parameters for this hook point. |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('FileDownload', 1, function($vars) {
    // Perform hook code here...
});
```

## NetworkIssueAdd

Executes as a network issue is being crated.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int |  |
| startdate | string |  |
| enddate | string |  |
| title | string |  |
| description | string |  |
| type | string |  |
| server | int |  |
| affecting | string |  |
| priority | string |  |
| status | string |  |
| lastupdate | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('NetworkIssueAdd', 1, function($vars) {
    // Perform hook code here...
});
```

## NetworkIssueClose

Executes as a network issue is being resolved.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('NetworkIssueClose', 1, function($vars) {
    // Perform hook code here...
});
```

## NetworkIssueDelete

Executes as a network issue is being deleted.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('NetworkIssueDelete', 1, function($vars) {
    // Perform hook code here...
});
```

## NetworkIssueEdit

Executes as a network issue is being edited.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int |  |
| startdate | string |  |
| enddate | string |  |
| title | string |  |
| description | string |  |
| type | string |  |
| server | int |  |
| affecting | string |  |
| priority | string |  |
| status | string |  |
| lastupdate | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('NetworkIssueEdit', 1, function($vars) {
    // Perform hook code here...
});
```

## NetworkIssueReopen

Executes as a network issue is being re-opened.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('NetworkIssueReopen', 1, function($vars) {
    // Perform hook code here...
});
```

