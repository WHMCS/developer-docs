+++
next = "/payment-gateways/third-party-gateway"
prev = "/payment-gateways/meta-data-params"
title = "Configuration"
toc = true
weight = 30

+++

## Configuration

A payment gateway module can have user configurable settings that are set via the WHMCS admin interface.

These are defined in the `yourmodulename_config` function of the module which is a required function for all gateway modules.

This function should define both the display name for the module (for backwards compatibility), and any settings that the gateway module requires.

### Defining configuration fields

The supported configuration field types include the following:

* Text
* Password
* Yes/No Checkboxes
* Dropdown Menus
* Radio Buttons
* Text Areas

Below is an example config function that demonstrates each type of field and the parameters available for them.

```
function yourmodulename_config()
{
    return array(
        // the friendly display name for a payment gateway should be
        // defined here for backwards compatibility
        'FriendlyName' => array(
            'Type' => 'System',
            'Value' => 'Sample Third Party Payment Gateway Module',
        ),
        // a text field type allows for single line text input
        'accountID' => array(
            'FriendlyName' => 'Account ID',
            'Type' => 'text',
            'Size' => '25',
            'Default' => '',
            'Description' => 'Enter your account ID here',
        ),
        // a password field type allows for masked text input
        'secretKey' => array(
            'FriendlyName' => 'Secret Key',
            'Type' => 'password',
            'Size' => '25',
            'Default' => '',
            'Description' => 'Enter secret key here',
        ),
        // the yesno field type displays a single checkbox option
        'testMode' => array(
            'FriendlyName' => 'Test Mode',
            'Type' => 'yesno',
            'Description' => 'Tick to enable test mode',
        ),
        // the dropdown field type renders a select menu of options
        'dropdownField' => array(
            'FriendlyName' => 'Dropdown Field',
            'Type' => 'dropdown',
            'Options' => array(
                'option1' => 'Display Value 1',
                'option2' => 'Second Option',
                'option3' => 'Another Option',
            ),
            'Description' => 'Choose one',
        ),
        // the radio field type displays a series of radio button options
        'radioField' => array(
            'FriendlyName' => 'Radio Field',
            'Type' => 'radio',
            'Options' => 'First Option,Second Option,Third Option',
            'Description' => 'Choose your option!',
        ),
        // the textarea field type allows for multi-line text input
        'textareaField' => array(
            'FriendlyName' => 'Textarea Field',
            'Type' => 'textarea',
            'Rows' => '3',
            'Cols' => '60',
            'Description' => 'Freeform multi-line text input field',
        ),
    );
}
```

Each field includes:

1. **System Name** - a normalized name by which the field can be referenced in module code
2. **Friendly Name** - a human readable friendly display name for the field
3. **Type** - The type of field. The available field types are "text", "password", "yesno" (checkbox), "dropdown", "radio" and "textarea"
4. Any settings specific to that field type such as Size, Rows, Cols, Default Value and Description

Any fields defined here will be available along with their configured values in all gateway module functions in the $params array.

{{% notice info %}}
Avoid common names like currency, invoiceid, etc, as these may conflict with the standard variables.
{{% /notice %}}

## Build your gateway

Now it's time to integrate your payment gateway provider.

For a Third Party Gateway, [click here][third-party]. For a Merchant Gateway, [click here][merchant-gateway].

[third-party]: /payment-gateways/third-party-gateway "Third Party Gateway"
[merchant-gateway]: /payment-gateways/merchant-gateway "Merchant Gateway"
