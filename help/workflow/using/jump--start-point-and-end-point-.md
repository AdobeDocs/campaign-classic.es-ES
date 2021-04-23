---
solution: Campaign Classic
product: campaign
title: Saltos (puntos iniciales y finales)
description: Saltos (puntos iniciales y finales)
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 0d2d04e7-cb86-4456-b7cf-513c71210355
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '116'
ht-degree: 100%

---

# Saltos (puntos iniciales y finales){#jump-start-point-and-end-point}

Los objetos del tipo gráficos **[!UICONTROL Jump]** se utilizan para mejorar la legibilidad de un diagrama complejo, especialmente uno con transiciones de cruce.

Los saltos son transiciones sin flechas.

Pasan de una actividad a otra, como en el ejemplo siguiente:

![](assets/s_user_segmentation_jump_sample.png)

Para cada transición de tipo “punto inicial”, se debe colocar una transición de tipo “punto final”.

Puede insertar varios saltos de punto iniciales y finales en el mismo flujo de trabajo. Se identifican con un número que se debe introducir en los parámetros:

![](assets/s_user_segmentation_jump_in.png)

Para mejorar la legibilidad del diagrama, puede cambiar la imagen asociada a los saltos para mostrar el número relacionado. Consulte [Gestión de imágenes de actividad](../../workflow/using/managing-activity-images.md).
