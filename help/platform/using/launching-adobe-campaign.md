---
solution: Campaign Classic
product: campaign
title: Ejecutar Adobe Campaign
description: Ejecutar Adobe Campaign
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 86%

---


# Ejecutar Adobe Campaign{#launching-adobe-campaign}

La consola del cliente de Campaign es un cliente enriquecido que le permite conectarse a sus servidores de aplicaciones de Campaign. Obtenga información sobre cómo descargar y configurar la consola del cliente en [esta página](../../installation/using/installing-the-client-console.md).

## Iniciar Adobe Campaign {#starting-adobe-campaign}

Puede iniciar Adobes Campaign seleccionando **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

La ventana de conexión de la consola del cliente le permite seleccionar o configurar bases de datos existentes y conectarse con un nombre de usuario y una contraseña:

![](assets/acc-logon.png)

## Conexión a Adobe Campaign {#connecting-to-adobe-campaign}

Puede conectarse a Adobe Campaign con su Adobe ID. Para obtener más información, consulte [esta página](../../integrations/using/about-adobe-id.md).

También puede conectarse con un nombre de usuario y contraseña específicos:

1. Introduzca el identificador de la cuenta del operador en el campo de **[!UICONTROL login]**.

   El administrador de la plataforma Adobe Campaign proporciona su identificador.

1. Introduzca su contraseña en el campo **[!UICONTROL Password]**.

   La primera vez que acceda a la base de datos, la contraseña es la que le proporciona el administrador. Una vez que esté conectado, puede cambiar la contraseña mediante el menú **[!UICONTROL Tools > Change password...]**. Los detalles sobre operadores y conexiones están disponibles en [Administración de acceso](../../platform/using/access-management.md).

1. Haga clic en **[!UICONTROL LOG IN]** para confirmar.

Ahora puede acceder al [espacio de trabajo de Adobe Campaign](../../platform/using/adobe-campaign-workspace.md).

## Configuración de las conexiones {#setting-up-connections}

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

## Desconexión de Adobe Campaign {#disconnecting-from-adobe-campaign}

Para desconectarse de Adobe Campaign, utilice el primer icono de la barra de iconos.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>También puede cerrar la aplicación sin cerrar sesión primero.

## Obtención de la versión de Adobe Campaign {#getting-your-campaign-version}

El menú **[!UICONTROL Help > About...]** le permite obtener acceso a la siguiente información:

* **número de** versión para consola cliente de Campaña y servidor de aplicaciones
* **** buildnumber para consola cliente de Campaña y servidor de aplicaciones
* un vínculo para ponerse en contacto con el Servicio de atención al cliente de Adobe
* vínculos a la Política de privacidad de Adobe, a las Condiciones de uso y a la Política de cookies

![](assets/about-acc.png)

Siempre que se ponga en contacto con el equipo de atención al cliente de Adobe, debe proporcionar el número de versión y de compilación de la consola de cliente y el servidor de aplicaciones de Adobe Campaign.

Si está ejecutando la versión de [Campaign Gold Standard](../../rn/using/gold-standard.md) también debe compartir los caracteres SHA/1 que se muestran en la casilla **[!UICONTROL About]**. Como ejemplo, para la versión Gold **Standard 10**, el número de compilación mostrará la **compilación 9032@efd8a94**, como se muestra a continuación:

![](assets/about-acc-gs.png)

Consulte [este artículo](https://helpx.adobe.com/es/campaign/kb/gold-standard.html) para obtener más información sobre Gold Standard.

**Temas relacionados**:

* [Opciones de ayuda y asistencia técnica de Adobe Campaign](https://helpx.adobe.com/es/campaign/kb/ac-support.html#acc-support)
* [Distribución de software de Adobe](https://docs.adobe.com/content/help/es-ES/experience-cloud/software-distribution/home.html)
* [Sesiones de expertos y asistencia técnica de Adobe Experience Cloud](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
