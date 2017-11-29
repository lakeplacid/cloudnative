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

The {{site.data.keyword.dev_cli_long}} (formerly referred to as the Bluemix CLI Developer Plug-in) provides an extensible command driven approach for creating, developing, and deploying a web project, ideal for developers that would like to use command line control to develop end-to-end microservice applications.  

Projects created or enabled for use with the tool come with pre-configured settings encapsulated in the `cli-config.yml` file. The `cli-config.yml` contains default entries used by the commands of the tool, that can be overridden by values passed via the command line.

{: shortdesc}

The {{site.data.keyword.dev_cli_long}} uses two containers to facilitate building and testing your application. The first is the tools container, which contains the necessary utilities to build and test your application. The Dockerfile for this container is defined by the [`dockerfile-tools`](#command-parameters) parameter. You might think of it as a development container as it contains the tools normally useful for development of a particular runtime.

The second container is the run container. This container is of a form suitable to be deployed for use, for example, in {{site.data.keyword.Bluemix}}. As a result, an entry point is defined that starts your application. When you select to run your application through the {{site.data.keyword.dev_cli_short}}, it uses this container. The Dockerfile for this container is defined by the [`dockerfile-run`](#run-parameters) parameter.


## Setting up the {{site.data.keyword.dev_cli_notm}}
{: #add-cli}


### Prerequisites
{: #prereq}

You must obtain a few prerequisites to fully explore and properly utilize the {{site.data.keyword.dev_cli_short}}, as it is highly extensible for leveraging complementary technologies.

<!--1. Install the [Cloud Foundry CLI ![External link icon](../icons/launch-glyph.svg "External link icon")](https://github.com/cloudfoundry/cli#getting-started).-->

1. Obtain a [{{site.data.keyword.Bluemix_notm}}](https://www.bluemix.net) ID.

4. If you are using Microsoft Windows&trade;, you must use Windows 10 or later.


### Before you begin

#### Installing
{: #installation}

To install the tool, you can run the relevant command to invoke our installer. This will install dependencies as well, such as the IBM Cloud CLI, Kubernetes, Helm, and Docker. To install these, use these installation steps:

**Mac and Linux:**  `curl -sL https://ibm.biz/idt-installer | bash`

**Windows 10:**  `Set-ExecutionPolicy Unrestricted; iex(New-Object Net.WebClient).DownloadString('http://ibm.biz/idt-win-installer')`

The [Appendix](#appendix) has the manual installation instructions for each component if you have need of them.

Validate successful plug-in installation by running the following command:  

	bx dev
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
	
	<!-- 
	POINT TO IBM Cloud CLI LOG IN DOCUMENTATION !!!
	
	This link does not work in production yet --> 
	
	1. Log in to [{{site.data.keyword.iamshort}} ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.bluemix.net/iam/#/apikeys){: new_window}.
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


## Commands
{: #commands}

Use the following commands to create a project, deploy, debug, and test it.

### Build
{: #build}

You can build your application by using the `build` command. The `test`, `debug`, and `run` commands expect to find a compiled project so you must first run a `build` operation beforehand.  

The `build-cmd-debug` configuration element is used to build the application for all use except for `run`. You build your application for debugging by specifying the command line option `--debug`.  The `build-cmd-run` configuration element is used when building the application for use with the `run` command.

Run the following command in your current project directory to build your application:  

```
bx dev build [--debug]
```
{: codeblock}


[Build command parameters](#command-parameters)


### Code
{: #code}

Use the `code` command to download a previously created project with application template code and configuration files for the {{site.data.keyword.Bluemix_notm}}.  This is useful when you need to extract a second copy of a project you have created.

Run the following command to download the code from a specified project.

```
bx dev code <projectName>
```
{: codeblock}


### Console
{: #console}

Use the `console` command to open a web browser to your application's web console on IBM Cloud.  You can run the `bx dev console` command from inside your project's folder, and the CLI attempts to find a matching project on the IBM Cloud that has the same project ID as the current directory. If the system is not able to find a matching name, it opens the Web and Mobile dashboard on IBM Cloud instead of the specific project.

Optionally, you can provide a project name and the CLI will skip matching based on folder/application name.  In this case, the CLI opens the named project's console in a web browser.  

Run the following command to open a web browser to your application's web console.

```
bx dev console [projectName]
```
{: codeblock}


### Create
{: #create}

Create a project, prompting for all information, including language, project name, and app pattern type. The project is created in the current directory. 

To create a project in the current project directory and associate services with it, run the following command:

```
bx dev create
```
{: codeblock}


### Debug
{: #debug}

You can debug your application through the `debug` command. A build must first be completed against the project by using the build command with the `--debug` argument. When you invoke the `debug` command, a container is started which provides a debug port or ports as defined by the `container-port-map-debug` value in the cli-config.yml or specified on the command line. Connect your favorite debug tool to the port or ports, and you can debug your application as normal.

First, compile your project:

```
bx dev build --debug
```
{: codeblock}

Run the following command in your current project directory to debug your application:

```
bx dev debug 
```
{: codeblock}	

To exit the debug session use `CTRL-C`.


## Debug command parameters
{: #debug-parameters}

The following parameters are exclusive to the `debug` command and
assist with debugging an application. There are [additional parameters](#command-parameters) shared with other commands.

### `container-port-map-debug`
{: #port-map-debug}

* Port mappings for the debug port. The first value is the port to use in the host OS, the second is the port in the container [host-port:container-port].
* Usage: `bx dev debug --container-port-map-debug 7777:7777`

### `build-cmd-debug`
{: #build-cmd-debug}

* Parameter that is used to build code for DEBUG.
* Usage: `bx dev debug --build-cmd-debug build.command.sh`

### `debug-cmd`
{: #debug-cmd}

* Parameter that is used to specify a command to invoke debug in the tools container. Use this parameter if the `build-cmd-debug` starts your application in debug.
* Usage: `bx dev debug --debug-cmd /the/debug/command`



### Delete
{: #delete}

Use the `delete` command to remove projects from your {{site.data.keyword.Bluemix}} space. You can run the command without parameters to list available projects and select the project from the numbered list to delete. Project code and directories are not removed from your local disk space.

Run the following command to delete your project from {{site.data.keyword.Bluemix}}:

```
bx dev delete <projectName>
```
{: codeblock}
 

**Note:** {{site.data.keyword.Bluemix}} services are **not** removed.


### Deploy
{: #deploy}

You can deploy an application as a Cloud Foundry application or as a container.

To deploy as a Cloud Foundry application to {{site.data.keyword.Bluemix}}, a `manifest.yml` file must be present in your project's root directory.

To deploy an application as a container, you must locally install [Kubernetes](https://kubernetes.io/) and [Helm](https://github.com/kubernetes/helm). You can use the the [installation instructions](#installation) at the top of this page as your guide.

You must also define the location to a Helm chart with the `chart-path` configuration element and have configured the `deploy-target` element to `container`, and the `deploy-image-target` element in the cli-config.yml.  To deploy to {{site.data.keyword.Bluemix}} specifically, set the configuration element `ibm-cluster` to the name of the Kubernetes cluster you have created in {{site.data.keyword.Bluemix}} as described [here](https://console.bluemix.net/docs/containers/cs_tutorials.html#cs_tutorials).

```
    chart-path: "chart/myapplication"

    deploy-target: "container"

    deploy-image-target: "registry.<IBM Cloud Region>.bluemix.net/<Container Registry Namespace>/<App-Name>"

    ibm-cluster: "mycluster"
    ```

Run the following command in your current project directory to build your application:  

```
bx dev build
```
{: codeblock}

Run the following command in your current project directory to deploy your project:

```
bx dev deploy
```
{: codeblock}


## Parameters for deploy
{: #deploy-parameters}

The following parameters can be used with the `deploy` command or by updating the project's `cli-config.yml` file directly. There are [additional parameters](#command-parameters) shared with other commands.

### `chart-path`
{: #chart-path}

* Parameter used for a container deployment to specify the location of the Helm chart used for the deployment.
* Usage `bx dev deploy --chart-path [/the/path]`

### `deploy-target`
{: #deploy-target}

* Parameter optionally used to indicate the type of deployment to be completed.  The default deployment type is buildpack.
* Usage `bx dev deploy -t|--target buildpack|container`

### `deploy-image-target`
{: #deploy-image-target}

* Parameter used with a container deployment as the target image name for the deployment (e.g. to tag to a Docker registry).  The value must not include a version for example:  image-name:{version} as the version is automatically incremented and appended by `deploy`.
* Usage `bx dev deploy --deploy-image-target [image-name]`

### `ibm-cluster`
{: #ibm-cluster}

* Parameter optionally used to define the name of the Kubernetes cluster for a container deployment to {{site.data.keyword.Bluemix}}
* Usage `bx dev deploy --ibm-cluster [cluster-name]`


### Enable
{: #enable}

Enable an existing project for {{site.data.keyword.Bluemix_notm}} deployment. The `enable` command attempts to automatically detect the language of an existing project and then prompt for necessary additional information. This generates and adds files that can be used for local Docker containers, CloudFoundry deployment, or Kubernetes/Container Deployment. 

Run the following command to enable an existing project in the current directory for {{site.data.keyword.Bluemix_notm}} deployment:

```
bx dev enable
```
{: codeblock}

The presence of necessary files provides project language detection for a valid project structure.  

* The presence of a `package.json` file identifies a Node.js project.
* The presence of a `package.swift` file identifies a Swift project.
* The presence of either a `setup.py` or `requirements.txt` file identifies a Python project.
* The presence of either a `pom.xml` or `build.gradle` file identifies a Java project.
	* The presence of a `pom.xml` identifies a Maven project.
	* The presence of a `build.gradle` identifies a Gradle project.

Optionally, you can also override the detected project language using the `--language` argument.  However, only valid and complete projects are supported. The enable command does not modify your source code. 

Language options include:
* node
* swift
* python
* java-ee (interpreted as Java - Java EE)
* java-mp (interpreted as Java - Java MicroProfile)
* java-spring (interpreted as Java - Spring Framework)

Files created using the `bx dev enable` command that have naming conflicts with existing files in the project folder are saved with a `.merge` file extension.  

## Parameters for enable
{: #enable-parameters}

The following parameters can be used with the `enable` command or by updating the project's `cli-config.yml` file directly. There are [additional parameters](#command-parameters) shared with other commands.

### `language`
{: #enable-language}

* Parameter used to specify the language of the project to be enabled.
* Usage `bx dev enable -l|--language [language]`

### `force`
{: #enable-force}

* Parameter used to force re-enabling an already enabled project.
* Usage `bx dev enable -f|--force`



### Help
{: #help}

By default, if no action or arguments are passed in, or if the 'help' action is provided, this command shows a general "Help" text. General help displayed includes a description of the base arguments as well as a listing of the available actions.  

Run the following command to display General help information:

```
bx dev help
```
{: codeblock}


### List
{: #list}

You can list all {{site.data.keyword.Bluemix_notm}} projects in a space.

Run the following command to list your projects:

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

You can run your application through the `run` command. A build must first be completed against the project by using the `build` command. When you invoke the `run` command, the run container is started and exposes the ports as defined by the `container-port-map` parameter. The `run-cmd` parameter can be used to invoke the application if the run container Dockerfile does not contain an entry point to complete this step. 

First, compile your project:

```
bx dev build
```
{: codeblock}

Run the following command in your current project directory to start your application:

```
bx dev run
```
{: codeblock}

To exit the session use `CTRL-C`.


## Run Parameters
{: #run-parameters}

The following parameters are exclusive to the `run` command and
assist with managing your application within the run container. 
There are [additional parameters](#command-parameters) shared with other commands.

### `container-name-run`
{: #container-name-run}
	
* Container name for the run container.
* Usage: `bx dev run --container-name-run [<projectName>]`

### `container-path-run`
{: #container-path-run}

* Location in the container to share on run.
* Usage: `bx dev run --container-path-run [/path/to/app]`

### `host-path-run`
{: #host-path-run}

* Location on the host system to share in the container on run.
* Usage: `bx dev run --host-path-run [/path/to/app/bin]`

### `dockerfile-run`
{: #dockerfile-run}

* Dockerfile for the run container.
* Usage: `bx dev run --dockerfile-run [/path/to/Dockerfile]`

### `image-name-run`
{: #image-name-run}

* Image to create from `dockerfile-run`.
* Usage: `bx dev run --image-name-run [/path/to/image-name]`

### `run-cmd`
{: #run-cmd}

* Parameter that is used to run code in the run container. Use this parameter if your image starts your application.
* Usage: `bx dev run --run-cmd [/the/run/command]`
	
### Status
{: #status}

You can query the status of the containers that are used by the {{site.data.keyword.dev_cli_short}} as defined by `container-name-run` and `container-name-tools`. 

Run the following command in your current project directory to check container status:

```
bx dev status
```
{: codeblock}


[Status command parameters](#command-parameters)


### Stop
{: #stop}

You can stop your containers through the `stop` command.

To stop the tools and run containers as defined in your `cli-config.yml` file, run:

```
bx dev stop
```
{: codeblock}

To stop a container that is not defined in the `cli-config.yml` file, you can specify an extra command line parameter to override it.  If no containers are specified in the `cli-config.yml` file or on the command line, the stop command simply returns.

## Stop Parameters
{: #stop-parameters}

The following parameters are used for the `stop` command. There are [additional parameters](#command-parameters) shared with other commands.

### `container-name-run`
{: #container-name-run}
	
* Container name for the run container.
* Usage: `bx dev stop --container-name-run [<projectName>]`

### `container-name-tools`
{: #container-name-tools}
	
* Container name for the tools container.
* Usage: `bx dev stop --container-name-tools [<projectName>]`



### Test
{: #test}

You can test your application through the `test` command. A build must first be completed against the project by using the `build --debug` command. The tools container is then used to invoke the `test-cmd` for the application.

First, compile your project:

```
bx dev build --debug
```
{: codeblock}

Run the following command to test your application: 

```
bx dev test
```
{: codeblock}


[Test command parameters]
{: #test-parameters}

The following parameter is exclusive to the `test` command.  There are [additional parameters](#command-parameters) shared with other commands.

### `test-cmd`
{: #test-cmd}

* Parameter that is used to specify a command to test code in the tools container.
* Usage: `bx dev test --test-cmd /the/test/command`

## Parameters for build, debug, run, and test
{: #command-parameters}

The following parameters can be used with the `build|debug|run|test` commands or by updating the project's `cli-config.yml` file directly. Extra parameters are available for the [`debug`](#debug-parameters) and [`run`](#run-parameters) commands.

**Note**: Command parameters that are entered on the command line take precedence over the `cli-config.yml` configuration.

### `config-file`  
{: #config-file}

* Specify a cli-config.yml file to use for a command.
* Usage: `bx dev <build|debug|run|status|stop|test> --config-file cli-config.yml`

### `container-name-run`  
{: #container-name-run}

* Container name for the run container.
* Usage: `bx dev <run|status|stop> --container-name-run [<projectName>]`

### `container-name-tools`  
{: #container-name-tools}

* Container name for the tools container.
* Usage: `bx dev <build|debug|run|status|stop|test> --container-name-tools [<projectName>]`

### `host-path-tools`
{: #host-path-tools}

* Location on the host to share for build, debug, test.
* Usage: `bx dev <build|debug|run|test> --host-path-tools [/path/to/build/tools]`

### `container-path-tools`
{: #container-path-tools}

* Location in the container to share for build, debug, test.
* Usage: `bx dev <build|debug|run|test> --container-path-tools [/path/for/build]`

### `container-port-map`
{: #container-port-map}

* Port mappings for the container. The first value is the port to use in the host OS, the second is the port in the container [host-port:container-port].
* Usage: `bx dev <build|debug|run|test> --container-port-map [8090:8090,9090,9090]`

### `dockerfile-tools`
{: #dockerfile-tools}

* Dockerfile for the tools container.
* Usage: `bx dev <build|debug|run|test> --dockerfile-tools [path/to/dockerfile]`

### `image-name-tools`
{: #image-name-tools}

* Image to create from `dockerfile-tools`.
* Usage: `bx dev <build|debug|run|test> --image-name-tools [path/to/image-name]`

### `container-mounts-run`
{: #container-mounts-run}

* Use this option to define mounts between the host system and the run container.
* As a best practice and to prevent unexpected results, you should build and run using the same mount settings.
* Usage: `bx dev <build|run|test> --container-mounts-run [/relative/path/to/host/dir:/absolute/path/to/container/dir, etc.]`

### `container-mounts-tools`
{: #container-mounts-tools}

* Use this option to define mounts between the host system and the tools container.
* As a best practice and to prevent unexpected results, you should build and debug using the same mount settings.
* Usage: `bx dev <build|debug|test> --container-mounts-tools [/relative/path/to/host/dir:/absolute/path/to/container/dir, etc.]`

### `build-cmd-run`
{: #build-cmd-run}

* Parameter that is used to specify a command to build code for all use but DEBUG.
* Usage: `bx dev <build|debug|run|test> --build-cmd-run [some.build.command]`

### `trace`
{: #trace}

* Use this parameter to provide verbose output.
* Usage: `bx dev <build|debug|run|test> --trace`


## APPENDIX
{: #appendix}

The following resources can be helpful when developing Cloud Native apps with the IBM Developer Tools CLI:

**Main links**
- [IBM Cloud Developer Tools Landing page](https://www.ibm.com/cloud/cli) - Main product page for IDT CLI
- [IBM Developer Tools Installer](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools) - Public GitHub repo with detailed installation instructions
- [IBM Cloud App Service](https://console.bluemix.net/developer/appservice) - IBM Cloud console page which is a companion to the IDT tools to create and manage cloud native apps
- [IBM Cloud Tech's Slack - #developer-tools channel](https://ibm-cloud-tech.slack.com) - Discuss IDT tools, get answers, suggest ideas, and more
	- [Request team access](https://slack-invite-ibm-cloud-tech.mybluemix.net/)

**Blogs and Tutorials**
- [Deploying to IBM Cloud private with IBM Cloud Developer Tools CLI](https://www.ibm.com/blogs/bluemix/2017/09/deploying-ibm-cloud-private-ibm-cloud-developer-tools-cli/)
- [Enable existing projects for IBM Cloud with the IBM Cloud Developer Tools CLI](https://www.ibm.com/blogs/bluemix/2017/09/enable-existing-projects-ibm-cloud-ibm-cloud-developer-tools-cli/)
- [Deploying to Kubernetes on IBM Cloud with the IBM Cloud Developer Tools CLI](https://www.ibm.com/blogs/bluemix/2017/09/deploying-kubernetes-ibm-cloud-ibm-cloud-developer-tools-cli/)


