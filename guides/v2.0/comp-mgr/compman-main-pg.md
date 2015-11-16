---
layout: default 
group: compman
subgroup: C_UseCompMan
title: Manage your components
menu_title: Manage your components
menu_node: 
menu_order: 2
github_link: comp-mgr/compman-main-pg.md
---


<h4>Contents</h4>   

*	<a href="#compman-access">Component Management options</a>
*	<a href="#compman-access-sync">Update a component</a>
*	<a href="#compman-access-enable">Enable or disable a component</a>

<h2 id="compman-access">Component Management options</h2>
To choose whether to upgrade or uninstall components:

1.	After you <a href="{{ site.gdeurl }}comp-mgr/compman-start.html">run the Component Manager</a>, a page similar to the following displays:<br><br>
	<img src="{{ site.baseurl }}common/images/cman_initial-page.png" width="750px" alt="The Component Manager page enables you to synchronize with Magento Connect to see if updates are available">
2.	You have the following options:
	<table>
	<tbody>
	<tr>
		<th>Item</th>
		<th>Meaning</th>
	</tr>
	<tr>
		<td><p>Magento Connect Account section</p></td>
		<td><p>Shows when you last synchronized with your Magento Connect account. To get the latest information about available component versions, you must synchronize with Connect.</p>
			<p>Last Sync shows the last time you synchronized and Sync Status shows whether or not you're currently synchronized.</p>
			<div class="bs-callout bs-callout-info" id="info">
  				<p>Magento Connect isn't available yet. Although you can't log in to your account, you can synchronize your components with the ones that <code>composer.json</code> knows about.</p>
 			</div>
		</td>
	</tr>
	<tr>
		<td><p>Sync button</p></td>
		<td><p>Click <strong>Sync</strong> to compare the component versions you're currently using with those available on Connect.</p></td>
	</tr>
	<tr>
		<td><p>List of components</p></td>
		<td><p>For each component, one of the following status indicators displays in the left column:</p>
			<ul><li><img src="{{ site.baseurl }}common/images/cman_comp-status-green.png" alt="A green icon means that the component is enabled and is current as of the last sync">Green, which means the component is enabled and its status was current the last time you synchronized with Connect.</li>
				<li><img src="{{ site.baseurl }}common/images/cman_comp-status-info.png" alt="An info icon means there is an update available">An update is available.</li>
				<li><img src="{{ site.baseurl }}common/images/cman_comp-status-red.png" alt="A red icon means the component is disabled">The component is disabled.</li> </ul>
				<p>Middle columns display information about the component we obtained from its Composer package.</p>
				<p>The right column displays available actions for each component. </p></td>
	</tr>
	<tr>
		<td><p>Actions</p></td>
		<td><p>Displays a list of actions available for that component type. <a href="#compman-access-types">Details about available actions</a>.</p>
			<p>The following figure shows an example.</p>
			<img src="{{ site.baseurl }}common/images/cman_actions.png" alt="You can enable, disable, or update components">
			</li>
			</ul>
	<tr>
		<td><p>Pagination</p></td>
		<td><p>Enables you to:</p>
			<p><img src="{{ site.baseurl }}common/images/cman_page_number.png" width="100px" alt="Specify number of items to display on page">Specify the number of items to display on a page.</p>
			<p><img src="{{ site.baseurl }}common/images/cman_page_move.png" width="100px" alt="Move back and forward or specify a page number">From left to right, move back one page, go to a specific page, or move forward one page.</p></td>
	</tr>
	</tbody>
	</table>

<h3 id="compman-access-types">Supported actions per type</h3>
The following table shows which actions are supported for each Magento component type.
<table>
	<col width="40%">
  	<col width="15%">
  	<col width="15%">
  	<col width="15%">
  	<col width="15%">
		<tbody>
		<tr>
			<th>Type</th>
			<th>Enable</th>
			<th>Disable</th>
			<th>Update</th>
			<th>Uninstall</th>
		</tr>
		<tr>
			<td>magento2-module</td>
			<td>Yes</td>
			<td>Yes</td>
			<td>Yes</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>magento2-language and magento2-theme</td>
			<td>No</td>
			<td>No</td>
			<td>Yes</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>magento2-library</td>
			<td>No</td>
			<td>No</td>
			<td>Yes</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>component</td>
			<td>No</td>
			<td>No</td>
			<td>Yes</td>
			<td>Yes</td>
		</tr>
		</tbody>
	</table>

<div class="bs-callout bs-callout-info" id="info">
      <ul><li>Enable and disable will be supported soon.</li>
      <li>A magento2-module has no <strong>Uninstall</strong> option if it's part of a metapackage. Currently, uninstalling a metapackage is not supported.</li></ul>
</div>
<h2 id="compman-access-sync">Update a component</h2>
To see if any of your components can be updated, click **Sync**.

<img src="{{ site.baseurl }}common/images/cman_comp-status-info.png" alt="An info icon means there is an update available"> displays in the left column of each component that you can update. 

The following figure shows an example.

<img src="{{ site.baseurl }}common/images/cman_component-needs-update.png" width="650px" alt="Example showing components that need updating">

To update the component, click **Update** from the **Actions** list. A sample follows.

<img src="{{ site.baseurl }}common/images/cman_actions_update.png" alt="Click Update from the Actions menu">

Continue with <a href="{{ site.gdeurl }}comp-mgr/compman-readiness.html">Readiness check</a>.

<h2 id="compman-endis">Enable or disable a component</h2>
To enable or disable a component, click the appropriate choice from the **Actions** list.

The following figure shows an example of disabling a component.

<img src="{{ site.baseurl }}common/images/cman_actions-disable.png" alt="Click Disable from the Actions menu">

Continue with <a href="{{ site.gdeurl }}comp-mgr/compman-readiness.html">Readiness check</a>.

<h2 id="compman-uninst">Uninstall a component</h2>
To uninstall a component, click **Uninstall** from the **Actions** list as the following figure shows.

<img src="{{ site.baseurl }}common/images/cman_uninstall1.png" alt="Uninstall a component">

Continue with <a href="{{ site.gdeurl }}comp-mgr/compman-readiness.html">Readiness check</a>.




