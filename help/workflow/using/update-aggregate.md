---
solution: Campaign Classic
product: campaign
title: Actualizar acumulado
description: Descubra más información sobre la actividad del flujo de trabajo Actualizar acumulado
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '96'
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

