---
layout: default
group:  migration
subgroup: Data migration tool
title: Install the Data Migration Tool
menu_title: Install the Data Migration Tool
menu_node: 
menu_order: 2
github_link: migration/migration-tool-install.md
redirect_from: /guides/v1.0/migration/migration-tool-install.html
---

## Install the Data Migration Tool
This section discusses how to install the Magento Data Migration Tool. You can install it from either <a href="http://packages.magento.com/#magento/data-migration-tool" target="_blank">packages.magento.com</a> or from a GitHub repository.

<div class="bs-callout bs-callout-info" id="info">
  <p>The versions of both the Data Migration Tool and the Magento 2 code must be identical (for example, 1.0.0-beta). To find the version of either package, open <code>&lt;your Magento install dir>/composer.json</code> and find the value of "version".</p>
</div>

### Install the tool from GitHub
To install the Data Migration Tool from GitHub, use the following steps:

1.	Log in to your Magento 2 server as a user with privileges to write to the Magento 2 file system or <a href="{{ site.gdeurl }}install-gde/prereq/apache-user.html#install-update-depend-user-switch">switch to the Magento file system owner</a>.
2.	Change to Magento 2 root directory.
3.	Enter the following commands in the order shown:

			composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool-ce
			composer require magento/data-migration-tool:dev-master
3.	Wait while dependencies are updated.

### Install the tool from packages.magento.com
To install the Data Migration Tool, you must update `composer.json` in the Magento root installation directory to provide the location of the Data Migration Tool package. 

The Data Migration Tool is versioned like Magento code. Before you begin, you can either:

*	Find the exact version you want at <a href="http://packages.magento.com/#magento/data-migration-tool" target="_blank">packages.magento.com</a>
*	Install the latest version using Composer <a href="https://getcomposer.org/doc/01-basic-usage.md#next-significant-release-tilde-and-caret-operators-" target="_blank">next significant release syntax</a>

To install the Data Migration Tool, you must:

1.	Decide the version of `magento/data-migration-tool` you want as discussed in the preceding section.

2.	Run the `composer config` and `composer require` commands to update `composer.json`.

To update `composer.json`:

1.	Log in to your Magento server as the <a href="{{ site.gdeurl }}install-gde/prereq/apache-user.html#install-update-depend-user-switch">switch to the Magento file system owner</a> or as a user with privileges to write to the Magento 2 file system.

2.	Go to Magento 2 root directory.

7.	Enter the following command to reference Magento packages in `composer.json`:

		composer config repositories.magento composer http://packages.magento.com

8.	Enter the following command to require the current version of the sample data package:

		composer require magento/data-migration-tool:<version>

	where `<version>` is either an exact version or next significant release syntax.

	Exact version example:

		composer require magento/data-migration-tool:0.74.0-beta4

	Next significant release example:

		composer require magento/data-migration-tool:~0.74.0-beta4

9.	Wait while dependencies are installed.

###Related topics

* <a href="{{ site.gdeurl }}migration/migration-tool-configure.html">Configure migration</a>

* <a href="{{ site.gdeurl }}migration/migration-tool-preconditions.html">Preconditions</a>