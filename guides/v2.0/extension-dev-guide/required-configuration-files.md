---
layout: default
group: extension-dev-guide
subgroup: 3_Build
title: Define your configuration files
menu_title: Define your configuration files
menu_order: 3
github_link: extension-dev-guide/required-configuration-files.md
redirect_from: 
  - /guides/v1.0/extension-dev-guide/template_create_req_config_files.html
  - /guides/v2.0/extension-dev-guide/template_create_req_config_files.html
---

##{{page.menu_title}}


Each Magento 2 module has its own set of configuration files, gathered into the module&#8217;s `etc/` folder.  




<div class="bs-callout bs-callout-info" id="info">
	<span class="glyphicon-class">
  	<p>Unlike Magento 1, there is no monolithic configuration file in Magento 2. </p>
  </span>
</div>


##Use /etc for your configuration files  

Magento 2 looks for configuration information for each module in that module&#8217;s `etc` folder. Depending on the needs of your module, you might have the following configuration files at the top level of your module&#8217;s `etc` folder:

* acl.xml
* config.xml
* di.xml
* module.xml
* webapi.xml


<div class="bs-callout bs-callout-info" id="info">
	<span class="glyphicon-class">
  		<p>Additions you make to those configuration files are applied <em>globally</em> to your module.</p>
  </span>
 </div>

In addition to those files, a Magento 2 module also has nested configuration folders in the `etc` folder for any required administration html, frontend, API REST, or API SOAP specific configuration. Additions you make to files in these folders override the settings in the global configuration files for the respective functionality only. That is, if you add a `config.xml` file to `etc/frontend`, the settings you make in that file overrides the settings in `etc/config.xml` __only for frontend__ functionality.


* &lt;YourModule>/etc/adminhtml/
* &lt;YourModule>/etc/frontend/
* &lt;YourModule>/etc/webapi_rest/
* &lt;YourModule>/etc/webapi_soap/



###Configuration files


* Configuration files that are in the top level of that module&#8217;s `etc` folder are global to that module.
* Configuration files placed in subfolders (adminhtml, frontend, webapi_rest, webapi_soap) apply only to those respective functional areas.



###Tailor your configuration files for what your module does


The exact set of configuration files required for your module depends on what your new module does. The required configuration files depend on how you plan to use the module: will the module be manifested on the storefront UI, or in the Magento Admin panel, or as a backend extension that makes a service call? Or all of the above. For example, if your module performs a function in the Admin, you should add any necessary configuration files for those functions to `etc/adminhtml/`, like:

* <code>&lt;YourModule>/etc/adminhtml/di.xml</code>
* <code>&lt;YourModule>/etc/adminhtml/routes.xml</code>

Similarly, if your module changes the UI, you should add the needed configuration files to `~/etc/frontend/`. For example:

* <code>&lt;YourModule>/etc/frontend/.xml</code>
* <code>&lt;YourModule>/etc/frontend/page_types.xml</code>

If the module is a service that may call an API, or does some other work that is not manifested in the UI you should add any needed configuration files in the REST and/or SOAP webapi configuration folders, like this:

* <code>&lt;YourModule>/etc/webapi_rest/di.xml</code>
* <code>&lt;YourModule>/etc/webapi_soap/di.xml</code>

Keep in mind that you may be able to handle your module&#8217;s configuration solely with configuration files at the top level of your module&#8217;s `etc` folder, but the nested folder is a useful way to keep the configuration neatly compartmentalized.


<!-- <div class="bs-callout bs-callout-info" id="info">

  <p>To look at a sample module that uses these config files, go to
</p>



</div> -->





##Next

[Component registration](component-registration.html)


