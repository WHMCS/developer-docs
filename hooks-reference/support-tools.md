+++
title = "Support Tools"
weight = 10

+++

The following hooks are provided for Support Tools related events.

## AnnouncementAdd

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| announcementid | | |
| date | | |
| title | | |
| announcement | | |
| published | | |

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

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| announcementid | | |
| date | | |
| title | | |
| announcement | | |
| published | | |

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

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |

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

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | | |
| $updatearray | | |

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

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | | |

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

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | | |

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

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | | |
| $updatearray | | |

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

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('NetworkIssueReopen', 1, function($vars) {
    // Perform hook code here...
});
```

