---
product: campaign
title: Integración en un servidor web para Windows
description: Integración en un servidor web para Windows
feature: Installation, Instance Settings
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 041c4431-baae-4e64-9e9a-0daa5123bd8a
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 4%

---

# Integración en un servidor web para Windows {#integration-into-a-web-server-for-windows}

Adobe Campaign SOAP incluye Apache Tomcat, que actúa como punto de entrada en el servidor de aplicaciones a través de HTTP (y el servidor de correo electrónico) (y el servidor de correo electrónico).

Puede utilizar este servidor Tomcat integrado para servir solicitudes HTTP.

En este caso:

* el puerto de escucha predeterminado es 8080. Para cambiarlo, consulte [esta sección](../../installation/using/configure-tomcat.md).
* Las consolas de cliente se conectan mediante una dirección URL como ```https:// `<computer>`:8080```.

Sin embargo, por motivos de seguridad y administración, se recomienda utilizar un servidor Web específico como punto de entrada principal para el tráfico HTTP cuando el equipo que ejecuta Adobe Campaign está expuesto en Internet y desea abrir el acceso a la consola fuera de la red.

Un servidor web también permite garantizar la confidencialidad de los datos con el protocolo HTTP.

Del mismo modo, debe utilizar un servidor web cuando desee utilizar la funcionalidad de seguimiento, que solo está disponible como módulo de extensión de servidor web.

## Configurar el servidor web de IIS {#configuring-the-iis-web-server}

El procedimiento de configuración para un servidor web IIS de Microsoft es principalmente gráfico. Implica utilizar un sitio Web para tener acceso a los recursos del servidor de Adobe Campaign: archivos Java (.jsp), hojas de estilo (.css, .xsl), imágenes (.png), el archivo DLL ISAPI para redireccionamiento, etc.


### Pasos de configuración {#configuration-steps}

Para integrar Adobe Campaign con el servidor web IIS de Microsoft, siga estos pasos:

1. Abra Microsoft IIS.
1. Cree y configure el sitio (Adobe Campaign, por ejemplo) en función de los parámetros de su red (puerto de conexión TCP, host DNS, dirección IP).

   Debe especificar al menos el nombre del sitio y la ruta de acceso al directorio virtual. Dado que no se utiliza la ruta de acceso al directorio del sitio Web, puede utilizar el siguiente directorio.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. Un script **VBS** le permite configurar automáticamente los recursos que usa el servidor de Adobe Campaign en el directorio virtual que acabamos de crear. Para iniciarlo, haga doble clic en el archivo **iis_neolane_setup.vbs** ubicado en la carpeta `[INSTALL]\conf`, donde `[INSTALL]` es la ruta de acceso a la carpeta de instalación de Adobe Campaign.

   >[!NOTE]
   >
   >Debe iniciar sesión como administrador para ejecutar el script VBS o ejecutar el script como administrador.

   Haga clic en **[!UICONTROL OK]** si el servidor web se utiliza como servidor de redirección de seguimiento; de lo contrario, haga clic en **[!UICONTROL Cancel]**.

   Cuando ya hay varios sitios configurados en el servidor web, se muestra una página intermedia para especificar a qué sitio web se aplica la instalación: escriba el número vinculado al sitio y haga clic en **[!UICONTROL OK]**.

1. En la ficha **[!UICONTROL Content View]**, asegúrese de que el sitio web está configurado correctamente con los recursos de Adobe Campaign:

   Si no se muestra el árbol, reinicie Microsoft IIS.

### Administración de derechos {#managing-rights}

A continuación, debe establecer la configuración de seguridad de la DLL ISAPI y de los recursos del directorio de instalación de Adobe Campaign.

Para ello, siga los siguientes pasos:

1. Seleccione la ficha **[!UICONTROL Features View]** y haga doble clic en el vínculo **Autenticación**.

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. En la ficha **Seguridad de directorios** del sitio web, asegúrese de que el acceso anónimo está habilitado. Si es necesario, haga clic en el vínculo **[!UICONTROL Edit]** para cambiar la configuración.

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### Inicio del servidor web y prueba de la configuración {#launching-the-web-server-and-testing-the-configuration}

Ahora debe probar si la configuración es correcta.

Para ello, siga el siguiente procedimiento:

1. Reinicie el servidor IIS de Microsoft con la línea de comandos **iisreset**.

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

```sql
HH:MM:SS >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

También puede asegurarse de que el archivo DLL ISAPI está cargado correctamente.

Para ello, siga los siguientes pasos:

1. Edite los filtros ISAPI para el sitio Adobe Campaign haciendo clic en el icono **[!UICONTROL Driver mapping]**.
1. A continuación, compruebe el contenido del filtro ISAPI.


## Cambio del límite de tamaño de archivo de carga {#changing-the-upload-file-size-limit}

Al configurar el servidor Web de IIS, se establece automáticamente un límite de aproximadamente 28 MB para los archivos configurados que se cargan en el servidor.

Esto puede afectar a Adobe Campaign, especialmente si desea cargar archivos que superen este límite.

Por ejemplo, si utiliza una actividad de tipo **Carga de datos (archivo)** en un flujo de trabajo para importar un archivo de 50 MB, un error impedirá que el flujo de trabajo se ejecute correctamente.

En este caso, debe aumentar este límite.

Para obtener más información sobre esta opción de IIS de Microsoft, consulte la sección &quot;HowTo&quot; de la [documentación de Microsoft](https://learn.microsoft.com/en-us/iis/configuration/system.webServer/security/requestFiltering/requestLimits/){target="_blank"}.

