---
product: campaign
title: Matriz de capacidades locales, híbridas y alojadas de Campaign
description: Conozca las principales diferencias entre implementaciones alojadas y locales
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
exl-id: a2c425a8-9bde-4259-9140-5ada5397ed5f
source-git-commit: 1f8a51fc7760e8dcdf369cb759de724b0e7bea0c
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 39%

---

# Matriz de capacidades por modelo{#capability-matrix-per-model}

![](../../assets/v7-only.svg)

Adobe Campaign Classic incluye un conjunto de módulos y opciones. La disponibilidad de estos módulos y su uso pueden depender del tipo de implementación de la instalación. Este artículo comparte algunos detalles sobre las principales diferencias para ciertas funciones entre implementaciones totalmente alojadas (Managed Services) y locales.

Esta página muestra las principales diferencias entre las implementaciones alojadas (Managed Services) y locales. Las características específicas de las implementaciones híbridas dependen de los elementos alojados por Adobe y alojados en sus instalaciones.

Se introducen los distintos modelos de alojamiento [en esta sección](../../installation/using/hosting-models.md).

## Disponibilidad por modelo de implementación {#capability-matrix}

| Capacidad | Alojado | Híbrido | On-Premise | Detalles |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configuración del servidor de Campaign | Bajo demanda | Disponible | Disponible | [Más información](../../installation/using/the-server-configuration-file.md) |
| CCO del correo electrónico | Bajo demanda | Bajo demanda | Disponible | [Más información](../../installation/using/email-archiving.md) |
| Administrar instancia de ejecución del centro de mensajes | Bajo demanda | Bajo demanda | Disponible | [Más información](../../message-center/using/about-transactional-messaging.md) |
| Administración de la plataforma intermediaria | Bajo demanda | Bajo demanda | Disponible | [Más información](../../installation/using/mid-sourcing-server.md) |
| Renderización de la bandeja de entrada mediante Litmus | Bajo demanda | Bajo demanda | Disponible | [Más información](../../delivery/using/inbox-rendering.md) |
| Integración con IMS (Adobe ID) | Bajo demanda | Bajo demanda | Bajo demanda | [Más información](../../integrations/using/about-adobe-id.md) |
| Cifrar/descifrar datos para transferencias de archivos | Bajo demanda | Disponible | Disponible | [Más información](../../platform/using/unzip-decrypt.md) |
| Comprimir/descomprimir archivos | Bajo demanda | Disponible | Disponible | [Más información](../../platform/using/unzip-decrypt.md) |
| Delegación de nombres de dominio | Bajo demanda | Bajo demanda | No disponible | [Más información](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=es) |
| Instalación de SpamAssassin | Bajo demanda | Disponible | Disponible | [Más información](../../delivery/using/spamassassin.md) |
| Acceso a los informes de capacidad de envío | Disponible | Bajo demanda | Disponible | [Más información](../../delivery/using/monitoring-deliverability.md) |
| Configuración de la autenticación LDAP | No disponible | Disponible | Disponible | [Más información](../../installation/using/connecting-through-ldap.md) |


## Acceso de datos federado{#fda}

Adobe Campaign proporciona la opción **Acceso de Datos Federados** (FDA) para procesar la información almacenada en una o más bases de datos externas: puede acceder a datos externos sin cambiar la estructura de los datos de Adobe Campaign. [Más información](../../installation/using/about-fda.md)

>[!CAUTION]
>
>Los sistemas de bases de datos externas compatibles dependen del modelo de alojamiento. Obtenga más información en [Matriz de compatibilidad de Campaign](../../rn/using/compatibility-matrix.md).

**Consulte también**

* [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md)
* [Notas de la versión](../../rn/using/latest-release.md)
* [actualizaciones de Campaign Classic](../../rn/using/rn-overview.md)
* [Funciones obsoletas y eliminadas](../../rn/using/deprecated-features.md)
* [Versiones de [!DNL Gold Standard]](../../rn/using/gold-standard.md)
