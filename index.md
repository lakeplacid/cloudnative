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
{:note:.deprecated}

# Building Cloud Native Projects
{: #web-mobile}

You can manage cloud native apps through the concept of {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}} *Projects*. You can create a project by using the [{{site.data.keyword.dev_console}}](devex.html) or the [{{site.data.keyword.dev_cli_notm}}](idt/index.html) for the {{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}} CLI. The {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}} brings the most common service capabilities that are required for a cloud native application developer into a single, connected experience that has been optimized for the developer.

The {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}} enables a cloud native application developer to create a project from a variety of starter kits, create and connect key {{site.data.keyword.Bluemix_notm}} optimized services to your project, and quickly download working code with SDKs. The SDKs are fully integrated with capability credentials or dependencies that enable you to have it running in minutes. When your application is running and you have set up and configured capabilities, you can return to your project to monitor and manage engagement with your application users. You can also configure and manage your services through the {{site.data.keyword.dev_console}}.

<!--
While the {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.dev_console}} provides an integrated development experience, some developers might still want to have finer-grained control and wire services together manually. If this is your preferred approach, you might want to consider using the [{{site.data.keyword.mobilefirstbp}} Starter boilerplate](try_mobile.html).
-->

<!--With {{site.data.keyword.Bluemix}} Mobile services, you can incorporate pre-built, managed, and scalable cloud services into your mobile applications. You can focus on building your mobile apps, instead of the complexities of managing the back-end infrastructure.

The Mobile dashboard provides an integrated experience on {{site.data.keyword.Bluemix_notm}} where you can create mobile projects easily from within the dashboard.
-->


## Projects
{: #projects}

The {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}} combines the app user interface, data, and services in a complete *project*. By creating a project, all of the required parts of your app and the added services are maintained on the {{site.data.keyword.cloud_notm}} server. You can download your app code and the required credentials and initializers if the services are configured into your project. You can view all of your projects by selecting **Projects**.  

You can view additional information about a single project by selecting it on the **Projects** page. This displays the **Project Overview** page, which includes the services that are associated with the project. Services are separate capabilities that extend your app by adding a function. Because they are added individually, you can add the services that you need, like push services, authentication, data and storage, or other services. When you add a service to your project on the **Project Overview** page and follow the instructions to configure it, it is automatically associated with your app.


