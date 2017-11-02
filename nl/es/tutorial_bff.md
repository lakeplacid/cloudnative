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

# Guía de aprendizaje del iniciador BFF Basic
{: #tutorial}

En la siguiente guía de aprendizaje encontrará los pasos a seguir para crear un proyecto desde el iniciador BFF Basic. Las instrucciones incluyen la instalación de las herramientas necesarias y los pasos a seguir para ejecutar el código del proyecto. 


## Instalación de herramientas del desarrollador
{: #dev_tools}

Asegúrese de instalar las [herramientas de desarrollador necesarias ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](get_code.html#prereq-dev-tools "Icono de enlace externo"){: new_window}.


## Elija cómo desea crear su proyecto
{: #choose_how}

Puede crear un proyecto utilizando la [{{site.data.keyword.dev_console}}](#create-devex) basada en la web o la [{{site.data.keyword.dev_cli_notm}}](#create-cli) de mandatos. Una vez creado el proyecto, podrá [ejecutar el proyecto](#running-bff).


## Creación de un proyecto mediante la {{site.data.keyword.dev_console}}
{: #create-devex}

1. Cree un proyecto en la {{site.data.keyword.dev_console}} de {{site.data.keyword.Bluemix}}.

	1. En la página [**Iniciación** ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/developer/getting-started/ "Icono de enlace externo") de la {{site.data.keyword.dev_console}}, pulse **Crear proyecto**.

		De forma alternativa, puede pulsar **Crear proyecto** desde la página **Proyectos**.

	2. Seleccione **Programa de fondo para programa de usuario** y pulse **Siguiente**.

	3. Seleccione **Programa de fondo básico** y pulse **Siguiente**.

	4. Especifique el nombre del proyecto. En esta guía de aprendizaje, utilizaremos `BFFProject`.   

	5. Escriba un nombre de host exclusivo, como por ejemplo sus iniciales seguidas de `-devhost`. Por ejemplo:
	
	 ```
	 abc-devhost
	 ``` 

	6. Seleccione el lenguaje de la plataforma. En esta guía de aprendizaje, utilizaremos `Node`.
   
	7. Pulse **Crear**.

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

	* Seleccione un patrón: 3 (para Programa de fondo para programa de usuario)
	* Seleccione un iniciador: 1 (para Programa de fondo básico)
	* Seleccione un lenguaje: 1 (para Node)
	* Especifique un nombre para el proyecto: `BFFProjectCLI`
	* Especifique un nombre de host para el proyecto: `abc-devhost`
	  * Escriba un nombre de host exclusivo, como por ejemplo sus iniciales seguidas de `-devhost`. Por ejemplo:
	
	     ```
	     abc-devhost
	     ```
	  
4. Después de guardar `BFFProjectCLI`, vaya a la carpeta `BFFProjectCLI`.

5. Añada su propio código, compile y ejecute el proyecto.
 
	1. Compile el proyecto con el siguiente mandato: 

		```
		bx dev build
		```
		{: codeblock}
		 
	2. Ejecute el proyecto con el siguiente mandato:

 		```
		bx dev run
		```
		{: codeblock}


## Ejecución de un proyecto BFF
{: #running-bff}

Puede ejecutar la aplicación localmente en el sistema host si instala las herramientas de compilación necesarias, o bien utilizando el soporte de contenedor disponible en {{site.data.keyword.dev_cli_notm}}.


### Utilización del plugin de IBM Cloud
{: #using-blumix}

1. Para compilar el proyecto en el directorio de proyecto actual, escriba el siguiente mandato:

   ```
   bx dev build
   ```
   {: codeblock}

2. Para ejecutar el proyecto en el directorio de proyecto actual, escriba el siguiente mandato:

   ```
   bx dev run
   ```
   {: codeblock}

3. Puede ejecutar curl en el servidor con:

   ```
   curl http://localhost:8080
   ```
   {: codeblock}

4. Puede ver el documento de la API en el servidor en:

   ```
   http://localhost:8080/swagger/api
   ```
   {: codeblock}

5. Puede explorar la API en el servidor en:

   ```
   http://localhost:8080/explorer
   ```
   {: codeblock}
