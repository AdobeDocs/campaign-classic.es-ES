---
solution: Campaign Classic
product: campaign
title: Principio de configuración
description: Principio de configuración
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 4%

---


# Principio de configuración{#configuration-principle}

La plataforma de Adobe Campaign se basa en el concepto de instancias, similar al de los hosts virtuales utilizados por Apache. Este modo de operación permite compartir un servidor asignándole varias instancias. Las instancias están completamente separadas entre sí y funcionan con su propia base de datos y archivo de configuración.

Para un servidor determinado, hay dos elementos comunes a todas las instancias de Adobe Campaign:

* La contraseña **interna**: es la contraseña general del administrador. Es común a todas las instancias de un servidor de aplicaciones en particular.

   >[!IMPORTANT]
   >
   >Para iniciar sesión con el identificador **Interno**, debe haber definido una contraseña de antemano. Para obtener más información, consulte [esta sección](../../installation/using/campaign-server-configuration.md#internal-identifier).

* Varias configuraciones técnicas de servidor: todas estas configuraciones se pueden sobrecargar en la configuración específica de una instancia.

Los archivos de configuración se guardan en el directorio **conf** del directorio de instalación. La configuración se desglosa en tres archivos:

* **serverConf.xml**: configuración general para todas las instancias.
* **config-**`<instance>`**.xml** (donde  **`<instance>`** es el nombre de instancia): configuración específica de una instancia.
* **serverConf.xml.diff**: delta entre la configuración inicial y la configuración actual. La aplicación genera automáticamente este archivo y no debe modificarse manualmente. Se utiliza para propagar automáticamente las modificaciones del usuario al actualizar una versión de compilación.

Una configuración de instancia se carga de la siguiente manera:

* El módulo carga el archivo **serverConf.xml** para obtener los parámetros compartidos por todas las instancias.
* Luego carga el archivo **config-**`<instance>`**.xml**. Los valores encontrados en este archivo tienen prioridad sobre los valores contenidos en **serverConf.xml**.

   Estos dos archivos tienen el mismo formato. Cualquier valor de **serverConf.xml** se puede sobrecargar para una instancia determinada en el archivo **config-`<instance>`.xml**.

Este modo operativo proporciona buena flexibilidad para las configuraciones.
