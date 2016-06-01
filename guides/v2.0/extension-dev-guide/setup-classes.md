---
layout: default
group: extension-dev-guide
subgroup: 99_Module Development
title: Setup classes
menu_title: Setup classes
menu_order: 15
contributor_name: Classy Llama
contributor_link: http://www.classyllama.com/
github_link: extension-dev-guide/setup-classes.md
---
## {{page.menu_title}}

When installing or updating module, any schema or data setup classes contained in the module's `Setup/` directory will be executed.
Currently, there are six types of setup classes available:

*   `Setup/InstallSchema`
*   `Setup/UpgradeSchema`
*   `Setup/InstallData`
*   `Setup/UpgradeData`
*   `Setup/Recurring`
*   `Setup/Uninstall`

<div class="bs-callout bs-callout-tip">
  <p>
    Unlike Magento 1, where an install script or upgrade script is run only once and where there are often multiple upgrade scripts based
    on new versions of the module, Magento 2 now uses only one class for each type of action.
  </p>
</div>

Each setup class implements multiple interfaces that are located in `Magento\Framework\Setup\`.

{% highlight PHP %}
<?php

namespace My\Module\Setup;

use Magento\Framework\Setup\InstallSchemaInterface;
use Magento\Framework\Setup\ModuleContextInterface;
use Magento\Framework\Setup\SchemaSetupInterface;

class InstallSchema implements InstallSchemaInterface {

    public function install(SchemaSetupInterface $setup, ModuleContextInterface $context)
    ...
{% endhighlight %}

Each interface for each setup class type has one single method, which is the primary action that the class performs.
All of these methods also have a second required parameter called `ModuleContextInterface`. This parameter is used to get
the current version of the module which will be used to determine which parts of the setup classes need to be run.

## When the classes are executed

*   When installing a module for the first time, any install and upgrade classes that exist in the `Setup/` folder will run.
*   When a module is already installed but is being upgraded to a newer version, the two types of upgrade classes will run.
    *   Any version-specific code is handled inside the class.
*   The recurring class runs every time you run the `setup:upgrade` command.
*   The uninstall class runs only when you run the `module:uninstall` command.

## Types of setup scripts

### Install Schema and Upgrade Schema

Changes to database schema, such as creating new tables or modifying existing tables, are handled by InstallSchema and UpgradeSchema.

Examples of usage:

*   Creating a new table
*   Adding new fields to existing tables
*   Modifying table or column attributes

{% highlight PHP %}
<?php

namespace My\Module\Setup;

use Magento\Framework\Setup\UpgradeSchemaInterface;
use Magento\Framework\Setup\ModuleContextInterface;
use Magento\Framework\Setup\SchemaSetupInterface;

class UpgradeSchema implements UpgradeSchemaInterface {

    public function upgrade(SchemaSetupInterface $setup, ModuleContextInterface $context)
    {
        $setup->startSetup();
        if (version_compare($context->getVersion(), '0.1.0', '<')) {
            /**
             * Add new column to table
             */
            $setup->getConnection()
                ->addColumn(
                    $setup->getTable('existing_table'),
                    'new_column',
                    [
                        'type' => \Magento\Framework\DB\Ddl\Table::TYPE_TEXT,
                        'length' => 255,
                        'nullable' => true,
                        'default' => null,
                        'comment' => 'New Column'
                    ]
                );
        }
        $setup->endSetup();
    }
}
{% endhighlight %}

### Install Data and Upgrade Data

InstallData and UpgradeData is used to insert or update data in your existing tables.

Examples of usage:

*   Creating new records in a table, such as new CMS pages or blocks
*   Adding or updating EAV attributes

{% highlight PHP %}
<?php

namespace My\Module\Setup;

use Magento\Framework\Setup\InstallDataInterface;
use Magento\Framework\Setup\ModuleContextInterface;
use Magento\Framework\Setup\ModuleDataSetupInterface;

class InstallData implements InstallDataInterface {

    public function install(ModuleDataSetupInterface $setup, ModuleContextInterface $context)
    {
        $setup->startSetup();

        $setup->getConnection()->insert(
            $setup->getTable('existing_table'),
            [
                'column_1' => 'one',
                'column_2' => 'two'
            ]
        );

        $setup->endSetup();
    }
}
{% endhighlight %}

### Recurring

The `Recurring` class allows the same setup instructions to be run after any module setup or upgrade.
Recurring scripts implement `InstallSchemaInterface` rather than its own unique interface.
An example of a recurring class can be found in Magento's Indexer module (`Magento\Indexer\Setup\Recurring`).
This class looks for all indexers configured in Magento and either marks the an index for updating if the indexer has been modified
or adds any new indexers to the `indexer_state` table.

### Uninstall

Uninstall classes are used to cleanup and remove database schema that is no longer necessary after a module has been uninstalled.

{% highlight PHP %}
<?php

namespace My\Module\Setup;

use Magento\Framework\Setup\UninstallInterface;
use Magento\Framework\Setup\ModuleContextInterface;
use Magento\Framework\Setup\SchemaSetupInterface;

class InstallData implements InstallDataInterface {

    public function uninstall(SchemaSetupInterface $setup, ModuleContextInterface $context)
    {
        $setup->startSetup();
        $tableName = $setup->getTable('table_to_delete');
        if ($tableName) {
            $setup->getConnection()->dropTable($tableName);
        }
        $setup->endSetup();
    }
}
{% endhighlight %}