---
title: Inicio y final (Start y End)
description: Más información sobre las actividades de flujo de trabajo de Inicio y finalización
page-status-flag: never-activated
uuid: ec0c818c-c307-4f50-908c-507bce0ea27b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 8b239d5e-2317-42c8-9fee-7d40bea624da
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 93%

---


# Inicio y final (Start y End){#start-and-end}

Las actividades **[!UICONTROL Start]** y **[!UICONTROL End]** permiten marcar de forma gráfica el inicio y el final de un flujo de trabajo. Estas actividades no tienen impacto funcional y, por tanto, son opcionales.

* **[!UICONTROL Start]**

   La ejecución de un flujo de trabajo comienza con actividades sin una transición entrante y actividades del tipo inicial.

   ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL End]**

   Puede configurar la actividad **[!UICONTROL End]** para interrumpir todas las tareas que estén en curso. Para ello, haga doble clic en la actividad para mostrar sus propiedades y marque la opción apropiada.

   ![](assets/s_user_segmentation_end.png)

   Los datos de la tabla de trabajo se eliminan automáticamente cuando se activa la actividad final. Si no es necesario y para evitar cargas innecesarias, puede optar por deshabilitar la transición en la última salida de actividad. Por ejemplo, en una salida de envío, si no hay ningún proceso programado, anule la selección de la opción correspondiente como se muestra a continuación:

   ![](assets/s_advuser_delivery_option_no_output.png)

