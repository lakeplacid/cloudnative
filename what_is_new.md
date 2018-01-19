---
copyright:
  years: 2017, 2018
lastupdated: "2018-01-19"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# What is new in the {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}}
{: #what-is-new}

## New as of October 2017
{: #oct-2017}

The October 2017 update of the {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}} introduced the following changes:

* A new Resources section has been added to the console, which features a brand new design.
* The console, formerly known as the Bluemix Developer console, has been renamed to the {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}}.
* Mobile and Web/Backend projects now have separate consoles.
* Starter kit projects can now leverage the exciting capabilities provided by the following {{site.data.keyword.Bluemix_notm}} services: {{site.data.keyword.objectstoragefull}}, {{site.data.keyword.mobilepushfull}}, {{site.data.keyword.cloudantfull}}, {{site.data.keyword.alertnotificationfull}}, {{site.data.keyword.appid_full}}, {{site.data.keyword.conversationfull}},  {{site.data.keyword.composeForMongoDB_full}}, {{site.data.keyword.composeForRedis_full}}, and {{site.data.keyword.composeForPostgreSQL_full}}.
* Deploying projects to {{site.data.keyword.Bluemix_notm}} is easier than ever before with seamless DevOps Toolchain integration.
* Projects can be deployed as Kubernetes containers supported by {{site.data.keyword.containerlong_notm}} or as Cloud Foundry applications.
* New Starter Kits include blank projects for Python, Java, Node.js, and Swift, which provide a bare bones application with {{site.data.keyword.Bluemix_notm}} capabilities.



## New as of June 2017
{: #june-2017}

The June 2017 update of the {{site.data.keyword.Bluemix}} {{site.data.keyword.dev_console}} introduced the following changes:

   * The Mobile starters now handle creating the required {{site.data.keyword.ibmwatson}} services and injecting your service credentials into the project.
   * The {{site.data.keyword.dev_cli_long}} was updated with new features. For more information, see [What’s included in the {{site.data.keyword.Bluemix_notm}} CLI {{site.data.keyword.dev_cli_short}} version 0.1.12 ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/06/whats-included-bluemix-cli-developer-plug-version-0-1-12/).

## New as of March 2017
{: #mar-2017}

The March 2017 update of the {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.dev_console}} introduced the following changes:

   * The {{site.data.keyword.Bluemix_notm}} Mobile dashboard is now the {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.dev_console}}.
   * Project creation is redesigned to include Web App, BFF, and Microservice server pattern types with support for Node.js, Java, and Swift.
   * Integration with the new and improved {{site.data.keyword.appid_full}} service gives authenentication for Mobile and Web projects.
   * You can now generate SDKs for your projects by using the [SDK Generator plug-in](sdk/index.html). SDK generation in the {{site.data.keyword.dev_console}} is available only for Mobile projects.
   * You can now create projects by using the [{{site.data.keyword.dev_cli_short}}](idt/index.html).


## New as of January 2017
{: #jan-2017}

The January 2017 update of the {{site.data.keyword.Bluemix_notm}} Mobile dashboard introduced the following changes:

   * As of January 31, UI Starters are deprecated. Existing projects that were created from a UI Starter can be used until 30 April 2017. For more information about migration steps and removal dates, see the [deprecation announcement blog post ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/01/bluemix-mobile-dashboard-update/).
{: deprecated}
   * You can now update your project starter type instead of deleting your project and creating a new one.
   * You can now create your project with a [Watson Conversation](tutorial_conversation.html) Code Starter.
   * Where it is supported, you can now generate an SDK for your project.
   * You can now add your existing [Compute](sdk_compute.html) instances and generate client SDKs to add to your project.


## New as of December 2016
{: #dec-2016}

The December 2016 update of the {{site.data.keyword.Bluemix_notm}} Mobile dashboard introduced the following changes:

   * You can now remove a connected service from a project so it can be deleted or reused with another project.
   * You can now add an existing service to a project.
   * You can now create or connect an existing CloudantNoSQL service as a data source when you use a Code Starter.
   * Where it is supported, you can now create or connect an existing Object Storage service as a data source for your project.
   * You can now customize the navigation design of the app that you are creating with a UI Starter.


## New as of November 2016
{: #nov-2016}

The November 2016 update of the {{site.data.keyword.Bluemix_notm}} Mobile dashboard introduced the following changes:

   * You can now generate SDK artifacts for your projects from the **Code** page.
   * Cordova is now supported for the Basic Code Starter.
   * You can now [report network events ![External link icon](../icons/launch-glyph.svg "External link icon")](/docs/services/mobileanalytics/sdk.html#network-requests){: new_window} and [monitor network requests ![External link icon](../icons/launch-glyph.svg "External link icon")](/docs/services/mobileanalytics/app-monitoring.html#monitor-network-requests){: new_window} in the **Network Requests** page of the {{site.data.keyword.mobileanalytics_short}} console.
   * You can now [export data to dashDB ![External link icon](../icons/launch-glyph.svg "External link icon")](/docs/services/mobileanalytics/app-monitoring.html#dashdb){: new_window} in the {{site.data.keyword.mobileanalytics_short}} console.


## New as of October 2016
{: #oct-2016}

The October 2016 update of the {{site.data.keyword.Bluemix_notm}} Mobile dashboard introduced the following changes:

   * You can now add {{site.data.keyword.mobilepushshort}} and Analytics capabilities to your project directly from the dashboard.
   * Code Starters are now available.
   * You can add Authentication to your projects that you created from a Code Starter.
   * Swift is now supported.


### Analytics
{: #analytics notoc}

   * Demo mode is enabled by default when you add the Analytics capability. You can toggle off demo mode to view your analytics after you run your app.


### UI Builder
{: #ui_builder notoc}

   * The **{{site.data.keyword.mobilepushshort}}** capability is now accessed from the project.
   * The **Project Settings** tab is renamed to **Settings**.
   * The **Authentication** tab is renamed to **User Access**.


### Code
{: #code notoc}

   * The generated Objective-C and Swift code for iOS now uses CocoaPods to manage dependencies, so you must install it. To install CocoaPods, run `sudo gem install cocoapods`. After CocoaPods is installed, run `pod setup` to configure it (if not configured already). Finally, run `pod install` to download and install the project dependencies prior to opening your `.xcworkspace` file in Xcode. Further details are available in the `README.md` file in the downloaded code archive. Read about [Prerequisite Developer Tools](get_code.html#prereq-dev-tools) for more information.

Check back often to stay current with new updates.
