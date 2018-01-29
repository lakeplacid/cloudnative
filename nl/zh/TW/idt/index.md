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

{{site.data.keyword.dev_cli_long}} 提供一種可延伸的指令驅動方式，以使用 `dev` 外掛程式來建立、開發及部署 Web 專案。最適合想要使用指令行控制開發端對端微服務應用程式的開發人員。

{: shortdesc}

{{site.data.keyword.dev_cli_notm}} 使用兩個容器來協助建置及測試應用程式。第一個是 tools 容器，內含建置及測試應用程式的必要公用程式。此容器的 Dockerfile 是透過 [`dockerfile-tools`](#command-parameters) 參數所定義。您可以將它視為開發容器，因為它包含的工具一般適用於開發特定運行環境。

第二個容器是 run 容器。例如，此容器的形式適用於部署在 {{site.data.keyword.Bluemix}} 中使用。因此，會定義一個啟動應用程式用的進入點。當您選擇透過 {{site.data.keyword.dev_cli_short}} 來執行應用程式時，它會使用此容器。此容器的 Dockerfile 是透過 [`dockerfile-run`](#run-parameters) 參數所定義。


## 新增 {{site.data.keyword.dev_cli_notm}}
{: #add-cli}


### 必要條件
{: #prereq}

您必須取得一些必要條件，才能完整地探索及適當地利用 {{site.data.keyword.dev_cli_short}}，因為它可高度延伸，可讓您運用其他增補技術。

<!--1. Install the [Cloud Foundry CLI ![External link icon](../icons/launch-glyph.svg "External link icon")](https://github.com/cloudfoundry/cli#getting-started "External link icon").-->

1. 安裝 [{{site.data.keyword.Bluemix}} CLI ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](http://clis.ng.bluemix.net/ui/home.html "外部鏈結圖示")。

2. 取得 [{{site.data.keyword.Bluemix_notm}}](https://www.bluemix.net) ID。

3. 如果您打算在本端執行及除錯應用程式，則也必須安裝 [Docker ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://www.docker.com/get-docker "外部鏈結圖示")。


### 開始之前
{: #before-install}

1. 連接至 [{{site.data.keyword.Bluemix_notm}} 地區](/docs/overview/whatisbluemix.html#ov_intro_reg)中的 API 端點。例如，輸入下列指令以連接至 {{site.data.keyword.Bluemix_notm}} 美國南部地區：

	```
	bx api https://api.ng.bluemix.net
	```
	{: codeblock}
	
2. 提供 IBM ID 及密碼，以登入 {{site.data.keyword.Bluemix_notm}}：

	```
	bx login
	```
	{: codeblock}
	
	**附註：**如果您的認證遭到拒絕，則可以使用「聯合 ID」。請遵循下列步驟，以使用「聯合 ID」來進行鑑別。
	
	<!-- 
	POINT TO IBM CLOUD CLI LOG IN DOCUMENTATION !!!
	
	This link does not work in production yet --> 
	
	1. 登入 [{{site.data.keyword.iamshort}} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://www.bluemix.net/iam/#/apikeys "外部鏈結圖示"){: new_window}。
	2. 選取**建立 API 金鑰**。
		* 輸入 apiKey 名稱及說明
	3. 下載 apiKey。
	4. 開啟檔案，並複製 `apiKey` 欄位中的值。
	5. 使用下列指令來登入：
	 
		```
		bx login --apikey <value>
		```
		{: codeblock}


### 安裝
{: #installation}

1. 執行下列指令，以安裝 [{{site.data.keyword.dev_cli_short}} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](/docs/cli/reference/bluemix_cli/index.html#install_plug-in "外部鏈結圖示"){: new_window}：
 
	```
	bx plugin install dev
	```
	{: codeblock}

2. 	執行下列指令，以驗證外掛程式安裝成功：  
 
	```
	bx dev
	```
	{: codeblock}


