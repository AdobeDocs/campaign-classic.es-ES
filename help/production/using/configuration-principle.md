---
solution: Campaign Classic
product: campaign
title: Principio de configuración
description: Principio de configuración
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 4%

---

# Principio de configuración{#configuration-principle}

La plataforma de Adobe Campaign se basa en el concepto de instancias, similar al de los hosts virtuales utilizados por Apache. Este modo de operación permite compartir un servidor asignándole varias instancias. Las instancias están completamente separadas entre sí y funcionan con su propia base de datos y archivo de configuración.

Para un servidor determinado, hay dos elementos que son comunes a todas las instancias de Adobe Campaign:

* La contraseña **internal**: es la contraseña general del administrador. Es común a todas las instancias de un servidor de aplicaciones en particular.

   >[!IMPORTANT]
   >
   >Para iniciar sesión con el identificador **Internal**, debe haber definido previamente una contraseña. Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#internal-identifier).

* Varias configuraciones técnicas del servidor: estas configuraciones se pueden sobrecargar en la configuración específica de una instancia.

Los archivos de configuración se guardan en el directorio **conf** del directorio de instalación. La configuración se divide en tres archivos:

* **serverConf.xml**: configuración general para todas las instancias.
* **config-**`<instance>`**.xml**  (donde  **`<instance>`** es el nombre de instancia): configuración específica de una instancia.
* **serverConf.xml.diff**: delta entre la configuración inicial y la configuración actual. La aplicación genera automáticamente este archivo y no debe modificarse manualmente. Se utiliza para propagar automáticamente las modificaciones del usuario al actualizar una versión de compilación.

Una configuración de instancia se carga de la siguiente manera:

* El módulo carga el archivo **serverConf.xml** para obtener los parámetros compartidos por todas las instancias.
* A continuación, carga el archivo **config-**`<instance>`**.xml**. Los valores encontrados en este archivo tienen prioridad sobre los valores contenidos en **serverConf.xml**.

   Estos dos archivos tienen el mismo formato. Cualquier valor de **serverConf.xml** puede sobrecargarse para una instancia determinada en el archivo **config-`<instance>`.xml**.

Este modo operativo proporciona buena flexibilidad para las configuraciones.
