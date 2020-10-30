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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '93'
ht-degree: 100%

---


# Actualizar acumulado{#update-aggregate}

Los agregados se especifican en el nivel de cubo para fines informativos. Una pestaña **[!UICONTROL Workflow]** está disponible al configurar un acumulado.

Para obtener más información sobre los cubos y el uso de los acumulados en Adobe Campaign, consulte la [sección](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

La actividad **[!UICONTROL Update aggregate]** permite seleccionar el modo de actualización para aplicar: completo o parcial.

De forma predeterminada, se lleva a cabo una actualización completa durante cada cálculo. Para activar una actualización parcial, seleccione la opción correspondiente y defina las condiciones de actualización.

![](assets/s_advuser_cube_agregate_05.png)

**Good practice**: se puede utilizar una actividad **[!UICONTROL Scheduler]** para especificar la frecuencia de las actualizaciones de cálculo.

![](assets/s_advuser_cube_agregate_04.png)

