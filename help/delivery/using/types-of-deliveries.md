---
title: Tipos de entregas
seo-title: Tipos de entregas
description: Tipos de entregas
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
translation-type: ht
source-git-commit: 707352334144df86ae82aa51d595ae6bc751d1f2

---


# Tipos de entregas{#types-of-deliveries}

Existen tres tipos de objetos de envío en Campaign:

## Entrega única {#single-delivery}

Una **entrega** es un objeto de envío independiente que se ejecuta una vez. Puede duplicarse y prepararse de nuevo; sin embargo, cuando esté en su estado final (cancelado, detenido, finalizado), no se puede volver a utilizar.

Las entregas se pueden crear desde la lista de entregas o dentro de un flujo de trabajo mediante una actividad de [entrega](../../workflow/using/delivery.md).

Los flujos de trabajo también proporcionan actividades de entrega específicas según el tipo de canal que desee utilizar. Para obtener más información sobre estas actividades, consulte [esta sección](../../workflow/using/cross-channel-deliveries.md).

## Entrega recurrente {#recurring-delivery}

Una **entrega recurrente** le permite crear un nuevo envío cada vez que se ejecute la actividad. Esto evita tener que crear una nueva entrega para las tareas recurrentes.

Por ejemplo, si ejecuta este tipo de actividad una vez al mes, tras un año acaba teniendo 12 envíos.

Las entregas recurrentes se crean en los flujos de trabajo a través de la actividad de [entrega recurrente](../../workflow/using/recurring-delivery.md). En esta sección se muestra un ejemplo de esta actividad: [Creación de una entrega recurrente en un flujo de trabajo de objetivos](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Entrega continua {#continuous-delivery}

Una **entrega continua** le permite añadir nuevos destinatarios a una entrega existente, lo que evita tener que crear una nueva entrega cada vez que se ejecuta.

Si cambia la información de la entrega (contenido, nombre, etc.), se crea un nuevo objeto de envío en la ejecución de la entrega. Si no se ha cambiado ninguna información, se vuelve a utilizar el mismo objeto de envío y los “logs” de entrega y seguimiento se añaden en el mismo objeto.

Por ejemplo, si ejecuta este tipo de actividad una vez al mes, acaba teniendo un solo envío después de un año (siempre y cuando no haya realizado ningún cambio en la entrega).

Las entregas continuas se crean dentro de flujos de trabajo a través de la [Actividad de entrega continua](../../workflow/using/continuous-delivery.md).
