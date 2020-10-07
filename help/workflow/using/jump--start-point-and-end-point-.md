---
title: Saltos (puntos iniciales y finales)
seo-title: Saltos (puntos iniciales y finales)
description: Saltos (puntos iniciales y finales)
seo-description: null
page-status-flag: never-activated
uuid: 68e669eb-6c70-483e-afb7-7340225a6e1d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: f3cd5409-c301-4580-96e3-9349e18cf42a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '122'
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
