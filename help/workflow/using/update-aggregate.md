---
title: Actualizar acumulado
seo-title: Actualizar acumulado
description: Actualizar acumulado
seo-description: null
page-status-flag: never-activated
uuid: 34ae42e1-da34-43be-b219-0b3b872177b3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 031f8d5d-940c-4a4c-97e7-ad4ef61983c1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Actualizar acumulado{#update-aggregate}

Los agregados se especifican en el nivel de cubo para fines informativos. A **[!UICONTROL Workflow]** tab is available when configuring an aggregate.

Para obtener más información sobre los cubos y el uso de los acumulados en Adobe Campaign, consulte la [sección](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

The **[!UICONTROL Update aggregate]** activity lets you select the update mode to apply: full or partial.

De forma predeterminada, se lleva a cabo una actualización completa durante cada cálculo. Para activar una actualización parcial, seleccione la opción correspondiente y defina las condiciones de actualización.

![](assets/s_advuser_cube_agregate_05.png)

**Buenas prácticas**: se puede usar una **[!UICONTROL Scheduler]** actividad para especificar la frecuencia de las actualizaciones de cálculo.

![](assets/s_advuser_cube_agregate_04.png)

