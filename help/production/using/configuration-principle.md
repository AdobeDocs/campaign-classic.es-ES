---
product: campaign
title: Principio de configuración
description: Principio de configuración
feature: Monitoring, Configuration
badge-v7-prem: label="Solo local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 7%

---

# Principio de configuración{#configuration-principle}



La plataforma Adobe Campaign se basa en el concepto de instancias, similar al de los hosts virtuales utilizados por Apache. Este modo de operación le permite compartir un servidor asignándole varias instancias. Las instancias son completamente independientes entre sí y funcionan con su propia base de datos y archivo de configuración.

Para un servidor determinado, hay dos elementos que son comunes a todas las instancias de Adobe Campaign:

* El **interno** contraseña: es la contraseña de administrador general. Es común a todas las instancias de un servidor de aplicaciones en particular.

  >[!IMPORTANT]
  >
  >Para iniciar sesión con **Interno** identificador, debe haber definido una contraseña previamente. Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#internal-identifier).

* Varias configuraciones técnicas del servidor: todas estas configuraciones se pueden sobrecargar en la configuración específica de una instancia.

Los archivos de configuración se guardan en **conf** del directorio de instalación. La configuración se divide en tres archivos:

* **serverConf.xml**: configuración general para todas las instancias.
* **config-**`<instance>`**.xml** (donde **`<instance>`** es el nombre de la instancia): configuración específica de una instancia.
* **serverConf.xml.diff**: diferencia entre la configuración inicial y la configuración actual. La aplicación genera automáticamente este archivo y no se debe modificar manualmente. Se utiliza para propagar automáticamente las modificaciones del usuario al actualizar una versión de compilación.

Una configuración de instancia se carga de la siguiente manera:

* El módulo carga la variable **serverConf.xml** para obtener los parámetros compartidos por todas las instancias.
* A continuación, carga la variable **config-**`<instance>`**.xml** archivo. Los valores encontrados en este archivo tienen prioridad sobre los valores contenidos en **serverConf.xml**.

  Estos dos archivos tienen el mismo formato. Cualquier valor de **serverConf.xml** se puede sobrecargar para una instancia determinada en el **config-`<instance>`.xml** archivo.

Este modo de funcionamiento proporciona una gran flexibilidad para las configuraciones.
