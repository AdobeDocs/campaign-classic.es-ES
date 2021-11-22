---
product: campaign
title: Actualización del agregado
description: Descubra más información acerca de la actividad del flujo de trabajo Actualización de agregado
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 100%

---

# Actualización de agregado{#update-aggregate}

![](../../assets/common.svg)

Los agregados se especifican en el nivel de cubo para fines de creación de informes. Una pestaña **[!UICONTROL Workflow]** está disponible al configurar un acumulado.

Para obtener más información sobre los cubos y el uso de los acumulados en Adobe Campaign, consulte la [sección](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

La actividad **[!UICONTROL Update aggregate]** permite seleccionar el modo de actualización para aplicar: completo o parcial.

De forma predeterminada, se lleva a cabo una actualización completa durante cada cálculo. Para activar una actualización parcial, seleccione la opción correspondiente y defina las condiciones de actualización.

![](assets/s_advuser_cube_agregate_05.png)

**Good practice**: se puede utilizar una actividad **[!UICONTROL Scheduler]** para especificar la frecuencia de las actualizaciones de cálculo.

![](assets/s_advuser_cube_agregate_04.png)
