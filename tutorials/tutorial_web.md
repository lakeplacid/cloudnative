---
copyright:
  years: 2017, 2018
lastupdated: "2018-01-19"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Web Basic Starter
{: #tutorial}

The following end-to-end tutorial walks you through the steps to create a project from a Web Basic Starter. Use these starters to set up a simple web server for Swift, Node, Java, or Python with a choice of web frameworks. Steps include installing prerequisite tools, building and running the project locally and deploying to the cloud.


## Complete the prerequisites
{: #before-you-begin}

Ensure that you install the [prerequisite developer tools ![External link icon](../icons/launch-glyph.svg "External link icon")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}.


## Create a project using the {{site.data.keyword.dev_console}}
{: #create-devex}

Create a project in the {{site.data.keyword.Bluemix}} {{site.data.keyword.dev_console}}:

1. From the [**Starter Kits** ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) page in the {{site.data.keyword.dev_console}}, select a Starter Kit based on your chosen language. For example, for a Node.js application, go to **Express.js Basic** and click **Select Starter Kit**.

2. Enter your project name. For this tutorial, use `WebBasicProject`.   

3. Enter a unique hostname, such as your initials plus `-devhost`. For example:

	```
	abc-devhost
	```

	This hostname will be used for your project's route. For ex: `abc-devhost.mybluemix.net`

4. Select your language platform. For this tutorial, use `Node.js`.

5. Click **Create Project**.


## Optional: Add services
{: #add-services}

1. Select your project in the **Projects** page. 

2. Click **Add Service**.

3. Select the kind of service you want. For this tutorial, select **Data** > **Next** > **Cloudant NoSQL DB** > **Next**.

4. Enter your service name and click **Create**.


## Optional: Create DevOps Toolchain
{: #add-toolchain}

Enabling a toolchain is a valuable option as it creates a team-based development environment for your project. When you create a toolchain, the App Service will provision a Git repository, where you can view source code, clone your project and create/manage issues. You will also have access to a dedicated Gitlab environment and a continuous Delivery Pipeline that is customized to the deployment platform you choose-- Cloud Foundry or Kubernetes.

Continuous delivery is enabled for some applications. You may want to enable continuous delivery to automate builds, tests, and deployments through the Delivery Pipeline, GitHub, and more.

1. Select your project in the **Projects** page. 

2. Click **Create Toolchain**.

3. Select a deployment method. You may choose to either:

	1. Deploy using Cloud Foundry, where you do not need to manage the underlying infrastructure. 
	
	2. Deploy to a Kubernetes Cluster. Provision a cluster of hosts, called worker nodes, to deploy and manage highly available application containers. You may create a cluster or deploy to an existing cluster. 


## Generate your project code
{: #generate-code}

If you created a toolchain in the optional step above, a git repository will have been created for your project. Follow these steps to access your repo:

1. Select your project in the **Projects** page. 

2. Click **View Toolchain**. 

3. Click the **Git** card under the heading **CODE** to open your repository, where you can view source code and clone your project.

Alternatively, if a toolchain is not enabled, you can access your code by downloading the source directly from the App Service.

1. Select your project in the **Projects** page. 

2. Click **Download Code** to download your project archive.


## Begin working on your app
{: #code}

Begin working with your downloaded project:

1. Expand the archived file.

2. Navigate to the new project directory.

3. Use the {{site.data.keyword.dev_cli_notm}} to proceed.


## Build and run the app locally
{: #build-run}

Add your own code, build, and run the project. You can run the application locally on your host system if you install the necessary build tools, or by using the available container support in the {{site.data.keyword.dev_cli_notm}}.

### Using the {{site.data.keyword.dev_cli_short}}

1. Install the node dependencies:

  ```
  npm install
  ```
  {: codeblock}

2. Bundle your frontend code into a module:

  ```
  gulp
  ```
  {: codeblock}

3. To build the project in your current project directory, enter the following command:

  ```
  bx dev build
  ```
  {: codeblock}

4. To run the project in your current project directory, enter the following command:

  ```
  bx dev run
  ```
  {: codeblock}

5. Open your browser to `http://localhost:3000` (your port number may be different depending on the chosen runtime).


## Deploy to the cloud
{: #deploy}

To deploy your project to Cloud Foundry, enter the following command:

  ```
  bx dev deploy
  ```
  {: codeblock}

To deploy your project to a Kubernetes cluster, enter the following command:

```
bx dev deploy --target <container>
```
{: codeblock}

This step will deploy your application to the Cloud. Once the application is deployed, you should see a URL similar to `abc-devhost.mybluemix.net`. Visit this URL in your browser.

If you chose to create a DevOps toolchain, you may view your toolchain:

1. Select your project in the **Projects** page. 

2. Click **View Toolchain**. This gives you access to:

	1. Create and manage issues for your project in Git.
	
	2. View your generated code in Git.
	
	3. Access an Eclipse-based Web IDE.
	
	4. View your delivery pipeline where you can kick off builds, manage deployment and view logs and history.


## Run your project with Hot-Reload (NodeJS Only)
{: #hot-reload}
(Optional)

Hot-reload is a popular development practice where the application runtime updates upon code change by triggering rebuild (when necessary) and restart automatically.

1. Run hot-reload with container:

  ```
  bx dev shell run-dev
  ```
  {: codeblock}

  Open project at `http://localhost:3000` in your browser.

2. Run hot-reload with NPM script.

	1. Run both client-side and server-side hot reload:
	
	  ```
	  npm run dev
	  ```
	  {: codeblock}
	  
	  Open project at `http://localhost:3000` in your browser.

	2. Run server-side hot reload:
	
	  ```
	  npm run build
	  ```
	  {: codeblock}
	  
	  builds frontend code for server use, then
	  
	  ```
	  npm run server-reload
	  ```
	  {: codeblock}
	  
	  Open project at `http://localhost:3000` in your browser.
	
	3. Run client-side hot reload:
	
	  ```
	  npm run client-reload
	  ```
	  {: codeblock}
	  
	  Open project at `http://localhost:8080` in your browser. (Note: this does not use your backend server.)


## Run your project in Xcode (Swift Only)
{: #Xcode}
(Optional)

1. Create an Xcode project.

	Before you can develop in Xcode, you need to use the Swift package manager to build an Xcode project.
	
	```
	swift project generate-xcodeproj
	```
	{: codeblock}

2. Change your active target to the executable:

	Next, open your project in Xcode and make sure that your active target is the executable. You can hold down the option key and click the drop-down menu to select the desired active executable.

3. Press **run**.

4. Open your browser to `http://localhost:8080`.

