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

# Guía de aprendizaje del iniciador Microservice Basic
{: #tutorial}

En la siguiente guía de aprendizaje encontrará los pasos a seguir para crear un proyecto desde el iniciador Microservice Basic. Las instrucciones incluyen la instalación de las herramientas necesarias y los pasos a seguir para ejecutar el código del proyecto. 


## Instalación de herramientas del desarrollador
{: #dev_tools}

Asegúrese de instalar las [herramientas de desarrollador necesarias ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](get_code.html#prereq-dev-tools "Icono de enlace externo"){: new_window}.


## Elija cómo desea crear su proyecto
{: #choose_how}

Puede crear un proyecto utilizando la [{{site.data.keyword.dev_console}}](#create-devex) basada en la web o la [{{site.data.keyword.dev_cli_notm}}](#create-cli) de mandatos. Una vez creado el proyecto, podrá [ejecutar el proyecto](#running-dev-plugin).


## Creación de un proyecto mediante la {{site.data.keyword.dev_console}}
{: #create-devex}

1. Cree un proyecto en la {{site.data.keyword.dev_console}} de {{site.data.keyword.Bluemix}}.

	1. En la página [**Iniciación** ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/developer/getting-started/ "Icono de enlace externo") de la {{site.data.keyword.dev_console}}, pulse **Crear proyecto**.

		De forma alternativa, puede pulsar **Crear proyecto** desde la página **Proyectos**.

	2. Seleccione **Microservicio** y pulse **Siguiente**.

	3. Seleccione **Basic** y pulse **Siguiente**.

	4. Especifique el nombre del proyecto. En esta guía de aprendizaje, utilizaremos `MicroserviceProject`.   

	5. Escriba un nombre de host exclusivo, como por ejemplo sus iniciales seguidas de `-devhost`. Por ejemplo:
	
	 ```
	 abc-devhost
	 ```
	   
	6. Pulse **Crear**.

2. Opcional: Añada la capacidad de Datos.

	1. Pulse **Ver** para **Datos** en la página **Visión general del proyecto**.

      De forma alternativa, puede seleccionar **Crear** o **Añadir existente** en la página **Prestaciones > Data**.

   2. Especifique el nombre del servicio y pulse **Crear**.

3. Genere el código del proyecto:

	1. Pulse **Obtener el código** en la página **Visión general del proyecto** para seleccionar el lenguaje.
   
		Como alternativa, pulse la página **Código**.
      
	2. Pulse **Generar código**.
   
	3. Cuando se haya generado el código, pulse **Descargar código** para descargar el archivo del proyecto.

4. Empiece a trabajar con el proyecto descargado:

	1. Expanda el archivo archivado.
	
	2. Vaya al directorio del nuevo proyecto.
	
	3. Utilice {{site.data.keyword.dev_cli_notm}} para continuar.

5. Opcional: [Actualización del proyecto](project_overview_page.html#update_language) para generar un nuevo lenguaje.


## Creación de un proyecto mediante la {{site.data.keyword.dev_cli_notm}}
{: #create-cli}

1. Asegúrese de instalar [{{site.data.keyword.dev_cli_short}}](dev_cli.html).

2. En la solicitud de terminal, vaya al directorio local que prefiera y ejecute el siguiente mandato.
  
	```
	bx dev create
	```
	{: codeblock}

3. Proporcione los siguientes valores cuando se le solicite:

	* Seleccione un patrón: 4 (para Microservicios)
	* Seleccione un iniciador: 1 (para Basic)
	* Seleccione una plataforma: 1 (para Java)
	* Especifique un nombre para el proyecto: `MicroserviceProjectCLI`
	* Especifique un nombre de host para el proyecto: `abc-devhost`
	  * Escriba un nombre de host exclusivo, como por ejemplo sus iniciales seguidas de `-devhost`. Por ejemplo:
	
	     ```
	     abc-devhost
	     ```

4. Cuando `MicroserviceProjectCLI` se haya guardado correctamente, vaya a la carpeta `MicroserviceProjectCLI`.

5. Ahora puede añadir su propio código o ejecutar el proyecto.
 
 
## Ejecución del proyecto utilizando {{site.data.keyword.dev_cli_notm}}
{: #running-dev-plugin}

1. Para crear el proyecto en el directorio de proyecto actual, escriba el siguiente mandato:

	```
	bx dev build
	```     
	{: codeblock}

2. Para ejecutar el proyecto en el directorio de proyecto actual, escriba el siguiente mandato:

	```
	bx dev run
	```
	{: codeblock}	

3. Puede acceder a la aplicación utilizando `curl` en el servidor:

	```
	curl http://localhost:8080	
	```
	{: codeblock}
