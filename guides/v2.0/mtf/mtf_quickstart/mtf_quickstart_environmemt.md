---
layout: default
group: mtf-guide
subgroup: C_Quickstart
title: Quick start with the Magento Testing Framework
menu_title: Prepare environment for test run
menu_order: 2
github_link: mtf/mtf_quickstart/mtf_quickstart_environmemt.md
redirect_from: /guides/v1.0/mtf/mtf_quickstart/mtf_quickstart_environmemt.html
---
<h2 id="mtf_quickstart_config">Prepare environment for test run</h2>

* TOC
{:toc}

### Run the Selenium Server {#mtf_quickstart_env_selenium}
The Selenium Server will drive a browser to execute your tests.
You can download the Selenium Server from [Selenium project website](http://www.seleniumhq.org/download/).

<div class="bs-callout bs-callout-warning">
    <p>Install <a href="https://help.ubuntu.com/community/Java">Java</a> to work with Selenium.</p>
</div>


Specific versions of the Selenium Server are compatible with specific versions of browsers. <a href="http://docs.seleniumhq.org/about/platforms.jsp">Read more about compatibility of browser version and Selenium server version.</a>

Enter in terminal:

    java -jar <path_to_selenium_directory>/selenium-server.jar

### Run tests on non default browser {#mtf_quickstart_env_selenium-non-def}

If the Selenium Server does not work directly with your browser, find the corresponding [WebDriver][].

In `config.xml` <a href="{{site.gdeurl}}mtf/mtf_quickstart/mtf_quickstart_config.html#mtf_quickstart_config_configxml_browser"> set browser that MTF will use for tests</a>.

Run the Selenium Server with an additional argument.

Example for Google Chrome:

    java -jar <path_to_selenium_directory>/selenium-server.jar -Dwebdriver.chrome.driver=<path_to_chrome_driver>/chromedriver.exe

### Run generator {#mtf_quickstart_env_generator}

Generator generates fixtures, repositories and page objects. Once MTF is initialized, all classes will be pre-generated to facilitate creating and running the tests.

Enter in terminal:

    cd <magento2>/dev/tests/functional/utils
    php generate.php

<h2 id="mtf_install_pre">Next Steps</h2>
<a href="{{ site.gdeurl }}mtf/mtf_quickstart/mtf_quickstart_config.html">&lt;&lt; Adjust configuration </a> | <a href="{{ site.gdeurl }}mtf/mtf_quickstart/mtf_quickstart_runtest.html"> Test run &gt;&gt;</a>


[WebDriver]: http://docs.seleniumhq.org/about/platforms.jsp
