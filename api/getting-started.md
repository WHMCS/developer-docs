+++
next = "/api/authentication/"
prev = "/api"
title = "Getting Started"
toc = true
weight = 10

+++

Two methods are provided for accessing the API.

## External API

The External API should be used when the system making the call is hosted remotely from the WHMCS installation.

This API accepts `POST` requests to the API endpoint located at:

> https://www.yourdomain.com/path/to/whmcs/includes/api.php

## Internal API

The Internal API should be used when making API calls from within the WHMCS system.

For instance from modules, hooks, or other custom code local to the WHMCS installation.
