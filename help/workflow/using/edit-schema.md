---
product: campaign
title: Edición del esquema
description: Descubra más información sobre la actividad del flujo de trabajo Edición del esquema
feature: Workflows, Targeting Activity
exl-id: d26966a8-b5db-4fa4-85ec-7ebd770c4ef3
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 100%

---

# Edición del esquema{#edit-schema}



En el flujo de trabajo, los datos se pueden transformar, normalizar y, si es necesario, ampliar utilizando la actividad **[!UICONTROL Edit schema]**. Se suele utilizar para normalizar la estructura de datos: puede cambiar el nombre de las columnas de salida o modificar su contenido, por ejemplo, calculando los valores promedio de un campo o agregados.

Esta actividad no cambia los datos de la lista de trabajo, solo cambia su esquema, es decir, la vista lógica de los datos.

![](assets/wf_manipulation_box.png)

También se pueden crear vínculos con otras tablas de resultados a través de la pestaña **[!UICONTROL Links]**.

![](assets/wf_manipulation_box_link_tab.png)

La sección inferior permite configurar la lista de condiciones del vínculo, es decir, los criterios utilizados para reconciliar los datos de las dos tablas.
