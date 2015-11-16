---
layout: default
group: install2
subgroup: Getting Started
title: Installation overview
menu_title: Installation overview
menu_node: 
menu_order: 1
github_link: install-gde/bk-install-guide.md
redirect_from: /guides/v1.0/install-gde/bk-install-guide.html
---

<!-- This topic is referred to from Magento 2 code! Don't change the URL without informing engineering! -->
<!-- Referring file: README.md owned by core -->


<h2>Magento software installation</h2>
Hi, we're glad you're among the 240,000 merchants worldwide who put their trust in our eCommerce software. We've gathered some information to help you get started with Magento and with your Magento installation. 

We have some resources here to help get you started using the eCommerce platform of the future&mdash;Magento 2.

It’s what we do.

<h2>New to Magento installation? Need some help?</h2> 
If you're not sure about the following, you probably need a little help before you get started with your installation:

*	Is the Magento software <a href="{{ site.gdeurl }}install-gde/basics/basics_magento-installed.html">installed already</a>?
*	What's a <a href="{{ site.gdeurl }}install-gde/basics/basics_login.html">terminal, command prompt, or Secure Shell (ssh)</a>?
*	Where's my <a href="{{ site.gdeurl }}install-gde/basics/basics_login.html">Magento server</a> and how do I access it?
*	What's <a href="{{ site.gdeurl }}install-gde/basics/basics_software.html">PHP</a>?
*	What's <a href="{{ site.gdeurl }}install-gde/basics/basics_software.html">Apache</a>?
*	What's <a href="{{ site.gdeurl }}install-gde/basics/basics_software.html">MySQL</a>?

<h2 id="install-verify-prereq">Step 1: Verify your prerequisites</h2>

Use the following table to verify you have the correct prerequisites to install the Magento software.

<table>
	<tbody>
		<tr>
			<th>Prerequisite</th>
			<th>How to check</th>
			<th>For more information</th>
		</tr>
	<tr>
		<td><p>Apache 2.2 or 2.4</p></td>
		<td><p>Ubuntu: <code>apache2 -v</code></p>
		<p>CentOS: <code>httpd -v</code></p></td>
		<td><p><a href="{{ site.gdeurl }}install-gde/prereq/apache.html">Apache</a></p>
			<p>(Don't forget to <a href="{{ site.gdeurl }}install-gde/prereq/apache.html#apache-help-rewrite">enable rewrites and <code>.htaccess</code></a>!)</p></td>
	</tr>
	<tr>
		<td><p>PHP 5.6.x or 5.5.x (PHP 5.4 is not supported)</p>
			<p>See <a href="{{ site.gdeurl }}release-notes/known-issues.html#known-devrc-php">Known issue with certain PHP versions</a></p></td>
		<td><p><code>php -v</code></p></td>
		<td><a href="{{ site.gdeurl }}install-gde/prereq/php-ubuntu.html">PHP Ubuntu</a><br><a href="{{ site.gdeurl }}install-gde/prereq/php-centos.html">PHP CentOS</a></td>
	</tr>
	<tr><td><p>MySQL 5.6.x</p></td>
	<td><p><code>mysql -u &lt;root user name> -p</code></p></td>
	<td><a href="{{ site.gdeurl }}install-gde/prereq/mysql.html">MySQL</a></td>
	</tr>
</tbody>
</table>

<h2>Step 2: Prepare to install</h2>
After verifying your prerequisites, determine <a href="{{ site.gdeurl }}install-gde/install/pre-install.html">how to get started</a> with your installation.

<h2>Step 3: Install and verify the installation</h2>

1.	Install Magento:
	*	<a href="{{ site.gdeurl }}install-gde/install/install-web.html">Install the Magento software using the Setup Wizard</a>
	*	<a href="{{ site.gdeurl }}install-gde/install/cli/install-cli.html">Install Magento software using the command line</a>
2.	<a href="{{ site.gdeurl }}install-gde/install/verify.html">Verify the installation</a>

<h2>Useful information</h2>
At any time during your installation, take advantage of our <a href="{{ site.gdeurl }}install-gde/install-quick-ref.html">installation quick reference (tutorial)</a> or <a href="{{ site.gdeurl }}install-gde/install-roadmap_part1.html">installation roadmap (reference)</a>. They're really easy to use; the tutorial walks you through a sample installation. The roadmap provides links to common tasks throughout the guide.

Use the links on the left side of the page to navigate topics in each part of the installation.

<h2>Required server permissions</h2>
UNIX systems require `root` privileges to install and configure software like a web server, PHP, and so on. If you need to install this software, make sure you have `root` access.

You should *not* install the Magento software in the web server docroot as the `root` user because the web server might not be able to interact with those files. 

You'll also need `root` privileges to create the <a href="{{ site.gdeurl }}install-gde/prereq/apache-user.html">Magento file system owner</a> and add that owner to the web server's group. You'll use the Magento file system owner to run any commands from the command line and to set up the Magento cron job, which schedules tasks for you.
