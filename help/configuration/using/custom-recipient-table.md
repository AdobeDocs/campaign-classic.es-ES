---
title: Acerca del modelo de datos de Adobe Campaign Classic
description: Este documento describe los conceptos básicos del modelo de datos de Adobe Campaign Classic.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 65affa58a66090c3bffc837fdbd85aa46338bd3e

---


# Uso de una tabla de destinatarios personalizada{#custom-recipient-table}

Al diseñar el modelo de datos de Adobe Campaign, puede utilizar la tabla [Destinatario lista](../../configuration/using/default-recipient-table.md)para usar o decidir crear una tabla de destinatarios no estándar para almacenar sus perfiles de marketing.

De hecho, si el modelo de datos no se ajusta a la estructura centrada en el destinatario, puede configurar otras tablas como dimensión de objetivo dentro de Adobe Campaign. Por ejemplo, esto puede ser relevante cuando necesita dirigirse a hogares, cuentas (como teléfonos móviles) y empresas o sitios en lugar de simplemente destinatarios.

>[!NOTE]
>
>En este caso, deberá crear una nueva asignación [de](../../configuration/using/target-mapping.md)objetivos.

En esta [sección](../../configuration/using/about-custom-recipient-table.md)se detallan todos los principios y pasos necesarios para utilizar una tabla de destinatarios personalizada.

Las ventajas de utilizar una tabla de destinatarios personalizada son las siguientes:

## Modelo de datos flexible {#flexible-data-model}

La tabla Destinatario lista para usar es inútil si no necesita la mayoría de los campos de la tabla Destinatario o si el modelo de datos no está centrado en el destinatario.

## Escalabilidad {#scalability}

Los grandes volúmenes requieren una tabla optimizada con pocos campos para un diseño eficiente. La tabla Destinatario lista para usar tendría demasiados campos inútiles, lo que podría afectar al rendimiento y a la falta de eficiencia.

## Ubicación de datos {#data-location}

Si los datos residen en una base de datos de mercadotecnia existente externa, es posible que sea necesario realizar demasiado esfuerzo para utilizar la tabla de destinatarios lista para usar. Crear uno nuevo basado en una estructura existente es más sencillo.

## Fácil migración {#easy-migration}

No se necesita mantenimiento para comprobar que todas las extensiones siguen siendo válidas al actualizar.

>[!IMPORTANT]
>
>El uso de una tabla de destinatarios personalizada está reservada para usuarios avanzados y está sujeto a algunas limitaciones. Para obtener más información sobre esto, consulte esta sección.
