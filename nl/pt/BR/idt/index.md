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

O {{site.data.keyword.dev_cli_long}} fornece uma abordagem extensível orientada por comandos para criar, desenvolver e implementar um projeto da web com o plug-in `dev`. Ideal para desenvolvedores que gostariam de usar o controle da linha de comandos para desenvolver aplicativos de microsserviço de ponta a ponta.

{: shortdesc}

A {{site.data.keyword.dev_cli_notm}} usa dois contêineres para facilitar a construção e o teste do aplicativo. O primeiro é o contêiner de ferramentas, que contém os utilitários necessários para construir e testar seu aplicativo. O Dockerfile para esse contêiner é definido pelo parâmetro [`dockerfile-tools`](#command-parameters). Talvez você o considere um contêiner de desenvolvimento, pois contém as ferramentas normalmente úteis para o desenvolvimento de um tempo de execução específico.

O segundo contêiner é o contêiner de execução. Esse contêiner tem um formato adequado para ser implementado para uso, por exemplo, no {{site.data.keyword.Bluemix}}. Como resultado, um ponto de entrada que inicia seu aplicativo é definido. Quando você selecionar para executar o aplicativo por meio da {{site.data.keyword.dev_cli_short}}, ele usará esse contêiner. O Dockerfile para esse contêiner é definido pelo parâmetro [`dockerfile-run`](#run-parameters).


## Incluindo a {{site.data.keyword.dev_cli_notm}}
{: #add-cli}


### Pré-requisitos
{: #prereq}

Deve-se obter alguns requisitos para explorar completamente e usar adequadamente o {{site.data.keyword.dev_cli_short}}, pois ele é altamente extensível para alavancar tecnologias complementares.

<!--1. Install the [Cloud Foundry CLI ![External link icon](../icons/launch-glyph.svg "External link icon")](https://github.com/cloudfoundry/cli#getting-started "External link icon").-->

1. Instale o [{{site.data.keyword.Bluemix}} CLI ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](http://clis.ng.bluemix.net/ui/home.html "Ícone de link externo").

2. Obtenha um ID do [{{site.data.keyword.Bluemix_notm}}](https://www.bluemix.net).

3. Se você planejar executar e depurar aplicativos localmente, também deverá instalar o [Docker![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.docker.com/get-docker "Ícone de link externo").


### Antes de Come╬ar
{: #before-install}

1. Conecte-se a um terminal de API em sua [{{site.data.keyword.Bluemix_notm}} região](/docs/overview/whatisbluemix.html#ov_intro_reg). Por exemplo, insira o comando a seguir para se conectar à região Sul dos EUA {{site.data.keyword.Bluemix_notm}}:

	```
	bx api https://api.ng.bluemix.net
	```
	{: codeblock}
	
2. Efetue login no {{site.data.keyword.Bluemix_notm}} fornecendo seu IBMid e senha:

	```
	bx login
	```
	{: codeblock}
	
	**Nota:** se suas credenciais forem rejeitadas, talvez você esteja usando um ID federado. Siga essas etapas para autenticar usando o ID federado.
	
	<!-- 
	POINT TO IBM CLOUD CLI LOG IN DOCUMENTATION !!!
	
	This link does not work in production yet --> 
	
	1. Efetue login no [{{site.data.keyword.iamshort}} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.bluemix.net/iam/#/apikeys "Ícone de link externo"){: new_window}.
	2. Selecione **Criar chave API**.
		* Insira um nome e uma descrição da apiKey
	3. Faça download da apiKey.
	4. Abra o arquivo e copie o valor do campo `apiKey`.
	5. Efetue login usando o seguinte comando:
	 
		```
		bx login --apikey <value>
		```
		{: codeblock}


### Installing
{: #installation}

1. Instale a [{{site.data.keyword.dev_cli_short}} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](/docs/cli/reference/bluemix_cli/index.html#install_plug-in "Ícone de link externo"){: new_window} executando o comando a seguir:
 
	```
	bx plugin install dev
	```
	{: codeblock}

2. 	Valide a instalação bem-sucedida do plug-in executando o comando a seguir:  
 
	```
	bx dev
	```
	{: codeblock}


