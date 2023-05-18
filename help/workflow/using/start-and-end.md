---
product: campaign
title: Inicio y final (Start y End)
description: Descubra más información sobre las actividades de flujo de trabajo de Inicio y final (Start y End)
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 56dfbaf3-93de-4ade-b4ad-9b54d239c7a5
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '133'
ht-degree: 100%

---

# Inicio y final{#start-and-end}



Las actividades **[!UICONTROL Start]** y **[!UICONTROL End]** permiten marcar de forma gráfica el inicio y el final de un flujo de trabajo. Estas actividades no tienen impacto funcional y, por tanto, son opcionales.

* **[!UICONTROL Start]**

   La ejecución de un flujo de trabajo comienza con actividades sin una transición entrante y actividades del tipo inicial.

   ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL End]**

   Puede configurar la actividad **[!UICONTROL End]** para interrumpir todas las tareas que estén en curso. Para ello, haga doble clic en la actividad para mostrar sus propiedades y marque la opción apropiada.

   ![](assets/s_user_segmentation_end.png)

   Los datos de la tabla de trabajo se eliminan automáticamente cuando se activa la actividad final. Si no es necesario y para evitar cargas innecesarias, puede optar por deshabilitar la transición en la última salida de actividad. Por ejemplo, en una salida de envío, si no hay ningún proceso programado, anule la selección de la opción correspondiente como se muestra a continuación:

   ![](assets/s_advuser_delivery_option_no_output.png)
