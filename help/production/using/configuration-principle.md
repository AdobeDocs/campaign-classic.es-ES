---
product: campaign
title: Principio de configuración
description: Principio de configuración
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 4%

---

# Principio de configuración{#configuration-principle}



La plataforma de Adobe Campaign se basa en el concepto de instancias, similar al de los hosts virtuales utilizados por Apache. Este modo de operación permite compartir un servidor asignándole varias instancias. Las instancias están completamente separadas entre sí y funcionan con su propia base de datos y archivo de configuración.

Para un servidor determinado, hay dos elementos que son comunes a todas las instancias de Adobe Campaign:

* La variable **internal** contraseña: es la contraseña general del administrador. Es común a todas las instancias de un servidor de aplicaciones en particular.

   >[!IMPORTANT]
   >
   >Para iniciar sesión con el **Internas** , debe haber definido previamente una contraseña. Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#internal-identifier).

* Varias configuraciones técnicas del servidor: estas configuraciones se pueden sobrecargar en la configuración específica de una instancia.

Los archivos de configuración se guardan en la variable **conf** del directorio de instalación. La configuración se divide en tres archivos:

* **serverConf.xml**: configuración general para todas las instancias.
* **config-**`<instance>`**.xml** (donde **`<instance>`** es el nombre de instancia): configuración específica de una instancia.
* **serverConf.xml.diff**: delta entre la configuración inicial y la configuración actual. La aplicación genera automáticamente este archivo y no debe modificarse manualmente. Se utiliza para propagar automáticamente las modificaciones del usuario al actualizar una versión de compilación.

Una configuración de instancia se carga de la siguiente manera:

* El módulo carga la variable **serverConf.xml** para obtener los parámetros compartidos por todas las instancias.
* Luego carga el **config-**`<instance>`**.xml** archivo. Los valores encontrados en este archivo tienen prioridad sobre los valores contenidos en **serverConf.xml**.

   Estos dos archivos tienen el mismo formato. Cualquier valor de **serverConf.xml** se puede sobrecargar para una instancia determinada en el **config-`<instance>`.xml** archivo.

Este modo operativo proporciona buena flexibilidad para las configuraciones.
