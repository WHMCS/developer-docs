+++
next = "/oauth/api/"
prev = "/oauth/introduction"
title = "Authentication Workflow"
toc = true
weight = 10

+++

Here’s how the process typically works.

1. User presses a “Connect to WHMCS” button inside your app.
2. Your app redirects the user to the WHMCS installation.
3. The user logs into WHMCS and authorizes your app to access their WHMCS account using the permissions your app has requested.
4. After the user approves your app, they’ll be redirected back to your app with an authorization code.
5. Your app can then use this authorization code to make a request for a re-usable access token which can be used to make subsequent requests to the WHMCS API. This takes place in the background and should not be visible to end users.

All OAuth requests require a valid API Client Credential Identifier and Secret. Credentials for OpenID connect can be created via the OpenID Connect admin interface. For Single Sign-On credentials, we recommend using the Provisioning Module API for Application Links. Alternatively, you can provision and manage OAuth Client Credentials via the WHMCS API.
