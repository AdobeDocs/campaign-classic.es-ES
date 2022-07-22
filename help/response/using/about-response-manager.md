---
product: campaign
title: Acerca del gestor de respuestas
description: Acerca del gestor de respuestas
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: ht
source-wordcount: '406'
ht-degree: 100%

---

# Introducción al Gestor de respuestas de Campaign{#about-response-manager}

![](../../assets/v7-only.svg)

Adobe Campaign ofrece una aplicación de gestión de respuestas que le permite medir el éxito y la rentabilidad de las campañas de marketing u ofrecer propuestas para todos los canales de comunicación: correo electrónico, móvil, correo directo, etc.

## Hipótesis {#hypothesis-concept}

Las Hipótesis se pueden configurar en un periodo determinado desde la fecha de contacto para deducir el comportamiento de los usuarios después de recibir una entrega. Estas hipótesis se basan en una tabla de **transacción** que guarda compras y detalles de estas compras.

Las hipótesis están limitadas en el tiempo y pueden aplicarse a un grupo de control para compararlas con la población de destino. Los resultados de Hipótesis se proporcionan mediante **indicadores** que se actualizan automáticamente una vez finalizado el cálculo. El ROI (retorno de la inversión) vinculado a la hipótesis se tomará en cuenta en los informes de campaña.

Además, los **informes** proporcionados con el Gestor de respuestas permiten resumir la información vinculada a los aumentos de facturación, el cálculo de los márgenes, así como el ROI de la entrega o la oferta.

Además, gracias a las líneas de detalle de compra, puede especificar su hipótesis para que solo se centre en un producto concreto, por ejemplo.

Por ejemplo: después de que una entrega promocione un artículo, deseamos evaluar los ingresos generados. Aplicamos la hipótesis de que cualquier destinatario que haya comprado al menos un artículo en el mes siguiente a la activación de la entrega ha reaccionado a esta acción. El gestor de respuestas va a determinar, en función de esta hipótesis, qué líneas de solicitud de compra deben asignarse. A continuación, según esto, será posible determinar los ingresos resultantes como suma de estas líneas.

>[!CAUTION]
>
>El Gestor de respuestas es una opción de **[!UICONTROL Campaign]**. Compruebe el acuerdo de licencia.

También puede calcular todas las reacciones de todo el hogar del destinatario que recibió la entrega u oferta.

Cada hipótesis está vinculada a una única tabla de transacción. Una entrega u oferta se puede vincular a varias hipótesis.

## Pasos de implementación {#method}

Antes de comenzar a utilizar el Gestor de respuestas, consulte [Configuration](configuration.md) y realice las configuraciones necesarias.

Para iniciar una hipótesis en una entrega o una oferta, debe definir su contexto en una plantilla que se utilizará para cada hipótesis que cree.

Para definir y crear hipótesis de medición, aplique el siguiente proceso:

1. Defina un modelo de hipótesis. [Más información](hypothesis-templates.md#creating-a-hypothesis-model)
1. Cree una o más hipótesis en una entrega existente. [Más información](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   o

   Cree una o más hipótesis en las ofertas. [Más información](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. Compruebe los resultados de las hipótesis. [Más información](hypothesis-tracking.md)
1. Vuelva a lanzar las hipótesis si es necesario. [Más información](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
