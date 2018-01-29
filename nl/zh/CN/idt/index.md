---

copyright:
  years: 2017
lastupdated: "2017-11-02"

---
{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}  

# {{site.data.keyword.dev_cli_short}}
{: #developercli}	

{{site.data.keyword.dev_cli_long}} 提供了可扩展的命令驱动方法，通过使用 `dev` 插件创建、开发和部署 Web 项目。对于想要在开发端到端微服务应用程序时使用命令行控件的开发者来说是理想的选择。

{: shortdesc}

{{site.data.keyword.dev_cli_notm}} 使用两个容器，便于构建和测试应用程序。第一个容器是工具容器，包含用于构建和测试应用程序所必需的实用程序。此容器的 Docker 文件通过 [`dockerfile-tools`](#command-parameters) 参数定义。您可以将其视为一个开发容器，因为它包含通常用于开发特定运行时的工具。

第二个容器是运行容器。此容器的形式适合部署在如 {{site.data.keyword.Bluemix}} 等产品中使用。因此，会定义一个入口点，用于启动应用程序。选择通过 {{site.data.keyword.dev_cli_short}} 运行应用程序时，会使用此容器。此容器的 Docker 文件通过 [`dockerfile-run`](#run-parameters) 参数定义。


## 添加 {{site.data.keyword.dev_cli_notm}}
{: #add-cli}


### 先决条件
{: #prereq}

因为 {{site.data.keyword.dev_cli_short}} 具有很高的可扩展性，支持利用更多补充技术，所以您必须满足一些先决条件，才可以完全开发并正确利用其功能。

<!--1. Install the [Cloud Foundry CLI ![External link icon](../icons/launch-glyph.svg "External link icon")](https://github.com/cloudfoundry/cli#getting-started "External link icon").-->

1. 安装 [{{site.data.keyword.Bluemix}} CLI ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](http://clis.ng.bluemix.net/ui/home.html "外部链接图标")。

2. 获取 [{{site.data.keyword.Bluemix_notm}}](https://www.bluemix.net) 标识。

3. 如果计划在本地运行和调试应用程序，那么还必须安装 [Docker ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://www.docker.com/get-docker "外部链接图标")。


### 开始之前
{: #before-install}

1. 连接到您 [{{site.data.keyword.Bluemix_notm}} 区域](/docs/overview/whatisbluemix.html#ov_intro_reg)中的 API 端点。例如，输入以下命令以连接到 {{site.data.keyword.Bluemix_notm}} 美国南部区域：

	```
	bx api https://api.ng.bluemix.net
	```
	{: codeblock}
	
2. 通过提供 IBM 标识和密码来登录到 {{site.data.keyword.Bluemix_notm}}：

	```
	bx login
	```
	{: codeblock}
	
	**注：**如果凭证被拒绝，那么使用的可能是联合标识。执行以下步骤以使用联合标识进行认证。
	
	<!-- 
	POINT TO IBM CLOUD CLI LOG IN DOCUMENTATION !!!
	
	This link does not work in production yet --> 
	
	1. 登录到 [{{site.data.keyword.iamshort}} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://www.bluemix.net/iam/#/apikeys "外部链接图标"){: new_window}。
	2. 选择**创建 API 键**。
		* 输入 apiKey 名称和描述
	3. 下载 apiKey。
	4. 打开文件并从 `apiKey` 字段复制值。
	5. 使用以下命令登录：
	 
		```
		bx login --apikey <value>
		```
		{: codeblock}


### 安装
{: #installation}

1. 通过运行以下命令安装 [{{site.data.keyword.dev_cli_short}} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](/docs/cli/reference/bluemix_cli/index.html#install_plug-in "外部链接图标"){: new_window}：
 
	```
	bx plugin install dev
	```
	{: codeblock}

2. 	通过运行以下命令验证插件安装是否成功：  
 
	```
	bx dev
	```
	{: codeblock}


