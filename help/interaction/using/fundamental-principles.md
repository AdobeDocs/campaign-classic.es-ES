---
solution: Campaign Classic
product: campaign
title: Principios fundamentales
description: Principios fundamentales
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: b13ecfc9-1723-42b2-ab30-d5637cc3d0dd
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '338'
ht-degree: 100%

---

# Principios fundamentales{#fundamental-principles}

## Implementación de entornos {#deploying-environments}

Para cada dimensión de segmentación existen dos entornos utilizados al gestionar las ofertas:

* Un entorno de diseño en el que el gestor de ofertas se encarga de la creación y la clasificación de las ofertas, la edición y el inicio del proceso de aprobación para que se puedan utilizar. También se definen en este entorno: las reglas para cada categoría, los espacios de oferta en los que se pueden presentar las mismas y los filtros predefinidos utilizados para determinar una oferta.

   Las categorías también se pueden publicar manualmente en el entorno en línea.

   El proceso de aprobación de ofertas se detalla en la sección [Aprobación y activación de ofertas](../../interaction/using/approving-and-activating-an-offer.md).

* Un entorno interactivo en el que se pueden encontrar ofertas aprobadas del entorno de diseño, así como los diversos espacios de ofertas, filtros, categorías y reglas configuradas en el entorno de diseño. Durante el acceso al motor de oferta, este siempre utiliza las ofertas del entorno interactivo.

Una oferta solo se implementa en los espacios de oferta seleccionados durante el proceso de aprobación. Por lo tanto, una oferta puede estar activa pero no puede utilizarse en un espacio de oferta que también esté activo.

![](assets/architecture_interaction1.png)

## Tipos de interacción y métodos de contacto {#interaction-types-and-contact-methods}

Existen dos posibles tipos de interacciones: interacciones entrantes (iniciadas por un contacto) e interacciones salientes (iniciadas por el generador de la oferta).

Estos dos tipos de interacciones se pueden llevar a cabo tanto en modo unitario (la oferta se determina para un único contacto) o en modo agrupado (la oferta se determina para un conjunto de contactos). Por lo general, las interacciones entrantes se realizan en modo unitario y las interacciones salientes se llevan a cabo en modo agrupado. Sin embargo, puede haber ciertas excepciones, por ejemplo, para los mensajes de transacción cuya interacción saliente se realiza en modo unitario (consulte [esta sección](../../message-center/using/about-transactional-messaging.md)).

En cuanto se puede, o se debe, presentar una oferta (según las configuraciones llevadas a cabo), el motor de oferta realiza la función de intermediario: calcula automáticamente la mejor oferta posible para un contacto entre las disponibles combinando los datos recibidos sobre dicho contacto y las diferentes reglas que se pueden aplicar según lo especificado en la propuesta.

![](assets/architecture_interaction2.png)
