---
copyright:

  years: 2018

lastupdated: "2018-01-29"

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}  

# {{site.data.keyword.dev_cli_notm}} Overview
{: #developercli}

The (formerly referred to as the Bluemix CLI Developer Plug-in) is a command line driven approach for creating, developing, and deploying applications, ideal for developers that would like to use command line control to develop end-to-end web, mobile, and microservice applications.
{: shortdesc}


## Setting up the {{site.data.keyword.dev_cli_notm}}
{: #add-cli}


### Prerequisites
{: #prereq}

You must obtain a few prerequisites to fully explore and properly utilize the {{site.data.keyword.dev_cli_short}}, as it is highly extensible for leveraging complementary technologies.

1. Obtain an [{{site.data.keyword.Bluemix_notm}}](https://www.bluemix.net) ID.

Note: If you are using Microsoft Windows&trade;, you must use Windows 10 or later.

Note: You must use the stable channel for Docker, with a minimum version of 1.13.1


### Installing
{: #installation}

To install the tool, you can run the relevant command to invoke our installer. This will install dependencies as well, such as the IBM Cloud CLI, Kubernetes, Helm, and Docker. To install these, use these installation steps:

**Mac and Linux:**<br>

```
curl -sL https://ibm.biz/idt-installer | bash
```
{: codeblock}


**Windows 10:**<br>

```
Set-ExecutionPolicy Unrestricted; iex(New-Object Net.WebClient).DownloadString('http://ibm.biz/idt-win-installer')
```
{: codeblock}

Validate successful plug-in installation by running the following command:  

```
bx dev
```
{: codeblock}

#### Configure Your Environment
{: #configure-environment}

1. Connect to an API endpoint in your [{{site.data.keyword.Bluemix_notm}} region](/docs/overview/cf.html#ov_intro_reg). For example, enter the following command to connect to the {{site.data.keyword.Bluemix_notm}} US South region:

	```
	bx api https://api.ng.bluemix.net
	```
	{: codeblock}

2. Log in to {{site.data.keyword.Bluemix_notm}} by providing your IBMid and password:

	```
	bx login
	```
	{: codeblock}

	**Note:** If your credentials are rejected, you might be using a Federated ID. Follow these steps to authenticate by using a Federated ID.

	1. Log in to [{{site.data.keyword.iamshort}} ![External link icon](/docs/icons/launch-glyph.svg "External link icon")](https://www.bluemix.net/iam/#/apikeys){: new_window}.
	2. Select **Create API key**.
		* Enter an apiKey name and description
	3. Download your apiKey.
	4. Open the file and copy the value from the `apiKey` field.
	5. Log in using the following command:

		```
		bx login --apikey <value>
		```
		{: codeblock}

3. Set your ORG and SPACE using:

	```
	bx target -o <value> -s <value>
	```
	{: codeblock}



## Learn More
{: #learn}

Now that you have your {{site.data.keyword.dev_cli_short}} CLI installed, you can learn how to be effctive with this powerful tool.  The following are sugested next steps:
- [Getting Started with IDT CLI](getting_started.html)
- [IDT (bx dev) commands](commands.html)
- [Developer Tools for VS Code](vscode.html)
- [Developer Tools for Jetbrains IDEs](jetbrains.html)
- [Troubleshooting](../troubleshoot.html)

There are also several tutorials shown in the left nav that show how to create cloud native apps using {{site.data.keyword.dev_cli_short}} CLI.


## APPENDIX
{: #appendix}

The following resources can be helpful when developing Cloud Native apps with the IBM Developer Tools CLI:

**Main links**

- [IBM Cloud Developer Tools main landing page](https://www.ibm.com/cloud/cli) - Main product page for IDT CLI
- [IBM Developer Tools Installer](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools) - Public GitHub repo with detailed installation instructions
- [IBM Cloud App Service](https://console.bluemix.net/developer/appservice) - IBM Cloud console page which is a companion to the IDT tools to create and manage cloud native apps
- [IBM Cloud Tech's Slack - #developer-tools channel](https://ibm-cloud-tech.slack.com) - Discuss IDT tools, get answers, suggest ideas, and more
	- [Request team access](https://slack-invite-ibm-cloud-tech.mybluemix.net/)

**Language focused**

- [Node,js on IBM Cloud](https://developer.ibm.com/node/cloud/)
- [Spring @ IBM Cloud](https://developer.ibm.com/java/spring/)
- [Swift @ IBM](https://developer.ibm.com/swift)

**Blogs and Tutorials**

- [Deploying to IBM Cloud private with IBM Cloud Developer Tools CLI](https://www.ibm.com/blogs/bluemix/2017/09/deploying-ibm-cloud-private-ibm-cloud-developer-tools-cli/)
- [Enable existing projects for IBM Cloud with the IBM Cloud Developer Tools CLI](https://www.ibm.com/blogs/bluemix/2017/09/enable-existing-projects-ibm-cloud-ibm-cloud-developer-tools-cli/)
- [Deploying to Kubernetes on IBM Cloud with the IBM Cloud Developer Tools CLI](https://www.ibm.com/blogs/bluemix/2017/09/deploying-kubernetes-ibm-cloud-ibm-cloud-developer-tools-cli/)
