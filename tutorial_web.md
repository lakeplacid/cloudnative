---

copyright:
  years: 2016, 2017
lastupdated: "2017-06-12"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# End-to-end tutorial of the Web Basic Starter
{: #tutorial}

The following end-to-end tutorial walks you through the steps to create a project from the Web Basic Starter. Steps include installing prerequisite tools and how to run the project code.


## Installing developer tools
{: #dev_tools}

Ensure that you install the [prerequisite developer tools ![External link icon](../icons/launch-glyph.svg "External link icon")](get_code.html#prereq-dev-tools){: new_window}.


## Choose how to create your project
{: #choose_how}

You can create a project by using either the web-based [{{site.data.keyword.dev_console}}](#create-devex) or through the command-driven [{{site.data.keyword.dev_cli_notm}}](#create-cli). Once the project is created, you can then [run the project](#run).


## Creating a project by using the {{site.data.keyword.dev_console}}
{: #create-devex}

1. Create a project in the {{site.data.keyword.Bluemix}} {{site.data.keyword.dev_console}}:

	1. From the [**Getting Started** ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/developer/getting-started/) page in the {{site.data.keyword.dev_console}}, click **Create Project**.

		You can alternatively click **Create Project** from the **Projects** page.

	2. Select **Web App** and click **Next**.

	3. Select **Basic Web** and click **Next**.

	4. Enter your project name. For this tutorial, use `WebBasicProject`.   

	5. Enter a unique hostname, such as your initials plus `-devhost`. For example:
	
	 ```
	 abc-devhost
	 ```

	6. Select your language platform. For this tutorial, use `Swift`.
   
	7. Click **Create**.

2. Optional: Add the Data capability:

	1. Click **View** for **Data** on the **Project Overview** page.

      You can alternatively select **Create** or **Add Existing** on the **Capabilities > Data** page.

   2. Enter your service name and click **Create**.

3. Generate your project code:

	1. Click **Get the Code** on the **Project Overview** page to select your language.
   
		You can alternatively click on the **Code** page.
      
	2. Click **Generate Code**.
   
	3. When the project code is finished generating, click **Download Code** to download your project archive.

4. Begin working with your downloaded project:

	1. Expand the archived file.
	
	2. Navigate to the new project directory.
	
	3. Use the {{site.data.keyword.dev_cli_notm}} to proceed.

5. Optional: [Update your project](project_overview_page.html#update_language) to generate a new language.


## Creating a project by using the {{site.data.keyword.dev_cli_notm}}
{: #create-cli}

1. Ensure that you install the [{{site.data.keyword.dev_cli_short}}](dev_cli.html).

2. In your Terminal prompt, navigate to a local directory of your choice and run the following command.
  
	```
	bx dev create
	```
	{: codeblock}

3. Provide the following values when prompted:

	* Select a pattern: 1 (for Web)
	* Select a starter: 1 (for Basic Web)
	* Select a language: 2 (for Swift)
	* Enter a name for your project: `WebBasicProjectCLI`
	* Enter a hostname for your project: `abc-devhost`
	  * Enter a unique hostname, such as your initials plus `-devhost`. For example:
	
	     ```
	     abc-devhost
	     ```

4. When your `WebBasicProjectCLI` project is successfully saved, navigate to the `WebBasicProjectCLI` folder.

5. Add your own code, build, and run the project.
	
	1. Build the project with the following command:
 
		```
		bx dev build
		```
		{: codeblock}
	 
	2. Run the project with the following command:
 
		```
		bx dev run
		```
		{: codeblock}


## Running a web project
{: #run}

You can run the application locally on your host system if you install the necessary build tools, or by using the available container support in the {site.data.keyword.dev_cli_notm}}.


### Using the {{site.data.keyword.dev_cli_short}}
{: #dev notoc}

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

5. Open your browser to `http://localhost:8080`.


## Running your project in Xcode
{: #Xcode}

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

