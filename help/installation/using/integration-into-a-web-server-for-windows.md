---
solution: Campaign Classic
product: campaign
title: Integración en un servidor web para Windows
description: Integración en un servidor web para Windows
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 4%

---


# Integración en un servidor web para Windows{#integration-into-a-web-server-for-windows}

Adobe Campaign incluye Apache Tomcat que actúa como punto de entrada en el servidor de aplicaciones mediante HTTP (y SOAP).

Puede utilizar este servidor Tomcat integrado para servir solicitudes HTTP.

En este caso:

* el puerto de escucha predeterminado es 8080. Para cambiarlo, consulte [Configuración de Tomcat](../../installation/using/configuring-campaign-server.md#configuring-tomcat).
* Las consolas de cliente se conectan mediante una dirección URL como [https:// `<computer>`:8080](https://myserver.adobe.com:8080).

Sin embargo, por razones de seguridad y administración, recomendamos utilizar un servidor Web dedicado como punto de entrada principal para el tráfico HTTP cuando el equipo que ejecuta Adobe Campaign se expone en Internet y desea abrir el acceso a la consola fuera de la red.

Un servidor Web también permite garantizar la confidencialidad de los datos con el protocolo HTTP.

Del mismo modo, debe utilizar un servidor Web cuando desee utilizar la funcionalidad de seguimiento, que sólo está disponible como módulo de extensión de servidor Web.

>[!NOTE]
>
>Si no utiliza la funcionalidad de seguimiento, puede realizar una instalación estándar de Apache o IIS con una redirección a la Campaña. No se requiere el módulo de extensión del servidor Web de seguimiento.

## Configuración del servidor Web IIS {#configuring-the-iis-web-server}

El procedimiento de configuración para un servidor Web IIS es principalmente gráfico. Implica utilizar un sitio Web (ya creado o pendiente de creación) para acceder a los recursos del servidor de Adobe Campaign: Archivos Java (.jsp), hojas de estilo (.css, .xsl), imágenes (.png), la DLL ISAPI para redirección, etc.

Las secciones siguientes detallan la configuración en IIS 7. La configuración de IIS8 es básicamente la misma.

Si el servidor Web IIS no está instalado en el equipo, puede instalarlo mediante el menú **[!UICONTROL Add > Remove Programs > Enable or disable Windows functionalities]**.

En IIS 7, además de los servicios estándar, debe instalar las extensiones ISAPI y los filtros ISAPI.

![](assets/s_ncs_install_iis7_isapi.png)

### Pasos de configuración {#configuration-steps}

Aplique los siguientes pasos de configuración:

1. Abra IIS mediante el menú **[!UICONTROL Control panel > Administrative tools > Services]**.
1. Cree y configure el sitio (por ejemplo, Adobe Campaign) en función de los parámetros de la red (puerto de conexión TCP, host DNS, dirección IP).

   ![](assets/s_ncs_install_iis7_add_site.png)

   Debe especificar al menos el nombre del sitio y la ruta de acceso al directorio virtual. Como no se utiliza la ruta para acceder al directorio del sitio web, puede utilizar el siguiente directorio.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. Una secuencia de comandos **VBS** permite configurar automáticamente los recursos utilizados por el servidor de Adobe Campaign en el directorio virtual que acabamos de crear. Para iniciarlo, doble haga clic en el archivo **is_neolane_setup.vbs** ubicado en la carpeta `[INSTALL]\conf`, donde `[INSTALL]` es la ruta para acceder a la carpeta de instalación de Adobe Campaign.

   ![](assets/s_ncs_install_iis7_parameters_step2.png)

   >[!NOTE]
   >
   >En el caso de una instalación de Windows Server 2008/IIS7, debe iniciar sesión como administrador para ejecutar la secuencia de comandos de VBS o ejecutar la secuencia de comandos como administrador.

   Haga clic en **[!UICONTROL OK]** si el servidor Web se utiliza como servidor de redirección de seguimiento; de lo contrario, haga clic en **[!UICONTROL Cancel]**.

   Cuando ya hay varios sitios configurados en el servidor Web, se muestra una página intermedia para especificar a qué sitio Web se aplica la instalación: introduzca el número vinculado al sitio y haga clic en **[!UICONTROL OK]**.

   ![](assets/s_ncs_install_iis7_parameters_step3.png)

   Se debe mostrar un mensaje de confirmación:

   ![](assets/s_ncs_install_iis7_parameters_step7.png)

1. En la ficha **[!UICONTROL Content View]**, asegúrese de que el sitio Web esté correctamente configurado con los recursos de Adobe Campaign:

   ![](assets/s_ncs_install_iis7_parameters_step6.png)

   Si no se muestra el árbol, reinicie IIS.

### Administración de derechos {#managing-rights}

A continuación, debe configurar la configuración de seguridad para la DLL ISAPI y para los recursos del directorio de instalación de Adobe Campaign.

Para ello, siga los siguientes pasos:

1. Seleccione la ficha **[!UICONTROL Features View]** y haga clic con el doble en el vínculo **Autenticación**.

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. En la ficha **Seguridad del directorio** del sitio Web, asegúrese de que el acceso anónimo esté habilitado. Si es necesario, haga clic en el vínculo **[!UICONTROL Edit]** para cambiar la configuración.

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### Inicio del servidor Web y prueba de la configuración {#launching-the-web-server-and-testing-the-configuration}

Ahora debe probar si la configuración es correcta.

Para ello, siga el procedimiento siguiente:

1. Reinicie el servidor IIS mediante la línea de comandos **iisreset**.
1. Pruebe el módulo de seguimiento insertando la siguiente dirección URL en un explorador Web:

   ```
   https://<computer>/r/test
   ```

   El explorador debe mostrar la siguiente respuesta:

   ```
   <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='myserver.mydomain.com' localHost='localhost'/>
   ```

Para probar la presencia del módulo de redirección, ejecute la siguiente línea de comandos:

```
nlserver pdump
```

Debe devolver la siguiente información:

```
12:00:33 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

También puede asegurarse de que el archivo DLL ISAPI esté correctamente cargado.

Para ello, siga los siguientes pasos:

1. Edite los filtros ISAPI para el sitio Adobe Campaign haciendo clic en el icono **[!UICONTROL Driver mapping]**.
1. Comprobar el contenido del filtro ISAPI:

   ![](assets/s_ncs_install_iis7_parameters_step11.png)

## Configuraciones adicionales {#additional-configurations}

### Cambio del límite de tamaño del archivo de carga {#changing-the-upload-file-size-limit}

Al configurar el servidor Web IIS, se establece automáticamente un límite de aproximadamente 28 MB para los archivos que se cargan en el servidor.

Esto puede tener un impacto en Adobe Campaign, especialmente si desea cargar archivos que superen este límite.

Por ejemplo, si utiliza una actividad de tipo **Carga de datos (archivo)** en un flujo de trabajo para importar un archivo de 50 MB, un error impedirá que el flujo de trabajo se ejecute correctamente.

En este caso, debe aumentar este límite:

1. Abra IIS mediante el menú **[!UICONTROL Start > (Control panel) > Administration tools]**.
1. En el panel **Conexiones**, seleccione el sitio creado para la instalación de Adobe y, a continuación, haga clic con el doble en **Filtrado de solicitudes** en el panel principal.
1. En el panel **Acciones**, seleccione **Editar configuración de funciones** para poder editar el valor en el campo **Tamaño máximo de contenido autorizado (bytes)**.

   Por ejemplo, para autorizar la carga de archivos de 50 MB, debe especificar un valor de más de &quot;52428800&quot; bytes.

>[!NOTE]
>
>Para obtener más información sobre esta opción de IIS, consulte la sección &quot;Cómo&quot; de la [documentación oficial](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits).

### Configuración de la visualización de mensajes de error http {#configuring-http-error-message-display}

Si utiliza un servidor IIS de la versión 6.1, los mensajes de error generados pueden ser difíciles de leer debido a que se muestra un código HTML no deseado en el mensaje.

Para solucionar este problema y mostrar el error correctamente, aplique la siguiente configuración:

1. Abra IIS mediante el menú **[!UICONTROL Start > Control Panel > Administrative tools]**.
1. En el panel **Conexiones**, seleccione el sitio creado para la instalación de Adobe Campaign y, a continuación, haga clic con el botón de doble **Editor de configuración** en el panel principal.
1. En la lista desplegable **Section**, seleccione **system.webServer** > **httpErrors**.
1. Seleccione el valor **PassThrough** en la línea **existenteResponse**.

![](assets/ins_iis_httperrors.png)

