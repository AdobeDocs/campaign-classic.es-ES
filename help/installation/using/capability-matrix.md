---
title: Tabla de campaña in situ, híbrida y alojada
description: Conocer las principales diferencias entre las implementaciones alojadas y las in situ
page-status-flag: never-activated
uuid: d1c786a1-2691-4966-9108-059004050464
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 582f7ac6-cebe-4b47-8730-bbc16fd6b1bd
translation-type: tm+mt
source-git-commit: c2e1b4cf7051b7f1b9d5f2db0d9f51a733ca2abc
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 21%

---


# Matriz de capacidad por modelo de alojamiento {#capability-matrix-per-model}

Adobe Campaign Classic incluye un conjunto de módulos y opciones. La disponibilidad de estos módulos y su uso pueden depender del tipo de implementación de la instalación. Este artículo comparte algunos detalles sobre las principales diferencias para determinadas funciones entre implementaciones totalmente alojadas (Managed Services) y locales.

Esta página muestra las principales diferencias entre las implementaciones alojadas (Managed Services) y las in situ. Las características específicas de las implementaciones híbridas dependen de los elementos alojados en Adobe y alojados en sus instalaciones.

Los distintos modelos de alojamiento se introducen [en esta sección](../../installation/using/hosting-models.md).

## Matriz de capacidad{#capability-matrix}

| Capacidad | Alojado | Híbrido | In situ | Detalles |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configuración del servidor de Campaña | Bajo demanda | Disponible | Disponible | Adobe sólo puede modificar el archivo[de configuración del](../../installation/using/the-server-configuration-file.md)servidor para clientes alojados. |
| Email BCC | Bajo demanda | Bajo demanda | Disponible | Para arquitecturas híbridas y alojadas, póngase en contacto con el ejecutivo de cuentas para activar el CCO de correo electrónico. Para las instalaciones in situ, siga las directrices de la documentación. [Más información](../../installation/using/email-archiving.md) |
| Administrar la instancia de ejecución del centro de mensajes | Bajo demanda | Bajo demanda | Disponible | Para implementaciones alojadas, ciertos ajustes, como la creación de usuarios en instancia de ejecución, solo se pueden realizar mediante Adobe. [Más información](../../message-center/using/about-transactional-messaging.md) |
| Administración de la plataforma Intermediaria | Bajo demanda | Bajo demanda | Disponible | Las plataformas de intermediaria alojadas en Adobe solo se pueden configurar en Adobe. |
| Procesamiento de bandeja de entrada mediante Litmus | Bajo demanda | Bajo demanda | Disponible | Necesitas una cuenta Litmus. Debe ponerse en contacto con Adobe para obtener los detalles necesarios o realizar la configuración de procesamiento de la Bandeja de entrada. [Más información](../../delivery/using/inbox-rendering.md) |
| Integración con IMS (Adobe ID) | Bajo demanda | Bajo demanda | Bajo demanda | El aprovisionamiento de IMS se realiza mediante Adobe. Esta integración es un requisito previo para las integraciones de Adobe Experience Cloud. [Más información](../../integrations/using/about-adobe-id.md) |
| Cifrado y descifrado de datos para transferencias de archivos | Bajo demanda | Disponible | Disponible | Para habilitar el procesamiento previo o posterior del archivo es necesario instalar la utilidad necesaria en el servidor de Adobe Campaign. Los clientes alojados pueden utilizar el Panel de control de Campaign de Campaña. [Más información](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Impresión/descompresión de archivos | Disponible a petición | Disponible | Para habilitar el procesamiento previo o posterior del archivo es necesario instalar la utilidad necesaria en el servidor de Adobe Campaign. Los clientes alojados pueden utilizar el Panel de control de Campaign de Campaña. [Más información](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Delegación de nombres de dominio | Bajo demanda | Bajo demanda | No disponible | [Más información](https://helpx.adobe.com/es/campaign/kb/domain-name-delegation.html) |
| Instalación de SpamAssassin | Bajo demanda | Disponible | Disponible | La instalación de SpamAssassin requiere editar el archivo de configuración del servidor. [Más información](../../delivery/using/spamassassin.md) |
| Acceso a los informes de entregabilidad | Disponible | Bajo demanda | Disponible | En determinadas implementaciones híbridas, no se puede acceder a los informes de entregabilidad desde la instancia de marketing. |
| Configuración de la autenticación LDAP | No disponible | Disponible | Disponible | La configuración LDAP sólo es posible para instalaciones in situ o híbridas. [Más información](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

Adobe Campaign proporciona la opción **Acceso de Datos Federados** (FDA) para procesar la información almacenada en una o más bases de datos externas: puede acceder a datos externos sin cambiar la estructura de los datos de Adobe Campaign. [Más información](../../platform/using/about-fda.md)

>[!CAUTION]
>
>Accessing an external database via FDA is only possible for on-premise or hybrid installations, except with the [Snowflake connector](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake).


**Consulte también**

* [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md)
* [Notas de la versión](../../rn/using/latest-release.md)
* [Actualizaciones de Campaign Classic](../../rn/using/rn-overview.md)
* [Funciones obsoletas y eliminadas](../../rn/using/deprecated-features.md)
* [Versiones de Gold Standard](../../rn/using/gold-standard.md)
* [Programa](https://helpx.adobe.com/es/campaign/kb/gold-standard.html)Gold Standard.
