---

copyright:
  years: 2016, 2017
lastupdated: "2017-06-27"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# Novedades de la {{site.data.keyword.dev_console}} de {{site.data.keyword.Bluemix_notm}}
{: #what-is-new}


## Novedades de junio de 2017
{: #june-2017}

La actualización de junio de 2017 de la {{site.data.keyword.dev_console}} de {{site.data.keyword.Bluemix}} ha introducido los siguientes cambios:

   * Ahora los iniciadores de dispositivos móviles pueden gestionar los servicios {{site.data.keyword.ibmwatson}} necesarios e inyectar credenciales de servicio en el proyecto. 
   * La {{site.data.keyword.dev_cli_long}} se ha actualizado con nuevas características. Para obtener más información, consulte [Lo que se incluye en la CLI de {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.dev_cli_short}} versión 0.1.12 ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/blogs/bluemix/2017/06/whats-included-bluemix-cli-developer-plug-version-0-1-12/ "Icono de enlace externo").

## Novedades de marzo de 2017
{: #mar-2017}

La actualización de marzo de 2017 de la {{site.data.keyword.dev_console}} de {{site.data.keyword.Bluemix_notm}} incorporaba los siguientes cambios: 

   * El panel de control de Mobile en {{site.data.keyword.Bluemix_notm}} ahora es la {{site.data.keyword.dev_console}} de {{site.data.keyword.Bluemix_notm}}.
   * Se ha rediseñado la creación de proyectos para incluir los tipos de patrón de servidor de app web, BFF y microservicio con soporte para Node.js, Java y Swift.
   * La integración con el nuevo y mejorado servicio de {{site.data.keyword.appid_full}} proporciona autenticación para proyectos web y móvil.
   * Ahora puede generar los SDK para sus proyectos utilizando el [plugin del generador de SDK](sdk_cli.html). La generación de SDK en la {{site.data.keyword.dev_console}} solo está disponible para proyectos móviles.
   * Ahora puede crear proyectos mediante [{{site.data.keyword.dev_cli_short}}](dev_cli.html).


## Novedades de enero de 2017
{: #jan-2017}

La actualización de enero de 2017 del panel de control de {{site.data.keyword.Bluemix_notm}} Mobile ha introducido los cambios siguientes:

   * A partir del 31 de enero, los Iniciadores de la IU estarán en desuso. Los proyectos existentes creados a partir de un Iniciador de IU se pueden utilizar hasta el 30 de abril de 2017. Para obtener más información sobre los pasos de migración y las fechas de eliminación, consulte la [publicación de blog del anuncio en desuso ![icono de enlace externo](../icons/launch-glyph.svg "icono de enlace externo")](https://www.ibm.com/blogs/bluemix/2017/01/bluemix-mobile-dashboard-update/ "icono de enlace externo").
{: deprecated}
   * Ahora puede actualizar el tipo de iniciador del proyecto en lugar de suprimir el proyecto y crear uno nuevo.
   * Ahora puede crear el proyecto con un Iniciador de código [Conversation de Watson](tutorial_conversation.html).
   * Si se admite, ahora puede generar un SDK para el proyecto.
   * Ahora puede añadir las instancias existentes de [Cálculo](sdk_compute.html) y generar SDK de clientes para añadir al proyecto.


## Novedades de diciembre de 2016
{: #dec-2016}

La actualización de diciembre de 2016 del panel de control de {{site.data.keyword.Bluemix_notm}} Mobile ha introducido los cambios siguientes:

   * Ahora puede eliminar un servicio conectado de un proyecto para que se pueda suprimir y reutilizar con otro proyecto. 
   * Ahora puede añadir un servicio existente a un proyecto.
   * Ahora puede crear o conectar un servicio CloudantNoSQL existente como origen de datos cuando utilice un Iniciador de código.
   * Si se admite, ahora puede crear o conectar un servicio Object Storage existente como origen de datos para el proyecto.
   * Ahora puede personalizar el diseño de navegación de la app que cree con un Iniciador de IU. 
   

## Novedades de noviembre de 2016
{: #nov-2016}

La actualización de noviembre de 2016 del panel de control de {{site.data.keyword.Bluemix_notm}} Mobile ha introducido los cambios siguientes:

   * Ahora puede generar artefactos SDK para proyectos desde la página **Código**.
   * Ahora se admite Cordova para el iniciador de código de Basic.
   * Ahora puede [notificar sucesos de red ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](/docs/services/mobileanalytics/sdk.html#network-requests "Icono de enlace externo"){: new_window} y [supervisar solicitudes de red ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](/docs/services/mobileanalytics/app-monitoring.html#monitor-network-requests "Icono de enlace externo"){: new_window} en la página **Solicitudes de red** de la consola de {{site.data.keyword.mobileanalytics_short}}.
   * Ahora puede [exportar datos a dashDB ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](/docs/services/mobileanalytics/app-monitoring.html#dashdb "Icono de enlace externo"){: new_window} en la consola de {{site.data.keyword.mobileanalytics_short}}.


## Novedad de octubre de 2016
{: #oct-2016}

La actualización de octubre de 2016 del panel de control de {{site.data.keyword.Bluemix_notm}} Mobile ha introducido los cambios siguientes:

   * Ahora puede añadir prestaciones de {{site.data.keyword.mobilepushshort}} y Analytics al proyecto directamente desde el panel de control.
   * Ahora están disponibles los Iniciadores de código.
   * Puede añadir autenticación a sus proyectos que ha creado a partir de un iniciador de código.
   * Ahora se da soporte a Swift.


### Analítica
{: #analytics notoc}

   * La modalidad de demostración está habilitada de forma predeterminada al añadir la prestación Analytics. Puede desactivar la modalidad de demostración para ver las analíticas tras ejecutar la app.


### Creador de IU
{: #ui_builder notoc}

   * Ahora se accede a la prestación **{{site.data.keyword.mobilepushshort}}** desde el proyecto.
   * Se ha cambiado el nombre del separador **Valores del proyecto** por **Valores**.
   * Se ha cambiado el nombre del separador **Autenticación** por **Acceso de usuarios**.


### Código
{: #code notoc}

   * El código generado de Objective-C y Swift para iOS utiliza ahora CocoaPods para gestionar las dependencias, así que debe instalarlo. Para instalar CocoaPods, ejecute `sudo gem install cocoapods`. Una vez que CocoaPods se haya instalado, ejecute `pod setup` para configurarlo (si aún no se ha configurado). Finalmente, ejecute `pod install` para descargar e instalar las dependencias del proyecto antes de abrir el archivo `.xcworkspace` en Xcode. Hay más detalles disponibles en el archivo `README.md` en el archivador de código descargado. Consulte sobre las [Herramientas necesarias del desarrollador](get_code.html#prereq-dev-tools) para obtener más información.

Consulte con frecuencia para estar al corriente de las nuevas actualizaciones.
