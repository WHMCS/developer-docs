+++
prev = "/advanced/widgets/"
title = "JSON File"
weight = 70

+++

When developing modules for WHMCS, you can place a `whmcs.json` file in the module's root directory to provide additional meta information that WHMCS will use in display of the **Apps & Integrations** pages. 

A sample `whmcs.json` is provided below:

```
{
  "schema": "1.0",
  "type": "whmcs-notifications",
  "name": "email",
  "license": "proprietary",
  "category": "notifications",
  "description": {
    "name": "Email",
    "tagline": "Configure rule based notifications delivered by email.",
    "long": "Setup advanced rule based notifications for events and triggers that matter to you and receive those notifications to one or more email addresses.",
    "features": [
      "Setup rule based events and triggers",
      "Receive notifications by email"
    ]
  },
  "logo": {
    "filename": "logo.png"
  },
  "support": {
    "homepage": "https:\/\/www.whmcs.com\/", 
    "learn_more": "https:\/\/www.whmcs.com\/tour", 
    "email": "support@whmcs.com", 
    "support_url": "https:\/\/support.whmcs.com\/",
    "docs_url": "https:\/\/docs.whmcs.com\/Notifications"
  },
  "authors": [
    {
      "name": "WHMCS",
      "homepage": "https:\/\/www.whmcs.com\/"
    }
  ]
}
```

A brief description of each parameter and what it is used for can be found below:

| Parameter            | Usage                                                                                                                                                        |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| schema               | The current version of the whmcs.json file structure.                                                                                                        |
| type                 | The type of module. The available types are: `whmcs-addons`, `whmcs-fraud`, `whmcs-gateways`, `whmcs-registrars`, `whmcs-security`, `whmcs-servers`, `whmcs-notifications` |
| name                 | The name of the module.                                                                                                                                      |
| license              | Which type of license the module is released under.                                                                                                          |
| category             | The category in which the module should be organized.                                                                                                        |
| description          | Additional parameters that describe the module.                                                                                                              |
| description.name     | The display name of the module.                                                                                                                              |
| description.tagline  | A short summary description of the module.                                                                                                                   |
| description.long     | A more detailed description of the module.                                                                                                                   |
| description.features | An array containing each feature that will display as a list of bullet points.                                                                               |
| logo.filename        | The file that should be used as the module logo (500 pixel recommended width.                                                                                                             |
| support.homepage     | A URL that links to the website homepage for the module.                                                                                                        |
| support.learn_more     | A URL that links to a page with additional information about the module.                                                                                                        |
| support.email     | The email address to contact to get support for the module                                                                                                        |
| support.support_url     | A URL that links to a support desk or resources for the module.                                                                                                        |
| support.docs_url     | A URL that links to the documentation for the module.                                                                                                        |
| authors              | An array of objects that represent each author and a link to their website.                                                                                  |
| author name          | The name of the module author.                                                                                                                               |
| author homepage      | A URL that links to the module author's website.                                                                                                             |

The logo.png file used for a module should not exceed **500** pixels in width. An example placeholder logo for reference can be found below:

 <img src="../module-image-placeholder.png" alt="Module Image Placeholder" />
