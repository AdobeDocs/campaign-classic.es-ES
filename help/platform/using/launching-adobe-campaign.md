---
solution: Campaign Classic
product: campaign
title: Ejecutar Adobe Campaign
description: Ejecutar Adobe Campaign
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
translation-type: tm+mt
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 95%

---

# Inicio de Adobe Campaign{#launching-adobe-campaign}

La consola del cliente de Campaign es un cliente enriquecido que le permite conectarse a sus servidores de aplicaciones de Campaign. Obtenga información sobre cómo descargar y configurar la consola del cliente en [esta página](../../installation/using/installing-the-client-console.md).

## Iniciar Adobe Campaign {#starting-adobe-campaign}

Puede iniciar Adobes Campaign seleccionando **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

La ventana de conexión de la consola del cliente le permite seleccionar o configurar bases de datos existentes y conectarse con un nombre de usuario y una contraseña:

![](assets/acc-logon.png)

## Conectarse a Adobe Campaign {#connecting-to-adobe-campaign}

Puede conectarse a Adobe Campaign con su Adobe ID. Para obtener más información, consulte [esta página](../../integrations/using/about-adobe-id.md).

También puede conectarse con un nombre de usuario y contraseña específicos:

1. Introduzca el identificador de la cuenta del operador en el campo de **[!UICONTROL Login]**.

   El administrador de la plataforma Adobe Campaign proporciona su identificador.

1. Introduzca su contraseña en el campo **[!UICONTROL Password]**.

   La primera vez que acceda a la base de datos, la contraseña es la que le proporciona el administrador. Una vez que esté conectado, puede cambiar la contraseña mediante el menú **[!UICONTROL Tools > Change password...]**. Los detalles sobre operadores y conexiones están disponibles en [Administración de acceso](../../platform/using/access-management.md).

1. Haga clic en **[!UICONTROL LOG IN]** para confirmar.<!--You can also press the **Enter** key to launch connection.-->

Ahora puede acceder al [espacio de trabajo de Adobe Campaign](../../platform/using/adobe-campaign-workspace.md).

Algunos métodos abreviados de teclado están disponibles en **[!UICONTROL Sign in screen]**:
* Todos los elementos procesables se pueden seleccionar mediante las teclas **Tab** (de arriba abajo) o **Tab** + **Mayús** (de abajo arriba).
* Para iniciar la conexión, también puede presionar la tecla **Intro**.
* Puede utilizar la tecla **Escape** para restablecer los campos **[!UICONTROL Login]** y **[!UICONTROL Password]** a los últimos valores de conexión correctos.

## Configuración de conexiones {#setting-up-connections}

Puede acceder a la configuración de conexión del servidor a través del vínculo situado encima del área de entrada.

![](assets/s_ncs_user_connections_management.png)

En la ventana **[!UICONTROL Connections]**, haga clic en **[!UICONTROL Add > Connection]**.

A continuación, debe definir la configuración de conexión. Para ello:

1. Introduzca una **[!UICONTROL Label]** para asignar un nombre a la conexión de base de datos.

1. Añada la dirección del servidor de aplicaciones en el campo **[!UICONTROL URL]**. Si no conoce la dirección URL de conexión, póngase en contacto con el administrador.

1. Consulte **[!UICONTROL Connect with an Adobe ID]** para que los operadores se conecten a la consola con su Adobe ID. Para obtener más información, consulte [esta página](../../integrations/using/about-adobe-id.md).

1. Haga clic en **[!UICONTROL OK]** para validar.

## Operadores y permisos {#operators-and-permissions}

Los identificadores y contraseñas de operadores con acceso al software y sus respectivos permisos se definen mediante el administrador del sistema de Adobe Campaign en el nodo **[!UICONTROL Administration > Access management > Operators]**.

Esta funcionalidad se detalla en la sección [Administración de acceso](../../platform/using/access-management.md).

## Desconectar de Adobe Campaign {#disconnecting-from-adobe-campaign}

Para desconectarse de Adobe Campaign, utilice el primer icono de la barra de iconos.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>También puede cerrar la aplicación sin cerrar sesión primero.

## Obtenga su versión de Adobe Campaign {#getting-your-campaign-version}

El menú **[!UICONTROL Help > About...]** le permite acceder a la siguiente información:

* **número de versión** de la consola de cliente de Campaign y del servidor de aplicaciones
* número de **compilación** para la consola de cliente y el servidor de aplicaciones de Campaign
* un vínculo para ponerse en contacto con el Servicio de atención al cliente de Adobe
* vínculos a la Política de privacidad de Adobe, a las Condiciones de uso y a la Política de cookies

![](assets/about-acc.png)

Cuando contacte con el equipo de atención al cliente de Adobe, debe proporcionar el número de versión y el número de compilación de la consola del cliente de Adobe Campaign y del servidor de aplicaciones.

Si está ejecutando la versión de [ [!DNL Gold Standard] Campaign ](../../rn/using/gold-standard.md) también debe compartir los caracteres SHA/1 que se muestran en la casilla **[!UICONTROL About]**. Como ejemplo, para la versión Gold **Standard 10**, el número de compilación mostrará la **compilación 9032@efd8a94**, como se muestra a continuación:

![](assets/about-acc-gs.png)

Obtenga más información sobre [!DNL Gold Standard] [en este artículo](../../rn/using/gs-overview.md)).

**Temas relacionados**:

* [Consulte las opciones de ayuda y asistencia técnica de Adobe Campaign](../../support.md)
* [Distribución de software de Adobe Campaign](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html)
* [Sesiones de expertos y de asistencia de Adobe Experience Cloud](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
