---
title: Ejecutar Adobe Campaign
seo-title: Ejecutar Adobe Campaign
description: Ejecutar Adobe Campaign
seo-description: null
page-status-flag: never-activated
uuid: c1c5bb0d-ae8e-4b0e-ab39-8b2291162557
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 6652b081-66b6-47a8-97e5-383e3251647e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 51e4d72abf3a1f48700ca38566dbf06dd24594b8

---


# Ejecutar Adobe Campaign{#launching-adobe-campaign}

## Iniciar Adobe Campaign {#starting-adobe-campaign}

Para iniciar Adobe Campaign, seleccione **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

La ventana de conexión de la consola del cliente le permite seleccionar o configurar bases de datos existentes y conectarse con un nombre de usuario y una contraseña:

![](assets/s_ncs_user_login.png)

## Conexión a Adobe Campaign {#connecting-to-adobe-campaign}

Puede conectarse a Adobe Campaign con su Adobe ID. Para obtener más información, consulte [esta página](../../integrations/using/about-adobe-id.md).

También puede conectarse con un nombre de usuario y contraseña específicos:

1. Introduzca el identificador de la cuenta del operador en el campo de **[!UICONTROL login]**.

   El administrador de la plataforma Adobe Campaign proporciona su identificador.

1. Introduzca su contraseña en el campo **[!UICONTROL Password]**.

   La primera vez que acceda a la base de datos, la contraseña es la que le proporciona el administrador. Once you are connected, you can change your password via the **[!UICONTROL Tools > Change password...]** menu. Details on operators and connections are available in [Access management](../../platform/using/access-management.md).

1. Click **[!UICONTROL Log in]** to confirm.

Ahora puede acceder al [espacio de trabajo de Adobe Campaign](../../platform/using/adobe-campaign-workspace.md).

## Configuración de las conexiones {#setting-up-connections}

Puede acceder a la configuración de conexión del servidor a través del vínculo situado encima del área de entrada.

![](assets/s_ncs_user_connections_management.png)

En la **[!UICONTROL Connections]** ventana, haga clic en **[!UICONTROL Add > Connection]**.

![](assets/s_ncs_user_add_connexion.png)

A continuación, debe definir la configuración de conexión. Para ello:

* Introduzca una **[!UICONTROL Label]** para asignar un nombre a la conexión de base de datos.
* Añada la dirección del servidor de aplicaciones en el campo **[!UICONTROL URL]** . Si no conoce la dirección URL de conexión, póngase en contacto con el administrador.
* Check **[!UICONTROL Connect with an Adobe ID]** for the operators to connect to the console using their Adobe ID. Para obtener más información, consulte [esta página](../../integrations/using/about-adobe-id.md).
* Click **[!UICONTROL OK]** to validate.

>[!NOTE]
>
>El botón **[!UICONTROL Add]** permite crear **[!UICONTROL folders]** para organizar todas las conexiones. Basta con arrastrar y colocar cada conexión en una carpeta.

## Operadores y permisos {#operators-and-permissions}

Los identificadores y contraseñas de operadores con acceso al software y sus respectivos permisos se definen mediante el administrador del sistema de Adobe Campaign en el nodo **[!UICONTROL Administration > Access management > Operators]**.

This functionality is detailed in the [Access management](../../platform/using/access-management.md) section.

## Desconexión de Adobe Campaign {#disconnecting-from-adobe-campaign}

Para desconectarse de Adobe Campaign, utilice el primer icono de la barra de iconos.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>También puede cerrar la aplicación sin cerrar sesión primero.

## Su versión de Adobe Campaign {#getting-your-campaign-version}

The **[!UICONTROL Help > About...]** menu lets you access the following information:

* número de **versión**,
* número de **registro**,
* un vínculo para ponerse en contacto con el servicio de asistencia de Adobe Campaign.

   >[!CAUTION]
   >
   >Cuando contacte con el equipo de asistencia de Adobe, debe proporcionar el número de versión y el número de registro de la consola del cliente de Campaign y del servidor de aplicaciones.

