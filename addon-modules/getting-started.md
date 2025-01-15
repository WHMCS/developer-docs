+++
next = "/addon-modules/configuration"
prev = "/addon-modules"
title = "Getting Started"
toc = true
weight = 10

+++

To get started, you need to begin by choosing a name for your module.
The module name chosen must be unique and should be all lowercase.
The name must only contain letters & numbers whilst always starting with a letter.
Underscore is the only accepted special character.
For example, valid names would be: 
    
    
**mymodulename** OR **my_module_name** OR **my_module**
    

Once you have chosen your name, you need to create a directory and module file for it.
Addon modules are found in the `/modules/addons/` directory.
Each module can be found within it's own directory **/your_module_name/**.
Then the core module file within it should be "**your_module_name**.php" to match the folder. 

We make available a sample addon module on GitHub. We recommend using this as a starting point for a custom addon module.

> https://github.com/WHMCS/sample-addon-module
