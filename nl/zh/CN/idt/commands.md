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



## 命令
{: #commands}

使用以下命令创建、部署、调试和测试项目。

### Build
{: #build}

您可以使用 `build` 命令构建应用程序。`build-cmd-run` 配置元素用于构建应用程序。`test`、`debug` 和 `run` 命令预期找到已编译的项目，因此您必须先提前至少运行一次构建操作。

在当前项目目录中运行以下命令以构建应用程序：  

```
bx dev build
```
{: codeblock}


[Build 命令参数](#command-parameters)


### Code
{: #code}

使用 `code` 命令可在部署后下载应用程序代码，以便可在本地查看或执行更改。

运行以下命令以从指定项目下载代码。

```
bx dev code <projectName>
```
{: codeblock}


### Create
{: #create}

创建项目，系统会提示输入所有信息，包括语言、项目名称和应用程序模式类型。将在当前目录中创建项目。 

要在当前项目目录中创建项目并将服务与其关联，请运行以下命令：

```
bx dev create
```
{: codeblock}


### Debug
{: #debug}

您可以通过 `debug` 命令调试应用程序。必须先使用 build 命令，完成对项目的构建。当您调用 `debug` 命令时，会启动一个容器，其可提供一个或多个调试端口，如 `container-port-map-debug` 值所定义。将偏好的调试工具连接到端口，可照常调试应用程序。

**限制**：Swift 项目不可用于调试。

首先，对项目进行编译：

```
bx dev build
```
{: codeblock}

在当前项目目录中运行以下命令以调试应用程序：

```
bx dev debug
```
{: codeblock}	

要退出调试会话，请使用 `CTRL-C`。


#### Debug 命令参数
{: #debug-parameters}

以下参数专用于 `debug` 命令，可帮助调试应用程序。

##### `container-port-map-debug`
{: #port-map-debug}

* 调试端口的端口映射。第一个值为要在主机操作系统中使用的端口，第二个值为容器中的端口 [host-port:container-port]。
* 用法：`bx dev debug --container-port-map-debug [7777:7777]`

##### `build-cmd-debug`
{: #build-cmd-debug}

* 用于为 DEBUG 构建代码的参数。
* 用法：`bx dev debug --build-cmd-debug build.command.sh`

##### `debug-cmd`
{: #debug-cmd}

* 用于指定在工具容器中调用 debug 的命令的参数。如果 `build-cmd-debug` 以调试方式启动应用程序，请使用此参数。
* 用法：`bx dev debug --debug-cmd /the/debug/command`

#### 本地应用程序调试：
{: #local-app-dev}

有关本地应用程序调试的更多信息，请参阅[本地应用程序调试](docs/cloudnative/dev_cli_local_debug.html#local-debug)。


### Delete
{: #delete}

使用 `delete` 命令可从 {{site.data.keyword.Bluemix}} 空间中除去项目。您可以运行不含参数的该命令，以列出可用项目进行删除。项目代码和目录不会从本地磁盘空间中除去。

运行以下命令可从 {{site.data.keyword.Bluemix}} 删除项目：

```
bx dev delete <projectName>
```
{: codeblock}
 

**注：****不会**除去 {{site.data.keyword.Bluemix}} 服务。


### Deploy
{: #deploy}

当您项目的根目录中存在 `manifest.yml` 文件时，通过 `deploy` 命令，可以将应用程序推送至 {{site.data.keyword.Bluemix}}。

在当前项目目录中运行以下命令以构建应用程序：  

```
bx dev build
```
{: codeblock}

运行以下命令可将项目部署到 {{site.data.keyword.Bluemix}}：

```
bx dev deploy
```
{: codeblock}


### Help
{: #help}

缺省情况下，如果未传入任何操作或自变量，或者，如果提供了“help”操作，那么此命令会显示常规“帮助”文本。显示的常规帮助包含基本自变量的描述以及可用操作的列表。  

运行以下命令以显示常规帮助信息：

```
bx dev help
```
{: codeblock}


### 列表
{: #list}

您可以列出空间中所有 {{site.data.keyword.Bluemix_notm}} 项目。

运行以下命令以列出项目：

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

您可以通过 `run` 命令运行应用程序。必须先使用 `build` 命令，完成对项目的构建。调用 run 命令时，会启动运行容器，并公开 `container-port-map` 参数所定义的端口。如果运行容器 Dockerfile 不包含完成此步骤的入口点，那么可以使用 `run-cmd` 参数调用应用程序。 

首先，对项目进行编译：

```
bx dev build
```
{: codeblock}

在当前项目目录中运行以下命令以启动应用程序：

```
bx dev run
```
{: codeblock}

要退出会话，请使用 `CTRL-C`。


#### 运行参数
{: #run-parameters}

以下参数专用于 `run` 命令，可帮助管理运行容器中的应用程序。

##### `container-name-run`
{: #container-name-run}
	
* 运行容器的容器名称。
* 用法：`bx dev run --container-name-run [<projectName>]`

##### `container-path-run`
{: #container-path-run}

* 容器中要在运行时共享的位置。
* 用法：`bx dev run --container-path-run [/path/to/app]`

##### `host-path-run`
{: #host-path-run}

* 容器中要针对运行共享的主机系统上的位置。
* 用法：`bx dev run --host-path-run [/path/to/app/bin]`

##### `dockerfile-run`
{: #dockerfile-run}

* 运行容器的 Dockerfile。
* 用法：`bx dev run --dockerfile-run [/path/to/Dockerfile.yml]`

##### `image-name-run`
{: #image-name-run}

* 要从 `dockerfile-run` 创建的映像。
* 用法：`bx dev run --image-name-run [/path/to/image-name]`

##### `run-cmd`
{: #run-cmd}

* 用于在运行容器中运行代码的参数。如果映像启动应用程序，请使用此参数。
* 用法：`bx dev run --run-cmd [/the/run/command]`
	
### Status
{: #status}

您可以查询 `container-name-run` 和 `container-name-tools` 所定义的 {{site.data.keyword.dev_cli_short}} 使用的容器的状态。 

在当前项目目录中运行以下命令以检查容器状态：

```
bx dev status
```
{: codeblock}


[Status 命令参数](#command-parameters)


### Stop
{: #stop}

您可以通过 `stop` 命令停止容器。

要如 `cli-config.yml` 文件中所定义的那样停止工具并运行容器，请运行：

```
bx dev stop
```
{: codeblock}

要停止未在 `cli-config.yml` 文件中定义的容器，您可以指定额外的命令行参数以对其进行覆盖。对于工具容器，请使用 [`--container-name-tools`](#container-name-tools) 参数，对于运行容器，请使用 [`--container-name-run`](#container-name-run) 参数。如果在 `cli-config.yml` 文件中或命令行上未指定任何容器，那么只是返回 stop 命令。


### Test
{: #test}

您可以通过 `test` 命令测试应用程序。必须先使用 `build` 命令，完成对项目的构建。然后，使用工具容器针对应用程序调用 `test-cmd`。

首先，对项目进行编译：

```
bx dev build
```
{: codeblock}

运行以下命令以测试应用程序： 

```
bx dev test
```
{: codeblock}


[Test 命令参数](#command-parameters)


## Build、debug、run 和 test 的参数
{: #command-parameters}

既可以将以下参数与 `build|debug|run|test` 命令配合使用，也可以通过直接更新项目的 `cli-config.yml` 文件来使用这些参数。[`debug`](#debug-parameters) 和 [`run`](#run-parameters) 命令还有其他参数可用。

**注**：在命令行上输入的命令参数优先于 `cli-config.yml` 配置。

### `container-name-tools`  
{: #container-name-tools}

* 工具容器的容器名称。
* 用法：`bx dev <build|debug|run|stop|test> --container-name-tools [<projectName>]`

### `host-path-tools`
{: #host-path-tools}

* 主机上要针对 build、debug 和 test 共享的位置。
* 用法：`bx dev <build|debug|run|test> --host-path-tools [/path/to/build/tools]`

### `container-path-tools`
{: #container-path-tools}

* 容器中要针对 build、debug 和 test 共享的位置。
* 用法：`bx dev <build|debug|run|test> --container-path-tools [/path/for/build]`

### `container-port-map`
{: #container-port-map}

* 容器的端口映射。第一个值为要在主机操作系统中使用的端口，第二个值为容器中的端口 [host-port:container-port]。
* 用法：`bx dev <build|debug|run|test> --container-port-map [8090:8090,9090,9090]`

### `dockerfile-tools`
{: #dockerfile-tools}

* 工具容器的 Dockerfile。
* 用法：`bx dev <build|debug|run|test> --dockerfile-tools [path/to/dockerfile]`

### `image-name-tools`
{: #image-name-tools}

* 要从 `dockerfile-tools` 创建的映像。
* 用法：`bx dev <build|debug|run|test> --image-name-tools [path/to/image-name]`

### `build-cmd-run`
{: #build-cmd-run}

* 用于指定针对除 DEBUG 之外的所有用法构建代码的命令的参数。
* 用法：`bx dev <build|debug|run|test> --build-cmd-run [some.build.command]`

### `test-cmd`
{: #test-cmd}

* 用于指定在工具容器中测试代码的命令的参数。
* 用法：`bx dev <build|debug|run|test> --test-cmd [/the/test/command]`

### `trace`
{: #trace}

* 使用此参数来提供详细输出。
* 用法：`bx dev <build|debug|run|test> --trace`


