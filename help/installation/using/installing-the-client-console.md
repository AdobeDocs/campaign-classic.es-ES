---
solution: Campaign Classic
product: campaign
title: Instalación de la consola del cliente
description: Obtenga información sobre cómo instalar la consola de cliente
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: cea4a26935312b1cb119a3fa671af7bf00788fe9
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 15%

---


# Instalando la consola cliente de Campaña{#installing-the-client-console}

La consola del cliente de Campaign es un cliente enriquecido que le permite conectarse a sus servidores de aplicaciones de Campaign. 

Antes de comenzar, debe comprobar la Campaña [Tabla de compatibilidad](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html), obtener la dirección URL del servidor de Campaña y las credenciales de usuario.

>[!CAUTION]
>
>La consola del cliente de campaña y el servidor de aplicaciones de Campaña deben ejecutarse en la misma versión del producto. Adobe también recomienda utilizar la misma compilación de productos.

![](assets/do-not-localize/how-to-video.png) Descubra cómo instalar y configurar el cliente de Adobe Campaign en  [vídeo](#video)

## Descargar la consola{#download-the-client-console}

Para descargar e instalar la consola de cliente de Adobe Campaign, siga los pasos a continuación:

1. Abra un navegador web y descargue la consola de la siguiente dirección:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. En la ventana de identificación, introduzca su nombre de inicio de sesión y contraseña.

   ![](assets/s_ncs_install_setup_download01.png)

   Si es necesario, utilice las credenciales de la cuenta interna definida durante la creación de la instancia.

1. Haga clic en el vínculo **[!UICONTROL Download]** en la página de instalación.
1. Descargue y guarde el archivo de configuración del cliente.
1. Ejecute el archivo descargado en un equipo con Windows: La instalación se inicio. La ruta de instalación predeterminada de la consola de cliente es **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, donde &#39;X&#39; es &#39;6&#39; o &#39;7&#39;, según la versión de Adobe Campaign.

>[!NOTE]
>
>En Windows, puede iniciar el archivo **nlclient.exe** directamente desde el directorio `[INSTALL]/bin` en un servidor Windows, donde `[INSTALL]` es la ruta de acceso para la carpeta de instalación de Adobe Campaign.

## Crear la conexión{#create-the-connection}

Una vez instalada la consola de cliente, siga los pasos a continuación para crear la conexión con el servidor de aplicaciones:

1. Inicio la consola desde el menú **[!UICONTROL Start]** de Windows, en el grupo de programas **Adobe Campaign**.

1. Haga clic en el vínculo en la esquina superior derecha de los campos de credenciales para acceder a la ventana de configuración de conexión.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Haga clic en **[!UICONTROL Add > Connection]** e introduzca la etiqueta y la dirección URL del servidor de aplicaciones de Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Especifique una conexión con el servidor de aplicaciones de Adobe Campaign mediante una URL. Use un DNS o un alias del equipo o su dirección IP.

   Por ejemplo, puede utilizar la dirección URL de tipo [`https://<machine>.<domain>.com`](https://myserver.adobe.com).

1. Si Adobe IMS está configurado para su organización, marque la opción **[!UICONTROL Connect with an Adobe ID]**

1. Haga clic en **[!UICONTROL Ok]** para guardar la configuración.

Puede agregar tantas conexiones como sea necesario para conectarse a los entornos de prueba, etapa y producción, por ejemplo.

>[!NOTE]
>
>El botón **[!UICONTROL Add]** permite crear **[!UICONTROL folders]** para organizar todas las conexiones. Basta con arrastrar y colocar cada conexión en una carpeta.

## Iniciar sesión en Adobe Campaign

Para iniciar sesión en una instancia existente, siga los pasos a continuación:

1. Inicio la consola desde el menú **[!UICONTROL Start]** de Windows, en el grupo de programas **Adobe Campaign**.

1. Haga clic en el vínculo en la esquina superior derecha de los campos de credenciales para acceder a la ventana de configuración de conexión.

1. Seleccione la instancia de Campaña en la que debe iniciar sesión.

1. Haga clic en **[!UICONTROL Ok]**

1. Introduzca sus credenciales de inicio de sesión de usuario y haga clic en **[!UICONTROL Log in]**

**Temas relacionados**

* [Creación de una instancia e inicio de sesión](../../installation/using/creating-an-instance-and-logging-on.md).
* [Matriz de compatibilidad](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

## Vídeo tutorial

Este vídeo muestra cómo instalar y configurar el cliente de Adobe Campaign.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

Puede encontrar disponibles más vídeos de procedimientos para Campaign Classic [aquí](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=es).
