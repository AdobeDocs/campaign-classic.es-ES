---
solution: Campaign Classic
product: campaign
title: Introducción a la prueba A/B
description: Obtenga más información sobre la prueba A/B en Campaign Classic.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 346b72d522c947b2a2552176b910ded8d622f3ab
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---


# Comience con la prueba A/B {#get-started-a-b-testing}

La prueba A/B le permite comparar varias versiones de un envío entre sí, a fin de identificar cuál tendrá el mayor impacto en la población objetivo.

Para ello, primero debe definir varias variantes del envío. Cada variante se envía luego a las muestras de población para determinar cuál tiene un mejor rendimiento según los criterios de su elección (abre, envía quejas de spam, hace clic en un vínculo específico, ...).

En el ejemplo siguiente, el destinatario de envío se ha dividido en dos grupos, cada uno de los cuales representa el 50% de la población objetivo. Cada grupo recibe dos versiones del envío con dos ofertas promocionales diferentes. Después de enviar el envío, se concluye que la variante A tuvo un mejor rendimiento, en función del número de clics en las ofertas promocionales.

![](assets/a-b-testing-schema.png)

Con Campaign Classic, la prueba A/B se implementa mediante flujos de trabajo, donde se especifica la población en destinatario, así como los grupos que recibirán cada variante (consulte [Configuración de la prueba a/b](../../delivery/using/configuring-a-b-testing.md)).

Los pasos principales son:

1. **** Dirigirse a la población deseada.
1. **Divida la** población en subconjuntos en los que probará las variantes del envío.

   Por ejemplo, puede enviar una versión de un envío a una pequeña parte de la población objetivo y otra versión a la población restante. Esto le permite probar una nueva versión de un envío en lugar del envío que se envía normalmente a sus clientes. También puede dividir la población objetivo en tres grupos para enviarles tres versiones diferentes de un envío.

1. **Cree varias** versiones del envío correspondientes a cada subconjunto. La variante a probar puede ser el asunto, el contenido del mensaje, el nombre del remitente, etc.
1. Inicio el flujo de trabajo y, a continuación, utilice los **registros de envío** para analizar el comportamiento de los subconjuntos con cada variante.

>[!NOTE]
>
>Los flujos de trabajo también le permiten automatizar sus procesos identificando automáticamente la variante de envío que tuvo un mejor rendimiento y, a continuación, enviándola a la población restante. Para obtener más información sobre esto, consulte este [caso de uso](../../delivery/using/a-b-testing-use-case.md) dedicado.
