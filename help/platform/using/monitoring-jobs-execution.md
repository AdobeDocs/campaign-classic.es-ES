---
solution: Campaign Classic
product: campaign
title: Supervisión de la ejecución de trabajos
description: Obtenga información sobre cómo supervisar la ejecución de trabajos de importación y exportación.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 100%

---


# Supervisión de la ejecución de trabajos {#monitoring-job-execution}

Puede realizar un seguimiento de la ejecución de los trabajos de importación y exportación directamente desde la lista de los trabajos de importación y exportación.

![](assets/s_ncs_user_export_list_and_details.png)

* La pestaña **[!UICONTROL Journal]** permite ver los mensajes de registro relacionados con la ejecución.
* La pestaña **[!UICONTROL Rejects]** contiene los registros rechazados. Consulte [Comportamiento en caso de error](../../platform/using/executing-import-jobs.md#behavior-in-the-event-of-an-error).

En la pestaña **[!UICONTROL General]**, el campo **[!UICONTROL Status]** indica el estado actual de un trabajo.

Cada estado aparece representado mediante un icono especial y una etiqueta. Los estados y sus iconos se enumeran a continuación:

![](assets/s_ncs_user_export_status.png)

* **Edición en curso**

   Se está creando el trabajo.

* **Ejecución en curso**

   Se está ejecutando el trabajo.

* **Cancelar**

   Haga clic en el botón **[!UICONTROL Cancel]**: el trabajo en curso se cancela.

* **Cancelación en curso**

   El comando de cancelación se ha ejecutado y el trabajo se está cancelando.

* **Pausa en curso**

   Haga clic en **[!UICONTROL Pause]**: el trabajo se suspende.

* **En pausa**

   Haga clic en **[!UICONTROL Pause]**: el trabajo está suspendido. Se puede reiniciar haciendo clic en **[!UICONTROL Start]**.

* **Finalizado**

   La ejecución del trabajo ha finalizado.

* **Finalizado con error**

   No se ha ejecutado el trabajo debido a un error técnico.

* **Apagado del servidor en progreso**

   El trabajo se ha interrumpido porque el servidor de Adobe Campaign se ha cerrado.
