---
product: campaign
title: Integración en un servidor web para Windows
description: Integración en un servidor web para Windows
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Solo se aplica a Campaign Classic v7"
badge-v7-prem: label="on-premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 041c4431-baae-4e64-9e9a-0daa5123bd8a
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 6%

---

# Integración en un servidor web para Windows{#integration-into-a-web-server-for-windows}



Adobe Campaign incluye Apache Tomcat, que actúa como punto de entrada en el servidor de aplicaciones a través de HTTP (y SOAP).

Puede utilizar este servidor Tomcat integrado para servir solicitudes HTTP.

En este caso:

* el puerto de escucha predeterminado es 8080. Para cambiarlo, consulte [esta sección](../../installation/using/configure-tomcat.md).
* A continuación, las consolas de cliente se conectan mediante una dirección URL como ```https:// `<computer>`:8080```.

Sin embargo, por motivos de seguridad y administración, se recomienda utilizar un servidor Web específico como punto de entrada principal para el tráfico HTTP cuando el equipo que ejecuta Adobe Campaign está expuesto en Internet y desea abrir el acceso a la consola fuera de la red.

Un servidor web también permite garantizar la confidencialidad de los datos con el protocolo HTTP.

Del mismo modo, debe utilizar un servidor web cuando desee utilizar la funcionalidad de seguimiento, que solo está disponible como módulo de extensión de servidor web.

>[!NOTE]
>
>Si no utiliza la funcionalidad de seguimiento, puede realizar una instalación estándar de Apache o IIS con una redirección a Campaign. El módulo de extensión del servidor web de seguimiento no es obligatorio.

## Configurar el servidor web de IIS {#configuring-the-iis-web-server}

El procedimiento de configuración de un servidor Web IIS es principalmente gráfico. Implica utilizar un sitio web (ya creado o pendiente de creación) para acceder a los recursos del servidor de Adobe Campaign: archivos Java (.jsp), hojas de estilo (.css, .xsl), imágenes (.png), el archivo DLL ISAPI para redireccionamiento, etc.

Las secciones siguientes detallan la configuración en IIS 7. La configuración para IIS8 es básicamente la misma.

Si el servidor IIS web no está instalado en el equipo, puede instalarlo mediante el **[!UICONTROL Add > Remove Programs > Enable or disable Windows functionalities]** menú.

En IIS 7, además de los servicios estándar, debe instalar las extensiones ISAPI y los filtros ISAPI.

![](assets/s_ncs_install_iis7_isapi.png)

### Pasos de configuración {#configuration-steps}

Aplique los siguientes pasos de configuración:

1. Abra IIS a través de **[!UICONTROL Control panel > Administrative tools > Services]** menú.
1. Cree y configure el sitio (Adobe Campaign, por ejemplo) en función de los parámetros de su red (puerto de conexión TCP, host DNS, dirección IP).

   ![](assets/s_ncs_install_iis7_add_site.png)

   Debe especificar al menos el nombre del sitio y la ruta de acceso al directorio virtual. Dado que no se utiliza la ruta de acceso al directorio del sitio Web, puede utilizar el siguiente directorio.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. A **VBS** El script de le permite configurar automáticamente los recursos utilizados por el servidor de Adobe Campaign en el directorio virtual que acabamos de crear. Para iniciarlo, haga doble clic en **iis_neolane_setup.vbs** archivo ubicado en el `[INSTALL]\conf` carpeta, donde `[INSTALL]` es la ruta para acceder a la carpeta de instalación de Adobe Campaign.

   ![](assets/s_ncs_install_iis7_parameters_step2.png)

   >[!NOTE]
   >
   >En el caso de una instalación de Windows Server 2008/IIS7, debe iniciar sesión como administrador para ejecutar la secuencia de comandos VBS o ejecutarla como administrador.

   Clic **[!UICONTROL OK]** si el servidor web se utiliza como servidor de redirección de seguimiento, en caso contrario, haga clic en **[!UICONTROL Cancel]**.

   Cuando ya hay varios sitios configurados en el servidor Web, se muestra una página intermedia para especificar a qué sitio Web se aplica la instalación: introduzca el número vinculado al sitio y haga clic en **[!UICONTROL OK]**.

   ![](assets/s_ncs_install_iis7_parameters_step3.png)

   Se debe mostrar un mensaje de confirmación:

   ![](assets/s_ncs_install_iis7_parameters_step7.png)

