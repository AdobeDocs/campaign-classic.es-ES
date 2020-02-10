---
title: Acerca del gestor de respuestas
seo-title: Acerca del gestor de respuestas
description: Acerca del gestor de respuestas
seo-description: null
page-status-flag: never-activated
uuid: 3087a96d-50fb-488a-9b76-70eb5c67deed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: a4669fee-4512-455f-b495-ebd5a0746b76
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Acerca del gestor de respuestas{#about-response-manager}

## Objetivos {#objectives}

Adobe Campaign ofrece una aplicación de gestión de respuestas (Response Manager)
				que le permite medir el éxito y la rentabilidad de las campañas de marketing u ofrecer
				propuestas para todos los canales de comunicación (correo electrónico, móvil, teléfono, correo postal,
				fax, agencia, etc.).

## Concepto de hipótesis {#hypothesis-concept}

Las Hipótesis se pueden configurar en un periodo determinado desde la fecha de contacto para deducir el comportamiento de los usuarios después de recibir un envío. Estas hipótesis se basan en una tabla de **transacción** que guarda compras y detalles de estas compras.

Las hipótesis están limitadas en el tiempo y pueden aplicarse a un grupo de control para compararlas con la población de destino. Los resultados de Hipótesis se proporcionan mediante **indicadores** que se actualizan automáticamente una vez finalizado el cálculo. El ROI (retorno de la inversión) vinculado a la hipótesis se tomará en cuenta en los informes de campaña.

Además, los **informes** proporcionados con el Gestor de respuestas permiten resumir la información vinculada a los aumentos de facturación, el cálculo de los márgenes, así como el ROI del envío o la oferta.

Además, gracias a las líneas de detalle de compra, puede especificar su hipótesis para que solo se centre en un producto concreto, por ejemplo.

Por ejemplo: después de que un envío promocione un artículo, deseamos evaluar los ingresos generados. Aplicamos la hipótesis de que cualquier destinatario que haya comprado al menos un artículo en el mes siguiente a la activación del envío ha reaccionado a esta acción. El gestor de respuestas va a determinar, en función de esta hipótesis, qué líneas de solicitud de compra deben asignarse. A continuación, según esto, será posible determinar los ingresos resultantes como suma de estas líneas.

>[!CAUTION]
>
>El Administrador de respuestas es una **[!UICONTROL Campaign]** opción. Compruebe el acuerdo de licencia.

También puede calcular todas las reacciones de todo el hogar del destinatario que recibió el envío u oferta.

Cada hipótesis está vinculada a una única tabla de transacción. Un envío u oferta se puede vincular a varias hipótesis.

## Método {#method}

Before you start using Response Manager, refer to [Configuration](../../campaign/using/configuration.md) and carry out the necessary configurations.

Para iniciar una hipótesis en un envío o una oferta, debe definir su contexto en una plantilla que se utilizará para cada hipótesis que cree.

Para definir y crear hipótesis de medición, aplique el siguiente proceso:

1. Defina un modelo de hipótesis. Consulte [Creación de un modelo](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)de hipótesis.
1. Cree una o más hipótesis en un envío existente. Refer to [Referencing a hypothesis in a campaign delivery](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery).

   o

   Cree una o más hipótesis en las ofertas. Consulte [Creación de una hipótesis en una oferta](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer).

1. Compruebe los resultados de las hipótesis. Consulte Seguimiento [de hipótesis](../../campaign/using/hypothesis-tracking.md).
1. Vuelva a lanzar las hipótesis si es necesario. Refer to [Creating a hypothesis on the fly on a delivery](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery).

