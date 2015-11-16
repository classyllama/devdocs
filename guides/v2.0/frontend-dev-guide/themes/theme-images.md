---
layout: default
group: fedg
subgroup: A_Themes
title: Configure images properties for a theme
menu_title: Configure images properties for a theme
menu_order: 4
github_link: frontend-dev-guide/themes/theme-images.md
---

## What's in this topic ##

The properties of product images used on the storefront are stored in the `view.xml` configuration file. This topic provides all details about what properties are available and how to configure them.

<h2 id="view_xml_structure">Configure image properties in view.xml</h2>

The conventional location of `view.xml` for a theme is:
{% raw %}
	app/design/frontend/<Vendor>/<theme>/etc/view.xml
{% endraw %}

For example, here is the path to `view.xml` of the Magento Blank theme: <a href="{{site.mage2000url}}app/design/frontend/Magento/blank/etc/view.xml" target="_blank"><code>app/design/frontend/Magento/blank/etc/view.xml</code></a>.

In `view.xml`, image properties are configured in the scope of `<images module="Magento_Catalog">` element:

{% highlight xml %}
<images module="Magento_Catalog">
...
<images/>
{% endhighlight xml %}

Image properties are configured for each image type defined by the `id` and `type` attributes of the `<image>` element:

{% highlight xml %}
<images module="Magento_Catalog">
	<image id="unique_image_id" type="image_type">
	...
	</image>
<images/>
{% endhighlight xml %}

<br>
The following table describes the attributes in detail:
<table>
  <tbody>
    <tr>
      <th>Attribute</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
    <tr>
      <td>
        <code>
          id
        </code>
      </td>
      <td>
        string
      </td>
      <td>
        <p>Image identifier. Unique in the scope of theme.</p> <p>
Can have any value, but in out-of-the- box Magento themes <code>id</code>'s are meaningful and describe the location of an image.</p><p> For example, the <code>id</code> value for images of cross-sell products displayed in a shopping card is <code>cart_cross_sell_products</code>.</p> <p><code>id</code>'s are used in <code>.phtml</code> templates for defining the type and properties of images displayed in each particular location on a particular page.</p>
      </td>
    </tr>
    <tr>
      <td>
        <code>
          type
        </code>
      </td>
      <td>
        string
      </td>
      <td>
        The type of the images defined by the specified <code>id</code>. Allowed values:
<ul>
<li><code>image</code> - corresponds to the Base Image role in the Magento Admin</li>
<li><code>small_image</code> - corresponds to the Small Image role in the Magento Admin</li>
<li><code>swatch_image</code> - corresponds to the Swatch Image role in the Magento Admin</li>
<li><code>swatch_thumb</code> - corresponds to the Swatch Image role in the Magento Admin. </li>
<li><code>thumbnail</code> - corresponds to the Thumbnail Image role in the Magento Admin</li>
</ul>

The following picture illustrates how image roles for product images are specified in the Magento Admin:
<img src="{{site.baseurl}}common/images/fdg_theme_bck.png" alt="Setting image role in Magento Admin">

      </td>
    </tr>
</tbody>
</table>

Image properties are defined by the corresponding elements, for example:

{% highlight xml %}
<images module="Magento_Catalog">
    <image id="unique_image_id" type="image">
        <width>100</width> <!-- Image width in px --> 
        <height>100</height> <!-- Image height in px -->
    </image>
</images>
{% endhighlight xml %}

<br>

The following table contains the list of all properties which can be configured:
<table>
  <tbody>
    <tr>
      <th>Element</th>
      <th>Type</th>
      <th>Description</th>
      <th>Required</th>
    </tr>
    <tr>
      <td>
        <code>
          width
        </code>
      </td>
      <td>
integer
      </td>
      <td>
 Image width in pixels.
      </td>
      <td>
        Optional
      </td>
    </tr>
    <tr>
      <td>
        <code>
          height
        </code>
      </td>
      <td>
integer
      </td>
      <td>
 Image height in pixels.
      </td>
      <td>
        Optional
      </td>
    </tr>
    <tr>
      <td>
        <code>
          constrain
        </code>
      </td>
      <td>
boolean
      </td>
      <td>
If set to <code>true</code>, images that are smaller than required by the configuration, are not enlarged. Default value: <code>true</code>.
      </td>
      <td>
        Optional
      </td>
    </tr>
    <tr>
      <td>
        <code>
          aspect_ratio
        </code>
      </td>
      <td>
boolean
      </td>
      <td>
If set to <code>true</code>, proportions of images are not changed even if required by the configuration. Default value: <code>true</code>.
      </td>
      <td>
        Optional
      </td>
    </tr>
    <tr>
      <td>
        <code>
          frame
        </code>
      </td>
      <td>
boolean
      </td>
      <td>
If set to <code>true</code>, images are not cropped. Default value: <code>true</code>. Applied only if <code>aspect_ratio</code> is set to <code>true</code>.
      </td>
      <td>
        Optional
      </td>
    </tr>
    <tr>
      <td>
        <code>
          transparency
        </code>
      </td>
      <td>
boolean
      </td>
      <td>
If set to <code>true</code>, the transparent background of images is saved. If is set to <code>false</code>, images have the white background (by default). You can set the color for the background using the <code>background</code> parameter. Default value: <code>true</code>.
      </td>
      <td>
        Optional
      </td>
    </tr>
    <tr>
      <td>
        <code>
          background
        </code>
      </td>
      <td>
array
      </td>
      <td>
The color for the images background. Not applied to images with transparency, if <code>transparency</code> is set to <code>true</code>.
      </td>
      <td>
        Optional
      </td>
    </tr>
</tbody>
</table>

####Catalog image resize command

The Magento_Catalog module provides Magento CLI command for resize all product images. Resized images are stored in `/pub/media/catalog/product/cache` directory.

The catalog:images:resize command has no options or arguments. 

Basic syntax:

`bin/magento catalog:images:resize`
