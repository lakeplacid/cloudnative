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



## 명령
{: #commands}

다음 명령을 사용하여 프로젝트를 작성하고, 배치하고, 디버그하고, 테스트하십시오. 

### build
{: #build}

`build` 명령을 사용하여 애플리케이션을 빌드할 수 있습니다. 애플리케이션을 빌드하는 데 `build-cmd-run` 구성 요소가 사용됩니다. `test`, `debug` 및 `run` 명령은 컴파일된 프로젝트를 찾을 것으로 예상하므로 사전에 한 번 이상 빌드 오퍼레이션을 실행해야 합니다.

애플리케이션을 빌드하려면 현재 프로젝트 디렉토리에서 다음 명령을 실행하십시오.   

```
bx dev build
```
{: codeblock}


[build 명령 매개변수](#command-parameters)


### code
{: #code}

`code` 명령을 사용하여 배치 이후에 애플리케이션 코드를 다운로드할 수 있으며, 이를 로컬에서 검토하거나 수정할 수 있습니다. 

지정된 프로젝트에서 코드를 다운로드하려면 다음 명령을 실행하십시오. 

```
bx dev code <projectName>
```
{: codeblock}


### create
{: #create}

프로젝트를 작성하며 언어, 프로젝트 이름 및 앱 패턴 유형을 포함하는 모든 정보에 대한 프롬프트를 표시합니다. 프로젝트는 현재 디렉토리에 작성됩니다.  

현재 프로젝트 디렉토리에 새 프로젝트를 작성하고 여기에 서비스를 연관시키려면 다음 명령을 실행하십시오. 

```
bx dev create
```
{: codeblock}


### debug
{: #debug}

`debug` 명령을 통해 애플리케이션을 디버그할 수 있습니다. build 명령을 사용하여 프로젝트에 대해 빌드를 우선 완료해야 합니다. `debug` 명령을 호출하면 `container-port-map-debug` 값에 의해 정의된 대로 디버그 포트 또는 포트를 제공하는 컨테이너가 시작됩니다. 원하는 디버그 도구를 포트에 연결하면 여느 때와 같이 애플리케이션을 디버그할 수 있습니다. 

**제한사항**: Swift 프로젝트는 디버그에 사용할 수 없습니다. 

우선 프로젝트를 컴파일하십시오. 

```
bx dev build
```
{: codeblock}

애플리케이션을 디버그하려면 현재 프로젝트 디렉토리에서 다음 명령을 실행하십시오. 

```
bx dev debug
```
{: codeblock}	

디버그 세션을 종료하려면 `CTRL-C`를 사용하십시오. 


#### debug 명령 매개변수
{: #debug-parameters}

다음 매개변수는 `debug` 명령 전용이며 애플리케이션 디버깅에 도움을 줍니다. 

##### `container-port-map-debug`
{: #port-map-debug}

* 디버그 포트의 포트 맵핑입니다. 첫 번째 값은 호스트 OS에서 사용할 포트이며, 두 번째 값은 컨테이너의 포트입니다([host-port:container-port]). 
* 사용법: `bx dev debug --container-port-map-debug [7777:7777]`

##### `build-cmd-debug`
{: #build-cmd-debug}

* DEBUG용 코드를 빌드하는 데 사용되는 매개변수입니다. 
* 사용법: `bx dev debug --build-cmd-debug build.command.sh`

##### `debug-cmd`
{: #debug-cmd}

* 도구 컨테이너에서 디버그를 호출하는 명령을 지정하기 위해 사용되는 매개변수입니다. `build-cmd-debug`가 애플리케이션을 디버그 모드로 시작하는 경우 이 매개변수를 사용하십시오. 
* 사용법: `bx dev debug --debug-cmd /the/debug/command`

#### 로컬 애플리케이션 디버깅
{: #local-app-dev}

로컬 애플리케이션 디버깅에 대한 자세한 정보는 [로컬 애플리케이션 디버깅](docs/cloudnative/dev_cli_local_debug.html#local-debug)을 참조하십시오. 


### delete
{: #delete}

`delete` 명령을 사용하여 {{site.data.keyword.Bluemix}} 영역에서 프로젝트를 제거할 수 있습니다. 매개변수 없이 명령을 실행하면 삭제가 가능한 프로젝트가 나열됩니다. 프로젝트 코드 및 디렉토리는 로컬 디스크 영역에서 제거되지 않습니다. 

{{site.data.keyword.Bluemix}}에서 프로젝트를 삭제하려면 다음 명령을 실행하십시오. 

```
bx dev delete <projectName>
```
{: codeblock}
 

**참고:** {{site.data.keyword.Bluemix}} 서비스는 제거되지 **않습니다**. 


### deploy
{: #deploy}

`manifest.yml` 파일이 프로젝트의 루트 디렉토리에 있을 때 `deploy` 명령을 통해 {{site.data.keyword.Bluemix}}에 애플리케이션을 푸시할 수 있습니다. 

애플리케이션을 빌드하려면 현재 프로젝트 디렉토리에서 다음 명령을 실행하십시오.   

```
bx dev build
```
{: codeblock}

{{site.data.keyword.Bluemix}}에 프로젝트를 배치하려면 다음 명령을 실행하십시오. 

```
bx dev deploy
```
{: codeblock}


### help
{: #help}

기본적으로, 조치 또는 인수가 전달되지 않거나 'help' 조치가 제공된 경우에는 이 명령에서 일반 "도움말" 텍스트를 표시합니다. 표시되는 일반 도움말에는 기본 인수와 사용 가능한 조치 목록이 포함됩니다.   

일반 도움말 정보를 표시하려면 다음 명령을 실행하십시오. 

```
bx dev help
```
{: codeblock}


### list
{: #list}

영역의 모든 {{site.data.keyword.Bluemix_notm}} 프로젝트를 나열할 수 있습니다. 

프로젝트를 나열하려면 다음 명령을 실행하십시오. 

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


### run
{: #run}

`run` 명령을 통해 애플리케이션을 실행할 수 있습니다. `build` 명령을 사용하여 프로젝트에 대해 빌드를 우선 완료해야 합니다. run 명령을 호출하면 실행 컨테이너가 시작되며 `container-port-map` 매개변수에 의해 정의된 대로 포트를 노출합니다. 실행 컨테이너 Dockerfile에 이 단계를 완료하기 위한 시작점이 포함되지 않은 경우에는 애플리케이션을 호출하기 위해 `run-cmd` 매개변수를 사용할 수 있습니다.  

우선 프로젝트를 컴파일하십시오. 

```
bx dev build
```
{: codeblock}

애플리케이션을 시작하려면 현재 프로젝트 디렉토리에서 다음 명령을 실행하십시오. 

```
bx dev run
```
{: codeblock}

세션을 종료하려면 `CTRL-C`를 사용하십시오. 


#### run 매개변수
{: #run-parameters}

다음 매개변수는 `run` 명령 전용이며 실행 컨테이너 내의 애플리케이션을 관리하는 데 도움을 줍니다. 

##### `container-name-run`
{: #container-name-run}
	
* 실행 컨테이너의 컨테이너 이름입니다. 
* 사용법: `bx dev run --container-name-run [<projectName>]`

##### `container-path-run`
{: #container-path-run}

* 실행 시 공유할 컨테이너 내의 위치입니다. 
* 사용법: `bx dev run --container-path-run [/path/to/app]`

##### `host-path-run`
{: #host-path-run}

* 실행 시 컨테이너에서 공유할 호스트 시스템 내의 위치입니다. 
* 사용법: `bx dev run --host-path-run [/path/to/app/bin]`

##### `dockerfile-run`
{: #dockerfile-run}

* 실행 컨테이너의 Dockerfile입니다. 
* 사용법: `bx dev run --dockerfile-run [/path/to/Dockerfile.yml]`

##### `image-name-run`
{: #image-name-run}

* `dockerfile-run`에서 작성할 이미지입니다.
* 사용법: `bx dev run --image-name-run [/path/to/image-name]`

##### `run-cmd`
{: #run-cmd}

* 실행 컨테이너에서 코드를 실행하는 데 사용되는 매개변수. 이미지가 애플리케이션을 시작하는 경우 이 매개변수를 사용하십시오. 
* 사용법: `bx dev run --run-cmd [/the/run/command]`
	
### status
{: #status}

`container-name-run` 및 `container-name-tools`에서 정의한 대로 {{site.data.keyword.dev_cli_short}}에서 사용하는 컨테이너의 상태를 조회할 수 있습니다.  

컨테이너 상태를 확인하려면 현재 프로젝트 디렉토리에서 다음 명령을 실행하십시오. 

```
bx dev status
```
{: codeblock}


[status 명령 매개변수](#command-parameters)


### stop
{: #stop}

`stop` 명령을 통해 컨테이너를 중지할 수 있습니다. 

`cli-config.yml` 파일에 정의된 대로 도구 및 실행 컨테이너를 중지하려면 다음을 실행하십시오.

```
bx dev stop
```
{: codeblock}

`cli-config.yml` 파일에 정의되지 않은 컨테이너를 중지하기 위해 추가 명령행 매개변수를 지정하여 대체할 수 있습니다. 도구 컨테이너의 경우 [`--container-name-tools`](#container-name-tools) 매개변수를 사용하고, 실행 컨테이너의 경우 [`--container-name-run`](#container-name-run) 매개변수를 사용하십시오. `cli-config.yml` 파일 또는 명령행에 컨테이너가 지정되어 있지 않으면 단순하게 stop 명령이 리턴됩니다. 


### test
{: #test}

`test` 명령을 통해 애플리케이션을 테스트할 수 있습니다. `build` 명령을 사용하여 프로젝트에 대해 빌드를 우선 완료해야 합니다. 그 후 애플리케이션에 대해 `test-cmd`를 호출하기 위해 도구 컨테이너가 사용됩니다. 

우선 프로젝트를 컴파일하십시오. 

```
bx dev build
```
{: codeblock}

애플리케이션을 테스트하려면 다음 명령을 실행하십시오.  

```
bx dev test
```
{: codeblock}


[test 명령 매개변수](#command-parameters)


## build, debug, run 및 test의 매개변수
{: #command-parameters}

다음 매개변수는 `build|debug|run|test` 명령에서 또는 프로젝트의 `cli-config.yml` 파일을 직접 업데이트하여 사용될 수 있습니다. [`debug`](#debug-parameters) 및 [`run`](#run-parameters) 명령에 대해 추가 매개변수가 사용 가능합니다. 

**참고**: 명령행에서 입력된 명령 매개변수는 `cli-config.yml` 구성보다 우선합니다. 

### `container-name-tools`  
{: #container-name-tools}

* 도구 컨테이너의 컨테이너 이름입니다. 
* 사용법: `bx dev <build|debug|run|stop|test> --container-name-tools [<projectName>]`

### `host-path-tools`
{: #host-path-tools}

* build, debug, test에 대해 공유할 호스트 내의 위치입니다. 
* 사용법: `bx dev <build|debug|run|test> --host-path-tools [/path/to/build/tools]`

### `container-path-tools`
{: #container-path-tools}

* build, debug, test에 대해 공유할 컨테이너 내의 위치입니다. 
* 사용법: `bx dev <build|debug|run|test> --container-path-tools [/path/for/build]`

### `container-port-map`
{: #container-port-map}

* 컨테이너의 포트 맵핑입니다. 첫 번째 값은 호스트 OS에서 사용할 포트이며, 두 번째 값은 컨테이너의 포트입니다([host-port:container-port]). 
* 사용법: `bx dev <build|debug|run|test> --container-port-map [8090:8090,9090,9090]`

### `dockerfile-tools`
{: #dockerfile-tools}

* 도구 컨테이너의 Dockerfile입니다. 
* 사용법: `bx dev <build|debug|run|test> --dockerfile-tools [path/to/dockerfile]`

### `image-name-tools`
{: #image-name-tools}

* `dockerfile-tools`에서 작성할 이미지입니다.
* 사용법: `bx dev <build|debug|run|test> --image-name-tools [path/to/image-name]`

### `build-cmd-run`
{: #build-cmd-run}

* DEBUG 외의 모든 용도를 위한 코드를 빌드하는 명령을 지정하기 위해 사용되는 매개변수입니다. 
* 사용법: `bx dev <build|debug|run|test> --build-cmd-run [some.build.command]`

### `test-cmd`
{: #test-cmd}

* 도구 컨테이너에서 코드를 테스트하는 명령을 지정하기 위해 사용되는 매개변수입니다. 
* 사용법: `bx dev <build|debug|run|test> --test-cmd [/the/test/command]`

### `trace`
{: #trace}

* 이 매개변수를 사용하여 상세 출력을 제공합니다.
* 사용법: `bx dev <build|debug|run|test> --trace`


