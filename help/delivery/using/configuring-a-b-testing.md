---
solution: Campaign Classic
product: campaign
title: Configuración de la prueba A/B
description: Obtenga información sobre cómo configurar la prueba A/B en Campaign Classic.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: a341980e9d940857388bb2755e5eaa74824cf6ea
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---


# Configuración de la prueba A/B {#configuring-a-b-testing}

En esta sección se explica cómo crear un flujo de trabajo para realizar pruebas A/B.

1. Cree un nuevo flujo de trabajo y luego configure una actividad [de Consulta](../../workflow/using/query.md) para destinatario de la población deseada.

1. Añada una actividad [Split](../../workflow/using/split.md) para dividir la población objetivo en varios subconjuntos.

1. Abra la actividad y luego configure cada subconjunto según sus necesidades. Para obtener más información sobre cómo configurar una actividad **[!UICONTROL Split]**, consulte [esta sección](../../workflow/using/split.md).

   En este ejemplo, queremos probar dos temas nuevos para un boletín de noticias presentando cada uno de ellos al 10 % de la población objetivo.

   ![](assets/ab-testing-split.png)

1. Añada una transición para enviar a la población restante la newsletter con el asunto actual. Para ello, active la opción **[!UICONTROL Generate complement]** desde la ficha **[!UICONTROL General]**.

   ![](assets/ab-testing-complement.png)

1. Para cada subconjunto, agregue la versión del envío que se va a probar.

   ![](assets/ab-testing-delivery.png)

Ahora puede realizar el inicio del flujo de trabajo. Una vez enviados los envíos, podrá rastrear el comportamiento de los tres subconjuntos en los registros de envío, para ver qué asunto ha tenido más éxito.

Los flujos de trabajo también le permiten automatizar sus procesos identificando automáticamente la variante de envío que tuvo un mejor rendimiento y, a continuación, enviándola a la población restante. Para obtener más información sobre esto, consulte este [caso de uso](../../delivery/using/a-b-testing-use-case.md) dedicado.