### Project Overview page
{: #project_overview}

Once you have logged on, you can view and work with a single {{site.data.keyword.dev_console}} project by selecting the project on the **Projects** page, which opens the Project Overview page.
{: shortdesc}

The **Project Overview** page displays an entry for each service that is configured for the selected project. For each service entry bound to your projetc, you will see its name, a link for further documentation, and an *actions* button with three vertically-aligned dots. The *actions* button options are to remove service from project, open dashboard for service, and delete service. Please note that removing a service instance only removes the association to this project and does not delete the service instance.

Examples of service types that might be available include {{site.data.keyword.mobilepushshort}}, Security, or Data and Storage. The Project Overview page also allows you to add new services to your project. The available services are dependent on the type of project and the services that are available in that region, so not all services will be available to associate with all projects.

For convenience, the credentials for the services associated with your project are shown on the **Project Overview** page under the **Credentials** section.

Select **Download Code** to generate and download the code for your project. For more information about downloading the code, see [Get code](get_code.html).

Also, note that you can deploy your project to {{site.data.keyword.cloud_notm}} by clicking on the *Create Toolchain* button.


## Starter kits
{: #starters}

With the {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}}, you can choose from a variety of starter kits for each pattern type.

Starter kits are optimized to be production ready starter code that focuses on demonstrating a key pattern implementation using a runtime (e.g Node.js + Express). In some cases, starters offer a simple user experience to highlight the integration of the service data or interactions with the user. Each starter can be configured to be enabled with Authentication, Data, and possibly other capabilities, if you decide to configure them for your project. In other words, high-value services can be added to projects you create from starter kits.


## Pattern types
{: #patterns}

Cloud-native patterns are proven designs that help ensure a consistent, scalable, and reliable topology for your applications. When you create a project from a starter kit, you are choosing one of different pattern types (e.g. Backend for Frontend) along with a runtime (e.g. Swift + Kitura) that you can choose from. After you select your project preferences by choosing a starter, a starter project is generated for you to edit, run or debug, and deploy locally or to {{site.data.keyword.Bluemix}}.


### Web App
{: #web}

Web projects add the ability to serve web content such as HTML, JavaScript, and stylesheets to the web server. There are several Web App starter kits that you can leverage such as:

* Basic: serves a static `index.html` file, default and empty stylesheet, and JavaScript file.
* React: a rich framework to build user interfaces. The source files are in `src/client/app`, and will be compiled with WebPack and served in the public directory.


### Backend for Frontend (BFF)
{: #bff}

Backend for Frontend patterns, commonly known as BFFs, help you to focus on exposing business data and services in a form that matches the user interaction requirements. To optimize a user journey to your cloud solution, it may require a different user journey for the mobile application and a richer, more detailed journey for the Web application. With the introduction of voice-controlled devices like the [{{site.data.keyword.conversationfull}} ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/conversation.html) service, the interaction with a user could be controlled by voice. This digital channel will require a very different BFF for managing these voice intent-based interactions.

With {{site.data.keyword.cloud_notm}}, you can build a BFF by using polyglot programming approach to define the BFF. IBM recommends using Node.js, Swift, Java, or Python and running them in a cloud native pattern with either Cloud Foundry, Container services, or serverless.

The BFF will manage the integration with services for data persistence, caching, and integration with high-value services like {{site.data.keyword.ibmwatson}}, {{site.data.keyword.iot_short_notm}}, {{site.data.keyword.weather_short}}, and data analytics like {{site.data.keyword.sparks}}.

The BFF will expose an API most commonly using a REST pattern, but you can design your BFF to work from a messaging architecture using {{site.data.keyword.messagehub}}.

There are several BFF starter kits that you can choose from depending on your language and framework requirements.


### Microservice
{: #microservice}

Microservice projects provide the foundation for building backend microservices, including a basic health endpoint, a REST API. Generated projects will contain all dependencies required both for the microservice itself, as well as for any attached cloud service.

There are several Microservice starter kits that you can choose from depending on your language and framework requirements.

<!--
## Other
{: #other}

The Other pattern represents a project that consists of only the language-specific server-side web framework. It has all the other file assets to work with the project, such as needed libraries and config files.

Content to be provided by Karl Bishop.
-->


### Languages
{: #languages notoc}

Supported languages are:

   * [Java ![External link icon](../icons/launch-glyph.svg "External link icon")](../runtimes/liberty/getting-started.html){: new_window}
   * [Node.js ![External link icon](../icons/launch-glyph.svg "External link icon")](../runtimes/nodejs/getting-started.html){: new_window}
   * [Swift ![External link icon](../icons/launch-glyph.svg "External link icon")](../runtimes/swift/getting-started.html){: new_window}
   * [Python ![External link icon](../icons/launch-glyph.svg "External link icon")](../runtimes/python/getting-started.html){: new_window}


#### Java
{: #java notoc}

Java has proven capabilities for building enterprise-grade applications. But new capabilities in Java 8, combined with lighter weight runtimes like Liberty and frameworks like Spring Boot, make Java perfectly suited for building microservices too.


#### Node.js
{: #node notoc}

Node.js is a JavaScript runtime that uses an event-driven, non-blocking I/O model, making it lightweight and efficient, excelling in throughput and scalability for Web applications, backend-for-front-end patterns, and microservices. Node.js' package ecosystem, npm, provides access to a large collection of open source modules, providing a wide range of capabilities to accelerate your application development.


#### Swift
{: #swift notoc}

Swift is a modern programming language created by Apple in 2014 that was designed to replace the use of Objective C and open sourced in December of 2015. Today, it is used to build iOS, macOS, web services, and systems software on Linux and macOS operating systems using the x86, ARM, or Z architecture. It writes like a scripting language but is compiled to gain C-like high performance with low overhead making it ideal for cloud runtimes. It uses a strong and static type system that you see in Java but the functional style and asynchronous routines that you see in JavaScript. It is very performant, and the source compiles to native code using the LLVM compiler toolchain and can leverage foreign system libraries written in C easily.


#### Python
{: #python notoc}

Python is a general-purpose, interpreted programming language that puts a lot of emphasis on readability. Because of this, Python allows programmers implement functionality with fewer lines of code than might be required in other languages. Features in the language makes it possible to write object-oriented, functional, or imperative code. Python is commonly used for processing of natural language tasks.


## Services
At the moment, our starter kits generate scaffolding code for the services listed under the **Resources** page. If you choose to associate any of the services listed on that page with your application, you can then download code that includes scaffolding code for accessing those services from the application.
