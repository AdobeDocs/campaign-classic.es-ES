---
product: campaign
title: Edición del esquema
description: Descubra más información sobre la actividad del flujo de trabajo Edición del esquema
feature: Workflows, Targeting Activity
hide: true
exl-id: d26966a8-b5db-4fa4-85ec-7ebd770c4ef3
TQID: 'https://experienceleague.adobe.com/cxBDJJXifg7C4vtB5MPBYSluRpgnbsBkDiuSsnIHDYo'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: ff84ab2f-a7c2-4ced-a3c8-5113f4348d99
    internal-label: Targeting Activity
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 100%
---
# Edición del esquema{#edit-schema}



En el flujo de trabajo, los datos se pueden transformar, normalizar y, si es necesario, ampliar utilizando la actividad **[!UICONTROL Edit schema]**. Se suele utilizar para normalizar la estructura de datos: puede cambiar el nombre de las columnas de salida o modificar su contenido, por ejemplo, calculando los valores promedio de un campo o agregados.

Esta actividad no cambia los datos de la tabla de trabajo, solo cambia su esquema, es decir, la vista lógica de los datos.

![](assets/wf_manipulation_box.png)

También se pueden crear vínculos con otras tablas de trabajo a través de la pestaña **[!UICONTROL Links]**.

![](assets/wf_manipulation_box_link_tab.png)

La sección inferior permite configurar la lista de condiciones del vínculo, es decir, los criterios utilizados para reconciliar los datos de las dos tablas.
