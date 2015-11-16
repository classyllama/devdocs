---
layout: default
group: extension-dev-guide
subgroup: 3_Build
title: Enable a module
menu_title: Enable a module
menu_order: 9
github_link: extension-dev-guide/enable-module.md

---
##{{page.menu_title}}

After you have built the module and are ready to enable it in your Magento environment, do the following: 
 
<ol>
<li>Disable the cache under <code>System->Cache Management</code>.</li>
<li>Enter the following at the command line:

		<pre>bin/magento module:enable --clear-static-content Module_Name
    	bin/magento setup:upgrade
    	</pre>

where <code>Module_Name</code> is the name of the module you are enabling.

</li>

<li>Check under <code>Stores->Configuration->Advanced->Advanced</code> that the module is present.</li>
 </ol>

<div class="bs-callout bs-callout-info" id="info">
<span class="glyphicon-class">
  <p>The general order of operations for <code>setup:upgrade</code> is:</p>

<ol>
<li><strong>Schema install/upgrade.</strong></li>
	<li><strong>Schema post-upgrade</strong>&#8212; handles any additional updates. These recurring upgrades occur independently and regardless of any changes to the schema.</li>
	<li><strong>Data install/upgrade</strong> &#8212; installs the data. Taken from <code>setup/InstallData.php</code>.</li>
</ol>
</span>
</div>



##Disable a module

To disable a module, enter the following at the command line:

    bin/magento module:disable --clear-static-content Module_Name


For more on enabling and disabling modules, see [enable or disable modules]({{ site.gdeurl}}install-gde/install/cli/install-cli-subcommands-enable.html#instgde-cli-subcommands-enable-disable).