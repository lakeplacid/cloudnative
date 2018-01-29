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

El {{site.data.keyword.dev_cli_long}} proporciona un enfoque basado en mandatos extensibles para crear, desarrollar y desplegar un proyecto web con el plugin `dev`. Ideal para desarrolladores que prefieren utilizar el control de línea de mandatos para desarrollar aplicaciones de microservicios completas.

{: shortdesc}

El {{site.data.keyword.dev_cli_notm}} utiliza dos contenedores para facilitar la creación y la realización de pruebas de su aplicación. El primero es el contenedor de herramientas que contiene las utilidades necesarias para crear y probar la aplicación. El Dockerfile para este contenedor está definido por el parámetro [`dockerfile-tools`](#command-parameters). Puede considerarlo como un contenedor de desarrollo, ya que contiene las herramientas que suelen utilizarse para el desarrollo de un tiempo de ejecución determinado.

El segundo contenedor es el contenedor de ejecución. El formato de este contenedor es adecuado para desplegarlo y utilizarlo en, por ejemplo, {{site.data.keyword.Bluemix}}. Como resultado, se define un punto de entrada que inicia su aplicación. Al seleccionar ejecutar la aplicación a través de {{site.data.keyword.dev_cli_short}}, utiliza este contenedor. El Dockerfile para este contenedor está definido por el parámetro [`dockerfile-run`](#run-parameters).


## Adición de {{site.data.keyword.dev_cli_notm}}
{: #add-cli}


### Requisitos previos
{: #prereq}

Debe obtener algunos requisitos previos para explorar completamente y utilizar correctamente el {{site.data.keyword.dev_cli_short}}, ya que es muy ampliable para utilizar tecnologías complementarias.

<!--1. Install the [Cloud Foundry CLI ![External link icon](../icons/launch-glyph.svg "External link icon")](https://github.com/cloudfoundry/cli#getting-started "External link icon").-->

1. Instale [{{site.data.keyword.Bluemix}} CLI ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](http://clis.ng.bluemix.net/ui/home.html "Icono de enlace externo").

2. Obtenga un [ID de {{site.data.keyword.Bluemix_notm}}](https://www.bluemix.net).

3. Si tiene intención de ejecutar y depurar aplicaciones a nivel local, deberá instalar también [Docker ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://www.docker.com/get-docker "Icono de enlace externo").


### Antes de empezar
{: #before-install}

1. Conecte con un punto final de API de la región de [{{site.data.keyword.Bluemix_notm}}](/docs/overview/whatisbluemix.html#ov_intro_reg). Por ejemplo, escriba el siguiente mandato para conectar con la región de {{site.data.keyword.Bluemix_notm}} EE.UU. Sur:

	```
	bx api https://api.ng.bluemix.net
	```
	{: codeblock}
	
2. Inicie sesión en {{site.data.keyword.Bluemix_notm}} especificando su ID de IBM y contraseña:

	```
	bx login
	```
	{: codeblock}
	
	**Nota:** si se rechazan sus credenciales, puede que esté utilizando un ID federado. Siga estos pasos para autenticarse mediante un ID federado.
	
	<!-- 
	POINT TO IBM Cloud CLI LOG IN DOCUMENTATION !!!
	
	This link does not work in production yet --> 
	
	1. Inicie sesión en [{{site.data.keyword.iamshort}} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://www.bluemix.net/iam/#/apikeys "Icono de enlace externo"){: new_window}.
	2. Seleccione **Crear clave de API**.
		* Especifique un nombre y descripción para la clave de API
	3. Descargue su clave de API.
	4. Abra el archivo y copie el valor del campo `apiKey`.
	5. Inicie sesión utilizando el siguiente mandato:
	 
		```
		bx login --apikey <value>
		```
		{: codeblock}


### Instalación
{: #installation}

1. Instale el [{{site.data.keyword.dev_cli_short}} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](/docs/cli/reference/bluemix_cli/index.html#install_plug-in "Icono de enlace externo"){: new_window} ejecutando el siguiente mandato:
 
	```
	bx plugin install dev
	```
	{: codeblock}

2. 	Valide la correcta instalación del plugin ejecutando el siguiente mandato:  
 
	```
	bx dev
	```
	{: codeblock}


