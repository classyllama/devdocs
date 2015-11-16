---
layout: default
group: install_pre
subgroup: Q_Pre-installation
title: Your install or upgrade path
menu_title: Your install or upgrade path
menu_node: parent
menu_order: 1
github_link: install-gde/install/pre-install.md
redirect_from: /guides/v1.0/install-gde/install/pre-install.html
---

<div class="bs-callout bs-callout-tip">
  <p>Totally lost? Need a helping hand? Try our <a href="{{ site.gdeurl }}install-gde/install-quick-ref.html">installation quick reference (tutorial)</a> or <a href="{{ site.gdeurl }}install-gde/install-roadmap_part1.html">installation roadmap (reference)</a>.</p>
</div>

<h2 id="install-overview-audience">Your install or upgrade path</h2>
Before you start your installation, take a moment to figure out which type of user you are. It's important because the installation procedure is very different for each type:

<table>
	<!-- <col width="25%">
	<col width="65%">
	<col width="10%"> -->
	<tbody>
		<tr>
			<th>User type</th>
			<th>Description</th>
			<th>High-level installation steps</th>
			<th>Get started link</th>
		</tr>
		
	
	<tr>
		<td><p>Contributing developer</p></td>
		<td><p>Wants to contribute to the Magento codebase, highly technical, has their own Magento development server, understands Composer and GitHub.</p></td>
		<td><ol><li>Clones the Magento 2 GitHub repository.</li>
			<li>Uses Composer to update package dependencies.</li>
			<li>Installs the Magento software.</li></ol>
		<td><p><a href="{{ site.gdeurl }}install-gde/prereq/dev_install.html">Developers start here</a></p></td>
	</td>
	</tr>
	<tr>
		<td><p>System integrator</p></td>
		<td><p>Wants full control over all components installed, has access to the Magento server, highly technical.</p></td>
		<td><ol><li>Creates a Composer <em>project</em> that contains the list of components to use.</li>
			<li>Uses Composer to update package dependencies.</li>
			<li>Installs the Magento software.</li></ol>
		<td><p><a href="{{ site.gdeurl }}install-gde/prereq/integrator_install.html">System integrators start here</a></p></td>
	</td>

	</tr>
	<tr>
		<td><p>Merchant</p></td>
		<td><p>Very little technical expertise, limited if any access to the Magento server.</p></td>
		<td><ol><li>Download a compressed file that contains the Magento software.</li>
			<li>Extracts it on the Magento server or asks a network administrator or hosting provider to do so.</li>
			<li>Installs the Magento software.</li></ol>
		</td>
		<td><p><a href="{{ site.gdeurl }}install-gde/prereq/merch_install.html">Merchants start here</a></p></td>
	</tr>
	</tbody>
</table>

#### Related topics
After you finish installing the Magento software, you can:

*	<a href="{{ site.gdeurl }}comp-mgr/bk-compman-upgrade-guide.html">Manage components</a>
*	<a href="{{ site.gdeurl }}comp-mgr/bk-compman-upgrade-guide.html">Upgrade</a>

