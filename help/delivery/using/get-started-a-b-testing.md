---
solution: Campaign Classic
product: campaign
title: Introducción a las pruebas A/B
description: Obtenga más información acerca de las pruebas A/B en Campaign Classic.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: ht
source-git-commit: 346b72d522c947b2a2552176b910ded8d622f3ab
workflow-type: ht
source-wordcount: '350'
ht-degree: 100%

---


# Introducción a las pruebas A/B {#get-started-a-b-testing}

Las pruebas A/B le permiten comparar varias versiones de un envío entre sí, a fin de identificar cuál tendrá mayor impacto en la población objetivo.

Para ello, primero debe definir varias variantes del envío. Cada variante se envía luego a muestras de población para determinar cuál de ellas tiene un mejor rendimiento según los criterios de su elección (abre el mensaje, envía quejas de spam, hace clic en un vínculo específico, etc.).

En el ejemplo siguiente, el destinatario del envío se ha dividido en dos grupos, cada uno de los cuales representa el 50 % de la población objetivo. Cada grupo recibe dos versiones del envío con dos ofertas promocionales diferentes. Tras su envío, se concluye que la variante A tuvo un mejor rendimiento, en función del número de clics en las ofertas promocionales.

![](assets/a-b-testing-schema.png)

Con Campaign Classic, las pruebas A/B se implementan mediante flujos de trabajo, donde se especifica la población objetivo, así como los grupos que recibirán cada variante (consulte [Configuración de las pruebas A/B](../../delivery/using/configuring-a-b-testing.md)).

Los pasos principales son los siguientes:

1. **Establezca como objetivo** la población deseada.
1. **Divida la población** en subconjuntos en los que probar las variantes del envío.

   Por ejemplo, puede enviar una versión a una pequeña parte de la población objetivo y enviar otra a la población restante. Esto le permite probar una nueva versión de un envío, en lugar del envío que se remite normalmente a sus clientes. También puede dividir la población objetivo en tres grupos para hacerles llegar tres versiones diferentes de un envío.

1. **Cree varias versiones** del envío correspondientes a cada subconjunto. La variante que pruebe puede ser el asunto, el contenido del mensaje, el nombre del remitente, etc.
1. Inicie el flujo de trabajo y, a continuación, utilice los **registros de envío** para analizar el comportamiento de los subconjuntos con cada variante.

>[!NOTE]
>
>Los flujos de trabajo también le permiten automatizar los procesos al identificar automáticamente la variante de envío que tuvo un mejor rendimiento y, a continuación, enviarla a la población restante. Para obtener más información al respecto, consulte este [caso de uso](../../delivery/using/a-b-testing-use-case.md).
