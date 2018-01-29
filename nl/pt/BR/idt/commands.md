---
copyright:
  years: 2017, 2018
lastupdated: "2018-01-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}  

# {{site.data.keyword.dev_cli_notm}} (bx dev) commands
{: #idt-cli}

Version: 1.1.0
Released: Dec 11, 2017

Use the following {{site.data.keyword.dev_cli_notm}} (bx dev) commands to create a project, deploy, debug, and test it.

- [build](#build): Build the project in a local container
- [code](#code): Download the code from a project
- [console](#console): Opens the IBM Cloud console for a project
- [create](#create): Creates a new project and gives you the option to add services
- [debug](#debug): Debug your application in a local container
- [delete](#delete): Deletes a project from your space
- [deploy](#deploy): Deploy an application to IBM Cloud
- [enable](#enable): Add IBM Cloud files to an existing project
- [get-credentials](get-credentials]): Gets credentials required by the project to enable use of bound services
- [help](#help): Help on IDT syntax and arguments
- [list](#list): List all IBM Cloud projects in a space
- [run](#run): Run your application in a local container
- [shell](#shell): Open a shell into a local container
- [status](#status): Check the status of the containers used by the CLI
- [stop](#stop): Stop a container
- [test](#test): Test your application in a local container
- [view](#view): View the app's deployed URL for testing and viewing



## Comandos
{: #commands}

Use os comandos a seguir para criar, implementar, depurar e testar um projeto.

### Compilação
{: #build}

É possível construir seu aplicativo usando o comando `build`. O elemento de configuração `build-cmd-run` é usado para construir o aplicativo. Os comandos `test`, `debug` e `run` esperam encontrar um projeto compilado, portanto, deve-se executar primeiro uma operação de compilação pelo menos uma vez antes.

Execute o comando a seguir no diretório de projeto atual para construir seu aplicativo:  

```
bx dev build
```
{: codeblock}


[Parâmetros do comando de construção](#command-parameters)


### Código
{: #code}

Use o comando `code` para fazer download do código do aplicativo após a implementação, para que possa revisá-lo ou fazer mudanças.

Execute o comando a seguir para fazer download do código de um projeto especificado.

```
bx dev code <projectName>
```
{: codeblock}


### criar
{: #create}

Crie um projeto, solicitando todas as informações, incluindo idioma, nome do projeto e tipo padrão de app. O projeto é criado no diretório atual. 

Para criar um projeto no diretório de projeto atual e associar serviços a ele, execute o comando a seguir:

```
bx dev create
```
{: codeblock}


### Debug
{: #debug}

É possível depurar o aplicativo por meio do comando `debug`. Uma construção deve primeiro ser concluída em relação ao projeto usando o comando build. Quando você chama o comando `debug`, inicia-se um contêiner que fornece uma ou mais portas de depuração, conforme definido pelo valor `container-port-map-debug`. Conecte sua ferramenta de depuração favorita à porta ou portas e será possível depurar seu aplicativo normalmente.

**Limitação**: projetos do Swift não estão disponíveis para depuração.

Primeiro, compile seu projeto:

```
bx dev build
```
{: codeblock}

Execute o comando a seguir no diretório de projeto atual para depurar seu aplicativo:

```
bx dev debug
```
{: codeblock}	

Para sair da sessão de depuração, use `CTRL-C`.


#### Parâmetros do comando de depuração
{: #debug-parameters}

Os parâmetros a seguir são exclusivos para o comando `debug` e
ajudam na depuração de um aplicativo.

##### `container-port-map-debug`
{: #port-map-debug}

* Mapeamentos de porta para a porta de depuração. O primeiro valor é a porta para usar no S.O. do host, o segundo é a porta no contêiner [host-port:container-port].
* Uso: `bx dev debug --container-port-map-debug [7777:7777]`

##### `build-cmd-debug`
{: #build-cmd-debug}

* Parâmetro que é usado para construir o código para DEBUG.
* Uso: `bx dev debug --build-cmd-debug build.command.sh`

##### `debug-cmd`
{: #debug-cmd}

* Parâmetro que é usado para especificar um comando para chamar a depuração no contêiner de ferramentas. Use esse parâmetro se o `build-cmd-debug` iniciar seu aplicativo em depuração.
* Uso: `bx dev debug --debug-cmd /the/debug/command`

#### Depuração de aplicativo local:
{: #local-app-dev}

Para obter mais informações sobre a depuração de aplicativo local, veja [Depuração de aplicativo local](docs/cloudnative/dev_cli_local_debug.html#local-debug).


### Apagar
{: #delete}

Use o comando `delete` para remover projetos do seu espaço do {{site.data.keyword.Bluemix}}. É possível executar o comando sem parâmetros para listar projetos disponíveis para exclusão. O código do projeto e os diretórios não são removidos do seu espaço de disco local.

Execute o comando a seguir para excluir seu projeto do {{site.data.keyword.Bluemix}}:

```
bx dev delete <projectName>
```
{: codeblock}
 

**Nota:** os serviços do {{site.data.keyword.Bluemix}} **não** são removidos.


### Deploy
{: #deploy}

É possível enviar um aplicativo por push para {{site.data.keyword.Bluemix}} por meio do comando `deploy` quando um arquivo `manifest.yml` está presente no diretório raiz do projeto.

Execute o comando a seguir no diretório de projeto atual para construir seu aplicativo:  

```
bx dev build
```
{: codeblock}

Execute o comando a seguir para implementar seu projeto para o {{site.data.keyword.Bluemix}}:

```
bx dev deploy
```
{: codeblock}


### Help
{: #help}

Por padrão, se nenhuma ação ou argumento for passado ou se a ação 'help' for fornecida, esse comando mostrará um texto de "Ajuda" geral. A ajuda geral exibida inclui uma descrição dos argumentos de base, bem como uma listagem das ações disponíveis.  

Execute o comando a seguir para exibir informações da ajuda Geral:

```
bx dev help
```
{: codeblock}


### Listar
{: #list}

É possível listar todos os projetos do {{site.data.keyword.Bluemix_notm}} em um espaço.

Execute o comando a seguir para listar seus projetos:

```
bx dev list
```
{: codeblock}


<!--
### Editing a project
{: #edit}

You can edit a project, such as changing the name, pattern or starter type, or adding services to your project. Run the following command:

```
bx dev edit
```
{: codeblock}
-->


### Run
{: #run}

É possível executar seu aplicativo por meio do comando `run`. Uma construção deve primeiro ser concluída em relação ao projeto usando o comando `build`. Quando você chama o comando de execução, o contêiner de execução é iniciado e expõe as portas, conforme definido pelo parâmetro `container-port-map`. O parâmetro `run-cmd` poderá ser usado para chamar o aplicativo se o Dockerfile do contêiner de execução não contiver um ponto de entrada para concluir essa etapa. 

Primeiro, compile seu projeto:

```
bx dev build
```
{: codeblock}

Execute o comando a seguir no diretório de projeto atual para iniciar seu aplicativo:

```
bx dev run
```
{: codeblock}

Para sair da sessão, use `CTRL-C`.


#### Parâmetros de Execução
{: #run-parameters}

Os parâmetros a seguir são exclusivos para o comando `run` e
ajudam no gerenciamento do aplicativo dentro do contêiner de execução.

##### `container-name-run`
{: #container-name-run}
	
* Nome do contêiner para o contêiner de execução.
* Uso: `bx dev run --container-name-run [<projectName>]`

##### `container-path-run`
{: #container-path-run}

* Local no contêiner para compartilhar na execução.
* Uso: `bx dev run --container-path-run [/path/to/app]`

##### `host-path-run`
{: #host-path-run}

* Local no sistema host para compartilhar no contêiner em execução.
* Uso: `bx dev run --host-path-run [/path/to/app/bin]`

##### `dockerfile-run`
{: #dockerfile-run}

* Dockerfile para o contêiner de execução.
* Uso: `bx dev run --dockerfile-run [/path/to/Dockerfile.yml]`

##### `image-name-run`
{: #image-name-run}

* Imagem a ser criada de `dockerfile-run`.
* Uso: `bx dev run --image-name-run [/path/to/image-name]`

##### `run-cmd`
{: #run-cmd}

* O parâmetro que é usado para executar o código no contêiner de execução. Use esse parâmetro se a sua imagem iniciar o aplicativo.
* Uso: `bx dev run --run-cmd [/the/run/command]`
	
### Status do
{: #status}

É possível consultar o status dos contêineres que são usados pelo {{site.data.keyword.dev_cli_short}} conforme definido por `container-name-run` e `container-name-tools`. 

Execute o comando a seguir no diretório de projeto atual para verificar o status do contêiner:

```
bx dev status
```
{: codeblock}


[Parâmetros do comando de status](#command-parameters)


### Stop
{: #stop}

É possível parar seus contêineres por meio do comando `stop`.

Para parar as ferramentas e executar os contêineres, conforme definido em seu arquivo `cli-config.yml`, execute:

```
bx dev stop
```
{: codeblock}

Para parar um contêiner que não é definido no arquivo `cli-config.yml`, é possível especificar um parâmetro extra da linha de comandos para sobrescrevê-lo. Para o contêiner de ferramentas, use o parâmetro [`--container-name-tools`](#container-name-tools)
e, para o contêiner de execução, use o parâmetro [`--container-name-run`](#container-name-run). Se nenhum contêiner for especificado no arquivo `cli-config.yml` ou na linha de comandos, o comando stop simplesmente será retornado.


### Testar (Test)
{: #test}

É possível testar o aplicativo por meio do comando `test`. Uma construção deve primeiro ser concluída em relação ao projeto usando o comando `build`. O contêiner de ferramentas é então usado para chamar o `test-cmd` para o aplicativo.

Primeiro, compile seu projeto:

```
bx dev build
```
{: codeblock}

Execute o comando a seguir para testar seu aplicativo: 

```
bx dev test
```
{: codeblock}


[Parâmetros do comando de teste](#command-parameters)


## Parâmetros para construir, depurar, executar e testar
{: #command-parameters}

Os parâmetros a seguir podem ser usados com os comandos `build|debug|run|test` ou atualizando o arquivo `cli-config.yml` do projeto diretamente. Parâmetros extras estão disponíveis para os comandos [`debug`](#debug-parameters) e [`run`](#run-parameters).

**Nota**: os parâmetros de comando que são inseridos na linha de comandos têm precedência sobre a configuração `cli-config.yml`.

### `container-name-tools`  
{: #container-name-tools}

* O nome do contêiner para o contêiner de ferramentas.
* Uso: `bx dev <build|debug|run|stop|test> --container-name-tools [<projectName>]`

### `host-path-tools`
{: #host-path-tools}

* Local no host a ser compartilhado para construção, depuração, teste.
* Uso: `bx dev <build|debug|run|test> --host-path-tools [/path/to/build/tools]`

### `container-path-tools`
{: #container-path-tools}

* Local no contêiner a ser compartilhado para construção, depuração, teste.
* Uso: `bx dev <build|debug|run|test> --container-path-tools [/path/for/build]`

### `container-port-map`
{: #container-port-map}

* Mapeamentos de porta para o contêiner. O primeiro valor é a porta para usar no S.O. do host, o segundo é a porta no contêiner [host-port:container-port].
* Uso: `bx dev <build|debug|run|test> --container-port-map [8090:8090,9090,9090]`

### `dockerfile-tools`
{: #dockerfile-tools}

* Dockerfile para o contêiner de ferramentas.
* Uso: `bx dev <build|debug|run|test> --dockerfile-tools [path/to/dockerfile]`

### `image-name-tools`
{: #image-name-tools}

* Imagem a ser criada de `dockerfile-tools`.
* Uso: `bx dev <build|debug|run|test> --image-name-tools [path/to/image-name]`

### `build-cmd-run`
{: #build-cmd-run}

* Parâmetro que é usado para especificar um comando para construir códigos para todos os usos, exceto DEBUG.
* Uso: `bx dev <build|debug|run|test> --build-cmd-run [some.build.command]`

### `test-cmd`
{: #test-cmd}

* Parâmetro que é usado para especificar um comando para testar códigos no contêiner de ferramentas.
* Uso: `bx dev <build|debug|run|test> --test-cmd [/the/test/command]`

### `rastreamento`
{: #trace}

* Use esse parâmetro para fornecer saída detalhada.
* Uso: `bx dev <build|debug|run|test> --trace`


