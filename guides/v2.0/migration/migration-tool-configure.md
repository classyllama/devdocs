---
layout: default
group:  migration
subgroup: Data migration tool
title: Configure migration
menu_title: Configure migration
menu_node: 
menu_order: 3
github_link: migration/migration-tool-configure.md
redirect_from: /guides/v1.0/migration/migration-tool-configure.html
---

#### Contents
*	<a href="#migration-configure-over">Overview of data migration tool configuration</a>
*	<a href="#migration-configure">Configuring the migration</a>
*	<a href="#migration-config">Work with configuration and mapping files</a>

<h2 id="migration-configure-over">Overview of data migration tool configuration</h2>
After you install the data migration tool, the following directories contain mapping and configuration files:

*	`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/ce-to-ce`: Configuration and scripts for migrating from Magento 1 CE to Magento 2 CE
*	`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/ce-to-ee`: Configuration and scripts for migrating from Magento 1 CE to Magento 2 EE
*	`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/ee-to-ee`: Configuration and scripts for migrating from Magento 1 EE to Magento 2 EE

Each of the preceding directories contains subdirectories for each supported version.

<h2 id="migration-configure">Configuring the migration</h2>
Before you migrate any data, you must create a `config.xml` configuration file from the provided sample.

To create a configuration file:

1.	Log in to your Magento server as, or switch to, the <a href="{{ site.gdeurl }}nstall-gde/prereq/apache-user.html">Magento file system owner</a>.
2.	Change to the following directory:

		`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
3.	Enter the following command to create a `config.xml` from the provided sample:

		cp config.xml.dist config.xml

4.	Open `config.xml` in a text editor.
4.	Specify the following at minimum:

{% highlight xml %}
<source version="1.9.1">
    <database host="localhost" name="magento1" user="root"/>
</source>
<destination version="2.0.0.0">
    <database host="localhost" name="magento2" user="root"/>
</destination>
{% endhighlight %}

Optional parameters:

*	Database user password: `password=<password>`
*	Table prefix: `<source_prefix>`, `<dest_prefix>`

For example, if your database owner's user name is `root` with password `pass` and you use the prefix `magento1` in your Magento 1 database, use the following in `config.xml`:

{% highlight xml %}
<source version="1.9.1">
    <database host="localhost" name="magento1" user="root" password="pass"/>
</source>
<destination version="2.0.0.0">
    <database host="localhost" name="magento2" user="root"/>
</destination>
<options>
    <source_prefix>magento1</source_prefix>
</options>
{% endhighlight %}

When you're finished, save your changes to `config.xml` and exit the text editor.

<h2 id="migration-config">Work with configuration and mapping files</h2>
The Data Migration Tool uses *mapping files* to enable you to perform custom database mapping between your Magento 1 and Magento 2 databases, including:

*	Changing table names
*	Changing field names
*	Ignoring tables or fields
*	Adapt transferring data of a field to Magento 2 format

Mapping files for supported Magento versions are located in subdirectories of `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`

To use the mapping files:

1.	Rename or copy them to remove the `.dist` extension.
2.	Edit them using the schema located in `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`.
3.	Then change config.xml in `<options>` node with the new name of the file.

The `<your Magento 2 install dir>/vendor/magento/data-migration-tool/<ce or ee version>/etc` directory contains the following configuration files:

Even though you will be working with `map.xml.dist` file most of the time, the following table discusses each mapping and other files.

<table>
<tbody>
	<tr>
		<th>Mapping file name</th>
		<th>Description</th>
	</tr>
<tr>
	<td>class-map.xml.dist</td>
	<td>Dictionary of class mappings between Magento 1 and Magento 2</td>
</tr>
<tr>
	<td>config.xml.dist</td>
	<td>Main configuration file that specifies the Magento 1 and Magento 2 database configurations, step configuration, and links to mapping files</td>
</tr>
<tr>
	<td><em>EE only</em>. customer-attr-document-groups.xml.dist</td>
	<td>List of tables used in the custom customer attributes step.</td>
</tr>
<tr>
	<td><em>EE only</em>. customer-attr-map.xml.dist</td>
	<td>Map file that is used in Custom Customer Attributes Step.</td>
</tr>
<tr>
	<td>deltalog.xml.dist</td>
	<td>Contains the list of tables required for database routines setup.</td>
</tr>
<tr>
	<td>eav-attribute-groups.xml.dist</td>
	<td>Contains list of attributes that are used in Eav Step.</td>
</tr>
<tr>
	<td>eav-document-groups.xml.dist</td>
	<td>Contains list of tables that are used in Eav Step.</td>
</tr>
<tr>
	<td>log-document-groups.xml.dist</td>
	<td>Contains list of tables that are used in Log Step.</td>
</tr>
<tr>
	<td>map-eav.xml.dist</td>
	<td>Map file that is used in EAV Step.</td>
</tr>
<tr>
	<td>map-log.xml.dist</td>
	<td>Log mapping file.</td>
</tr>
<tr>
	<td><em>EE only</em>. map-sales.xml.dist</td>
	<td>Map file that is used in SalesOrder step.</td>
</tr>
<tr>
	<td>map.xml.dist</td>
	<td>Mapping file required for the map step.</td>
</tr>
<tr>
	<td>settings.xml.dist</td>
	<td>Setting migration configuration file that specifies rules required for migrating the <code>core_config_data</code> table.</td>
</tr>

<tr>
	<td>customer-attribute-groups.xml</td>
	<td>Contains list of attributes that are used in Customer Attributes Step.</td>
</tr>

<tr>
	<td>customer-document-groups.xml</td>
	<td>Contains list of tables that are used in Customer Attributes Step.</td>
</tr>

<tr>
	<td>map-customer.xml</td>
	<td>Map file that is used in Customer Attributes Step.</td>
</tr>

<tr>
	<td>order-grids-document-groups.xml</td>
	<td>Contains list of tables that are used in OrderGrids Step.</td>
</tr>

</tbody>
</table>

You can refer to <a href="{{ site.gdeurl }}migration/migration-tool-internal-spec.html"> Data Migration Tool Internal Specification</a> for more details.

#### Next step
<a href="{{ site.gdeurl }}migration/migration-migrate-settings.html">Migrate using data migration tool</a>