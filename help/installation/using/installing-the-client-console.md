---
title: Instalación de la consola de cliente
seo-title: Instalación de la consola de cliente
description: Instalación de la consola de cliente
seo-description: null
page-status-flag: never-activated
uuid: 1279c0d8-bf27-4a58-ae94-796d6147231a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1069b23-e08d-43c5-bbfb-3158ac40dc7e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# Instalación de la consola de cliente{#installing-the-client-console}

El procedimiento de instalación de la consola de Adobe Campaign se detalla a continuación.

Antes de instalar la consola de Adobe Campaign, compruebe los requisitos previos enumerados en la matriz [](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)Compatibilidad.

Para instalar la consola de Adobe Campaign, siga los pasos siguientes:

1. Abra un explorador Web y descargue la consola desde la siguiente dirección:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://machine/nl/jsp/logon.jsp).

1. En la ventana de identificación, introduzca su nombre de inicio de sesión y contraseña.

   ![](assets/s_ncs_install_setup_download01.png)

   Si es necesario, utilice las credenciales de la cuenta interna definida durante la creación de la instancia.

1. Haga clic en el **[!UICONTROL Download]** vínculo en la página de instalación.
1. Descargue y guarde el archivo de configuración del cliente.
1. Ejecute el archivo descargado en un equipo con Windows: Se inicia la instalación. La ruta de instalación predeterminada de la consola de cliente es **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, donde &#39;X&#39; es &#39;6&#39; o &#39;7&#39;, según la versión de Adobe Campaign.
1. Una vez finalizado el programa de instalación, inicie la consola desde el menú Windows **[!UICONTROL Start]** (en el grupo de programas de **Adobe Campaign** ).

>[!NOTE]
>
>En Windows, puede iniciar el archivo **nlclient.exe** directamente desde el `[INSTALL]/bin` directorio de un servidor Windows, donde `[INSTALL]` es la ruta de acceso para la carpeta de instalación de Adobe Campaign.\
>Para crear una nueva conexión, consulte [Creación de una instancia e inicio de sesión](../../installation/using/creating-an-instance-and-logging-on.md).

