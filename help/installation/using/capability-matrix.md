---
solution: Campaign Classic
product: campaign
title: Tabla de campaña in situ, híbrida y alojada
description: Conocer las principales diferencias entre las implementaciones alojadas y las in situ
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 37%

---


# Matriz de capacidades {#capability-matrix-per-model}

Adobe Campaign Classic incluye un conjunto de módulos y opciones. La disponibilidad de estos módulos y su uso pueden depender del tipo de implementación de la instalación. Este artículo comparte algunos detalles sobre las principales diferencias para determinadas funciones entre implementaciones totalmente alojadas (Managed Services) y locales.

Esta página muestra las principales diferencias entre las implementaciones alojadas (Managed Services) y las in situ. Las características específicas de las implementaciones híbridas dependen de los elementos alojados en Adobe y alojados en sus instalaciones.

Los diferentes modelos de alojamiento se introducen [en esta sección](../../installation/using/hosting-models.md).

## Disponibilidad por modelo de implementación {#capability-matrix}

| Capacidad | Alojado | Híbrido | In situ | Detalles |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configuración del servidor de Campaña | Bajo demanda | Disponible | Disponible | [Más información](../../installation/using/the-server-configuration-file.md) |
| Correo electrónico CCO | Bajo demanda | Bajo demanda | Disponible | [Más información](../../installation/using/email-archiving.md) |
| Administrar la instancia de ejecución del centro de mensajes | Bajo demanda | Bajo demanda | Disponible | [Más información](../../message-center/using/about-transactional-messaging.md) |
| Administración de la plataforma Intermediaria | Bajo demanda | Bajo demanda | Disponible | [Más información](../../installation/using/mid-sourcing-server.md) |
| Procesamiento de bandeja de entrada mediante Litmus | Bajo demanda | Bajo demanda | Disponible | [Más información](../../delivery/using/inbox-rendering.md) |
| Integración con IMS (Adobe ID) | Bajo demanda | Bajo demanda | Bajo demanda | [Más información](../../integrations/using/about-adobe-id.md) |
| Cifrado y descifrado de datos para transferencias de archivos | Bajo demanda | Disponible | Disponible | [Más información](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Impresión/descompresión de archivos | Bajo demanda | Disponible | Disponible | [Más información](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Delegación de nombres de dominio | Bajo demanda | Bajo demanda | No disponible | [Más información](https://helpx.adobe.com/es/campaign/kb/domain-name-delegation.html) |
| Instalación de SpamAssassin | Bajo demanda | Disponible | Disponible | [Más información](../../delivery/using/spamassassin.md) |
| Acceso a los informes de entregabilidad | Disponible | Bajo demanda | Disponible | [Más información](../../delivery/using/monitoring-deliverability.md) |
| Configuración de la autenticación LDAP | No disponible | Disponible | Disponible | [Más información](../../installation/using/connecting-through-ldap.md) |


## acceso de datos federado{#fda}

Adobe Campaign proporciona la opción **Acceso de Datos Federados** (FDA) para procesar la información almacenada en una o más bases de datos externas: puede acceder a datos externos sin cambiar la estructura de los datos de Adobe Campaign. [Más información](../../installation/using/about-fda.md)

>[!CAUTION]
>
>El acceso a una base de datos externa mediante FDA sólo es posible para instalaciones in situ o híbridas, excepto con el [conector del Snowflake](../../installation/using/configure-fda-snowflake.md).


**Consulte también**

* [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md)
* [Notas de la versión](../../rn/using/latest-release.md)
* [Actualizaciones de Campaign Classic](../../rn/using/rn-overview.md)
* [Funciones obsoletas y eliminadas](../../rn/using/deprecated-features.md)
* [Versiones de Gold Standard](../../rn/using/gold-standard.md)
* [Programa estándar Gold](https://helpx.adobe.com/es/campaign/kb/gold-standard.html)
