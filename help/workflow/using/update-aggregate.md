---
product: campaign
title: Actualización del agregado
description: Descubra más información acerca de la actividad del flujo de trabajo Actualización de agregado
feature: Workflows
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 100%

---

# Actualización de agregado{#update-aggregate}



Los agregados se especifican en el nivel de cubo para fines de creación de informes. Una pestaña **[!UICONTROL Workflow]** está disponible al configurar un acumulado.

Los acumulados son útiles para manipular grandes volúmenes de datos. Se actualizan automáticamente según la configuración definida en la casilla de flujo de trabajo dedicado para integrar los datos recopilados recientemente en los indicadores.

Los acumulados se definen en la pestaña correspondiente de cada cubo.

![](assets/s_advuser_cube_agregate_01.png)


La actividad **[!UICONTROL Update aggregate]** permite seleccionar el modo de actualización para aplicar: completo o parcial.

De forma predeterminada, se lleva a cabo una actualización completa durante cada cálculo. Para activar una actualización parcial, seleccione la opción correspondiente y defina las condiciones de actualización.

![](assets/s_advuser_cube_agregate_05.png)

**Good practice**: se puede utilizar una actividad **[!UICONTROL Scheduler]** para especificar la frecuencia de las actualizaciones de cálculo.

![](assets/s_advuser_cube_agregate_04.png)