1. En el **[!UICONTROL Content View]** , asegúrese de que el sitio web está correctamente configurado con los recursos de Adobe Campaign:

   ![](assets/s_ncs_install_iis7_parameters_step6.png)

   Si no se muestra el árbol, reinicie IIS.

### Administración de derechos {#managing-rights}

A continuación, debe establecer la configuración de seguridad de la DLL ISAPI y de los recursos del directorio de instalación de Adobe Campaign.

Para ello, siga los siguientes pasos:

1. Seleccione el **[!UICONTROL Features View]** y haga doble clic en **Autenticación** vínculo.

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. En el **Seguridad de directorio** del sitio web, asegúrese de que el acceso anónimo está habilitado. Si es necesario, haga clic en **[!UICONTROL Edit]** para cambiar la configuración.

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### Inicio del servidor web y prueba de la configuración {#launching-the-web-server-and-testing-the-configuration}

Ahora debe probar si la configuración es correcta.

Para ello, siga el siguiente procedimiento:

1. Reinicie el servidor IIS con el **iisreset** línea de comandos.

1. Inicie el servicio de Adobe Campaign y asegúrese de que se esté ejecutando.

1. Pruebe el módulo de seguimiento insertando la siguiente URL en un explorador web:

   ```
   https://<computer>/r/test
   ```

   El explorador debe mostrar la siguiente respuesta:

   ```
   <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='myserver.mydomain.com' localHost='localhost'/>
   ```

Para comprobar la presencia del módulo de redirección, ejecute la siguiente línea de comandos:

```
nlserver pdump
```

Debe devolver la siguiente información:

```
12:00:33 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

También puede asegurarse de que el archivo DLL ISAPI está cargado correctamente.

Para ello, siga los siguientes pasos:

1. Edite los filtros ISAPI para el sitio de Adobe Campaign haciendo clic en **[!UICONTROL Driver mapping]** icono.
1. A continuación, compruebe el contenido del filtro ISAPI:

   ![](assets/s_ncs_install_iis7_parameters_step11.png)

## Configuraciones adicionales {#additional-configurations}

### Cambio del límite de tamaño de archivo de carga {#changing-the-upload-file-size-limit}

Al configurar el servidor Web de IIS, se establece automáticamente un límite de aproximadamente 28 MB para los archivos configurados que se cargan en el servidor.

Esto puede afectar a Adobe Campaign, especialmente si desea cargar archivos que superen este límite.

Por ejemplo, si utiliza un **Carga de datos (archivo)** Escriba la actividad en un flujo de trabajo para importar un archivo de 50 MB. Un error evitará que el flujo de trabajo se ejecute correctamente.

En este caso, debe aumentar este límite:

1. Abra IIS a través de **[!UICONTROL Start > (Control panel) > Administration tools]** menú.
1. En el **Conexiones** , seleccione el sitio creado para la instalación de Adobe y, a continuación, haga doble clic en **Filtrado de solicitudes** en el panel principal.
1. En el **Acciones** panel, seleccione **Editar configuración de funciones** para poder editar el valor en la variable **Tamaño máximo de contenido autorizado (bytes)** field.

   Por ejemplo, para autorizar la carga de archivos de 50 MB, debe especificar un valor de más de &quot;52428800&quot; bytes.

>[!NOTE]
>
>Para obtener más información sobre esta opción de IIS, consulte la sección &quot;Cómo&quot; del [documentación oficial](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits).

