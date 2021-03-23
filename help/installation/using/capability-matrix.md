---
solution: Campaign Classic
product: campaign
title: Matriz de capacidades locales, híbridas y alojadas de Campaign
description: Conozca las principales diferencias entre implementaciones alojadas y locales
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
translation-type: tm+mt
source-git-commit: b77a56a97e499f60c092fae45c7809f7bfd9f2ea
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 36%

---


# Matriz de capacidades por modelo{#capability-matrix-per-model}

Adobe Campaign Classic incluye un conjunto de módulos y opciones. La disponibilidad de estos módulos y su uso pueden depender del tipo de implementación de la instalación. Este artículo comparte algunos detalles sobre las principales diferencias para ciertas funciones entre implementaciones totalmente alojadas (Managed Services) y locales.

Esta página muestra las principales diferencias entre las implementaciones alojadas (Managed Services) y locales. Las características específicas de las implementaciones híbridas dependen de los elementos alojados por Adobe y alojados en sus instalaciones.

Los diferentes modelos de alojamiento se presentan [en esta sección](../../installation/using/hosting-models.md).

## Disponibilidad por modelo de implementación {#capability-matrix}

| Capacidad | Alojado | Híbrido | On-Premise | Detalles |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configuración del servidor de Campaign | Bajo demanda | Disponible | Disponible | [Obtenga más información](../../installation/using/the-server-configuration-file.md) |
| Correo electrónico CCO | Bajo demanda | Bajo demanda | Disponible | [Obtenga más información](../../installation/using/email-archiving.md) |
| Administrar instancia de ejecución del centro de mensajes | Bajo demanda | Bajo demanda | Disponible | [Obtenga más información](../../message-center/using/about-transactional-messaging.md) |
| Administración de la plataforma intermediaria | Bajo demanda | Bajo demanda | Disponible | [Obtenga más información](../../installation/using/mid-sourcing-server.md) |
| Renderización de la bandeja de entrada mediante Litmus | Bajo demanda | Bajo demanda | Disponible | [Obtenga más información](../../delivery/using/inbox-rendering.md) |
| Integración con IMS (Adobe ID) | Bajo demanda | Bajo demanda | Bajo demanda | [Obtenga más información](../../integrations/using/about-adobe-id.md) |
| Cifrar/descifrar datos para transferencias de archivos | Bajo demanda | Disponible | Disponible | [Obtenga más información](../../platform/using/unzip-decrypt.md) |
| Comprimir/descomprimir archivos | Bajo demanda | Disponible | Disponible | [Obtenga más información](../../platform/using/unzip-decrypt.md) |
| Delegación de nombres de dominio | Bajo demanda | Bajo demanda | No disponible | [Obtenga más información](https://helpx.adobe.com/es/campaign/kb/domain-name-delegation.html) |
| Instalación de SpamAssassin | Bajo demanda | Disponible | Disponible | [Obtenga más información](../../delivery/using/spamassassin.md) |
| Acceso a los informes de capacidad de envío | Disponible | Bajo demanda | Disponible | [Obtenga más información](../../delivery/using/monitoring-deliverability.md) |
| Configuración de la autenticación LDAP | No disponible | Disponible | Disponible | [Obtenga más información](../../installation/using/connecting-through-ldap.md) |


## Acceso de datos federado{#fda}

Adobe Campaign proporciona la opción **Acceso de Datos Federados** (FDA) para procesar la información almacenada en una o más bases de datos externas: puede acceder a datos externos sin cambiar la estructura de los datos de Adobe Campaign. [Obtenga más información](../../installation/using/about-fda.md)

>[!CAUTION]
>
>El acceso a una base de datos externa a través de FDA solo es posible para instalaciones locales o híbridas, excepto con el [conector del Snowflake](../../installation/using/configure-fda-snowflake.md).


**Consulte también**

* [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md)
* [Notas de la versión](../../rn/using/latest-release.md)
* [actualizaciones de Campaign Classic](../../rn/using/rn-overview.md)
* [Funciones obsoletas y eliminadas](../../rn/using/deprecated-features.md)
* [[!DNL Gold Standard] versiones](../../rn/using/gold-standard.md)
* [[!DNL Gold Standard] programa](../../rn/using/gs-overview.md)
