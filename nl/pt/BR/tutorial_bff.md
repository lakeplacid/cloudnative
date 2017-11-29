---

copyright:
  years: 2016, 2017
lastupdated: "2017-11-02"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Tutorial de ponta a ponta do Iniciador BFF Basic
{: #tutorial}

O tutorial de ponta a ponta a seguir percorre as etapas para a criação de um projeto por meio do BFF Basic Starter. As etapas incluem a instalação de ferramentas obrigatórias e as etapas para executar o código do projeto.


## Instalando ferramentas do desenvolvedor
{: #dev_tools}

Assegure-se de instalar as [ferramentas de desenvolvedor de pré-requisito![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](get_code.html#prereq-dev-tools "Ícone de link externo"){: new_window}.


## Escolha como criar o seu projeto
{: #choose_how}

Crie um projeto usando o [{{site.data.keyword.dev_console}}](#create-devex) baseado em texto ou usando o [{{site.data.keyword.dev_cli_notm}}](#create-cli) orientado por comandos. Depois que o projeto é criado, será possível [executar o projeto](#running-bff).


## Criando um projeto usando o {{site.data.keyword.dev_console}}
{: #create-devex}

1. Crie um projeto no {{site.data.keyword.Bluemix}} {{site.data.keyword.dev_console}}.

	1. Na página [**Introdução** ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/developer/getting-started/ "Ícone de link externo") no {{site.data.keyword.dev_console}}, clique em **Criar projeto**.

		Como alternativa, clique em **Criar projeto** na página **Projetos**.

	2. Selecione **Backend for Frontend** e clique em **Avançar**.

	3. Selecione **Basic Backend** e clique em **Avançar**.

	4. Insira o nome do projeto. Para este tutorial, use `BFFProject`.   

	5. Insira um nome do host exclusivo, tal como suas iniciais mais `-devhost`. Por exemplo:
	
	 ```
	 abc-devhost
	 ``` 

	6. Selecione a plataforma da linguagem. Para este tutorial, use `Node`.
   
	7. Clique em **Criar**.

2. Opcional: inclua o recurso Dados.

	1. Clique em **Visualizar** para **Dados** na página **Visão geral do projeto**.

      Como alternativa, é possível selecionar **Criar** ou **Incluir existente** na página **Recursos > Dados**.

   2. Insira o nome do serviço e clique em **Criar**.

3. Gere seu código do projeto:

	1. Clique em **Obter o código** na página **Visão geral do projeto** para selecionar sua linguagem.
   
		Como alternativa, é possível clicar na página **Código**.
      
	2. Clique em **Gerar código**.
   
	3. Quando o código do projeto concluir a geração, clique
em **Fazer download do código** para fazer
download do seu archive de projeto.

4. Comece a trabalhar com seu projeto transferido por download:

	1. Expanda o arquivo arquivado.
	
	2. Navegue até o novo diretório de projeto.
	
	3. Use o {{site.data.keyword.dev_cli_notm}} para continuar.

5. Opcional: [atualize seu projeto](project_overview_page.html#update_language) para gerar uma nova linguagem.


## Criando um projeto usando o {{site.data.keyword.dev_cli_notm}}
{: #create-cli}

1. Assegure-se de instalar o [{{site.data.keyword.dev_cli_short}}](dev_cli.html).

2. No prompt do Terminal, navegue para um diretório local de sua preferência e execute o comando a seguir.
  
	```
	bx dev create
	```
	{: codeblock}
	
3. Forneça os valores a seguir quando solicitado:

	* Selecione um padrão: 3 (para Backend for Frontend)
	* Selecione um iniciador: 1 (para Basic Backend)
	* Selecione uma linguagem: 1 (para Node)
	* Insira um nome para seu projeto: `BFFProjectCLI`
	* Insira um nome do host para o seu projeto: `abc-devhost`
	  * Insira um nome do host exclusivo, tal como suas iniciais mais `-devhost`. Por exemplo:
	
	     ```
	     abc-devhost
	     ```
	  
4. Após o seu `BFFProjectCLI` ser salvo, navegue para a pasta `BFFProjectCLI`.

5. Inclua seu próprio código e execute o projeto.
 
	1. Construa seu projeto com o comando a seguir:

		```
		bx dev build
		```
		{: codeblock}
		 
	2. Execute seu projeto com o comando a seguir:

 		```
		bx dev run
		```
		{: codeblock}


## Executando um projeto do BFF
{: #running-bff}

Será possível executar o aplicativo localmente em seu sistema host se você instalar as ferramentas de construção necessárias ou usando o suporte de contêiner disponível no {{site.data.keyword.dev_cli_notm}}.


### Usando o plug-in do IBM Cloud
{: #using-blumix}

1. Para construir o projeto no seu diretório de projeto atual, insira o comando a seguir:
   ```
   bx dev build
   ```
   {: codeblock}

2. Para executar o projeto em seu diretório de projeto atual, insira o comando a seguir:
   ```
   bx dev run
   ```
   {: codeblock}

3. É possível executar curl em seu servidor com:
   ```
   curl http://localhost:8080
   ```
   {: codeblock}

4. É possível visualizar o documento da API em seu servidor em:
   ```
   http://localhost:8080/swagger/api
   ```
   {: codeblock}

5. É possível explorar a API em seu servidor em:
   ```
   http://localhost:8080/explorer
   ```
   {: codeblock}
