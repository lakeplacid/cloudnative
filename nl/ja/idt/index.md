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

{{site.data.keyword.dev_cli_long}} では、`dev` プラグインで Web プロジェクトを作成、開発、デプロイするための拡張可能なコマンド駆動型アプローチを提供します。エンドツーエンドのマイクロサービス・アプリケーションを開発する際にコマンド・ライン制御を使用したい開発者に理想的です。

{: shortdesc}

{{site.data.keyword.dev_cli_notm}} では、アプリケーションのビルドおよびテストを容易にするために、2 つのコンテナーを使用します。1 つ目は、アプリケーションのビルドとテストに必要なユーティリティーを含むツール・コンテナーです。このコンテナーの Dockerfile は、[`dockerfile-tools`](#command-parameters) パラメーターで定義されます。これは、特定のランタイムの開発に通常役立つツールを含むため、開発コンテナーとして考えることもできます。

2 つ目のコンテナーは実行コンテナーです。このコンテナーは、例えば {{site.data.keyword.Bluemix}} などで使用するためにデプロイされるのに適した形式のものです。結果として、アプリケーションを開始するエントリー・ポイントが定義されます。{{site.data.keyword.dev_cli_short}} でアプリケーションを実行することを選択すると、このコンテナーが使用されます。このコンテナーの Dockerfile は、[`dockerfile-run`](#run-parameters) パラメーターで定義されます。


## {{site.data.keyword.dev_cli_notm}} の追加
{: #add-cli}


### 前提条件
{: #prereq}

{{site.data.keyword.dev_cli_short}} は追加の無料テクノロジーを活用できるように高度に拡張可能であるため、これをフルに探索して適切に利用するには、いくつかの前提条件を入手する必要があります。

<!--1. Install the [Cloud Foundry CLI ![External link icon](../icons/launch-glyph.svg "External link icon")](https://github.com/cloudfoundry/cli#getting-started "External link icon").-->

1. [{{site.data.keyword.Bluemix}} CLI ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](http://clis.ng.bluemix.net/ui/home.html "外部リンク・アイコン") をインストールします。

2. [{{site.data.keyword.Bluemix_notm}}](https://www.bluemix.net) ID を入手します。

3. ローカルでのアプリケーションの実行およびデバッグを予定している場合は、[Docker ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.docker.com/get-docker "外部リンク・アイコン") のインストールも必要です。


### 始めに
{: #before-install}

1. 自分の [{{site.data.keyword.Bluemix_notm}} 地域](/docs/overview/whatisbluemix.html#ov_intro_reg)内の API エンドポイントに接続します。例えば、{{site.data.keyword.Bluemix_notm}} 米国南部地域に接続するには、次のコマンドを入力します。

	```
	bx api https://api.ng.bluemix.net
	```
	{: codeblock}
	
2. IBM ID とパスワードを入力して {{site.data.keyword.Bluemix_notm}} にログインします。

	```
	bx login
	```
	{: codeblock}
	
	**注:** 資格情報が拒否された場合、フェデレーテッド ID を使用している可能性があります。フェデレーテッド ID を使用して認証するには、以下のステップに従ってください。
	
	<!-- 
	POINT TO IBM CLOUD CLI LOG IN DOCUMENTATION !!!
	
	This link does not work in production yet --> 
	
	1. [{{site.data.keyword.iamshort}} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.bluemix.net/iam/#/apikeys "外部リンク・アイコン"){: new_window} にログインします。
	2. **「API キーの作成」**を選択します。
		* apiKey の名前と説明を入力します。
	3. apiKey をダウンロードします。
	4. ファイルを開いて、`apiKey` フィールドから値をコピーします。
	5. 以下のコマンドを使用してログインします。
	 
		```
		bx login --apikey <value>
		```
		{: codeblock}


### インストール
{: #installation}

1. 以下のコマンドを実行して、[{{site.data.keyword.dev_cli_short}} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/cli/reference/bluemix_cli/index.html#install_plug-in "外部リンク・アイコン"){: new_window} をインストールします。
 
	```
	bx plugin install dev
	```
	{: codeblock}

2. 	以下のコマンドを実行して、プラグインのインストールが成功したことを確認します。  
 
	```
	bx dev
	```
	{: codeblock}


