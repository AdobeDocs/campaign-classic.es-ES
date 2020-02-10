---
title: Uso de la tabla Destinatarios de Adobe Campaign Classic
description: Descubra cómo utilizar la tabla de destinatarios lista para usar en Adobe Campaign Classic al diseñar su modelo de datos.
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


# Uso de la tabla de destinatarios predeterminada{#default-recipient-table}

La tabla Destinatario lista para usar de Adobe Campaign proporciona un buen punto de partida para crear el modelo de datos. Tiene una serie de campos predefinidos y vínculos de tabla que se pueden ampliar fácilmente. Esto resulta especialmente útil cuando se dirige principalmente a destinatarios, ya que se ajusta a un modelo de datos sencillo centrado en el destinatario.

Las ventajas de utilizar la tabla de destinatarios estándar son las siguientes:

* Trabajar de forma predeterminada con funcionalidades como suscripciones, listas de inicio, encuestas, sociales, etc.
* Proporcionar una base de datos de marketing con un modelo de datos centrado en el destinatario.
* Implementación más rápida.
* Fácil mantenimiento por parte del apoyo y los socios.

Sin embargo, es posible ampliar la tabla Destinatario, pero no reducir el número de campos o vínculos en la tabla.

>[!IMPORTANT]
>
>Se recomienda no eliminar campos (aunque no sean útiles) en la tabla del destinatario, ya que esto puede provocar errores en los módulos integrados.

Además, como la tabla Destinatario forma parte del producto, tanto la tabla como el formulario asociado evolucionan a medida que cambia el producto. Por lo tanto, se necesita un mantenimiento adicional para comprobar que las extensiones siguen siendo válidas al actualizar.
