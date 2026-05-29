---
product: campaign
title: Ejecutar Adobe Campaign
description: Ejecutar Adobe Campaign
feature: Access Management, Permissions
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
TQID: https://experienceleague.adobe.com/qpZM0jaN1ht6QfReQBy1c7jONGdc2PQ0ORepDaVficQ
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
  - id: efa38731-2723-4334-8d8b-a778af834835
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 451
ht-degree: 100%

---

# Lanzamiento de Adobe Campaign {#launching-adobe-campaign}

La consola del cliente de Campaign es un cliente enriquecido que le permite conectarse a sus servidores de aplicaciones de Campaign. Obtenga información sobre cómo descargar y configurar la consola del cliente en [esta página](../../installation/using/installing-the-client-console.md).

>[!CAUTION]
>
>Compruebe la compatibilidad del sistema y las herramientas con la consola del cliente de Adobe Campaign en la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

## Inicio de Adobe Campaign {#starting-adobe-campaign}

Puede iniciar Adobes Campaign seleccionando **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

La ventana de conexión de la consola del cliente le permite seleccionar o configurar bases de datos existentes y conectarse con un nombre de usuario y una contraseña:

![](assets/acc-logon.png)

## Conexión a Adobe Campaign {#connecting-to-adobe-campaign}

### Conexión mediante el Adobe ID

Los usuarios de Campaign se conectan a la consola de Adobe Campaign mediante su Adobe ID a través del sistema de administración de identidades (IMS) de Adobe. Pueden utilizar el mismo ID en todas las soluciones de Adobe. Cada conexión se guarda cuando se utiliza Adobe Campaign con otras soluciones. Obtenga más información sobre Adobe IMS en [esta página](https://helpx.adobe.com/es/enterprise/using/identity.html).

Para configurar la conexión de Campaign Classic v7 con el servicio de administración de identidades (IMS) de Adobe, consulte [esta página](../../integrations/using/about-adobe-id.md).

Una vez completada la configuración, aprenda a conectarse a Campaign con su Adobe ID en la [documentación de Campaign v8 (consola)](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/new/connect){target=_blank}.


### Conexión con un inicio de sesión o una contraseña

También puede conectarse con un nombre de usuario y contraseña específicos. Esta conexión se conoce como &#39;Autenticación nativa&#39; de Campaign:

1. Introduzca el identificador de la cuenta del operador en el campo de **[!UICONTROL Login]**.

   El administrador de la plataforma Adobe Campaign proporciona su identificador.

1. Introduzca su contraseña en el campo **[!UICONTROL Password]**.

   La primera vez que acceda a la base de datos, la contraseña es la que le proporciona el administrador. Una vez que esté conectado, puede cambiar la contraseña mediante el menú **[!UICONTROL Tools > Change password...]**. Los detalles sobre operadores y conexiones están disponibles en [Administración de acceso](../../platform/using/access-management.md).

1. Haga clic en **[!UICONTROL LOG IN]** para confirmar.

Ahora puede acceder al [espacio de trabajo de Adobe Campaign](../../platform/using/adobe-campaign-workspace.md).

## Configuración de conexiones {#setting-up-connections}

Puede acceder a la configuración de conexión del servidor a través del vínculo situado encima del área de entrada.

![](assets/s_ncs_user_connections_management.png)

Aprenda a configurar conexiones en la [documentación de Campaign v8 (consola)](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/new/connect#create-your-connection){target=_blank}.

## Operadores y permisos {#operators-and-permissions}

Los identificadores y contraseñas de operadores con acceso al software y sus respectivos permisos se definen mediante el administrador del sistema de Adobe Campaign en el nodo **[!UICONTROL Administration > Access management > Operators]**.

Esta funcionalidad se detalla en la sección [Administración de acceso](../../platform/using/access-management.md).

## Obtención de la versión de Adobe Campaign {#getting-your-campaign-version}

El menú **[!UICONTROL Help > About...]** le permite acceder a la siguiente información:

* **número de versión** de la consola de cliente de Campaign y del servidor de aplicaciones
* número de **compilación** para la consola de cliente y el servidor de aplicaciones de Campaign
* un vínculo para ponerse en contacto con el Servicio de atención al cliente de Adobe
* vínculos a la Política de privacidad de Adobe, a las Condiciones de uso y a la Política de cookies

![](assets/about-acc.png)

Cuando contacte con el equipo de atención al cliente de Adobe, debe proporcionar el número de versión y el número de compilación de la consola del cliente de Adobe Campaign y del servidor de aplicaciones.

