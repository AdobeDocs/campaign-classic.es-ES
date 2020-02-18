---
title: Tipos de envíos
seo-title: Tipos de envíos
description: Tipos de envíos
seo-description: null
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# Tipos de envíos{#types-of-deliveries}

Existen tres tipos de objetos de envío en Campaign:

## Envío único {#single-delivery}

Un **envío** es un objeto de envío independiente que se ejecuta una vez. Puede duplicarse y prepararse de nuevo; sin embargo, cuando esté en su estado final (cancelado, detenido, finalizado), no se puede volver a utilizar.

Los envíos se pueden crear desde la lista de envíos o dentro de un flujo de trabajo mediante una actividad de [envío](../../workflow/using/delivery.md).

Los flujos de trabajo también proporcionan actividades de envío específicas según el tipo de canal que desee utilizar. For more on these activities, refer to [this section](../../workflow/using/cross-channel-deliveries.md).

## Envío recurrente {#recurring-delivery}

Un **envío recurrente** le permite crear un nuevo envío cada vez que se ejecute la actividad. Esto evita tener que crear un nuevo envío para las tareas recurrentes.

Por ejemplo, si ejecuta este tipo de actividad una vez al mes, tras un año acaba teniendo 12 envíos.

Los envíos recurrentes se crean en los flujos de trabajo a través de la actividad de [envío recurrente](../../workflow/using/recurring-delivery.md). En esta sección se muestra un ejemplo de esta actividad: [Creación de una entrega recurrente en un flujo de trabajo](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-recurring-delivery-in-a-targeting-workflow)de segmentación.

## Envío continuo {#continuous-delivery}

Un **envío continuo** le permite añadir nuevos destinatarios a un envío existente, lo que evita tener que crear un nuevo envío cada vez que se ejecuta.

Si cambia la información del envío (contenido, nombre, etc.), se crea un nuevo objeto de envío en la ejecución del envío. Si no se ha cambiado ninguna información, se vuelve a utilizar el mismo objeto de envío y los “logs” de envío y seguimiento se añaden en el mismo objeto.

Por ejemplo, si ejecuta este tipo de actividad una vez al mes, acaba teniendo un solo envío después de un año (siempre y cuando no haya realizado ningún cambio en el envío).

Continuous deliveries are created within workflows via the [Continuous delivery activity](../../workflow/using/continuous-delivery.md).
