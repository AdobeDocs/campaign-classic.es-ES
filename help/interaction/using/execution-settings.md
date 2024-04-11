---
product: campaign
title: Configuración de ejecución
description: Configuración de ejecución
feature: Interaction, Offers
badge-v8: label="También se aplica a la versión 8" type="Positive" tooltip="También se aplica a Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: e2dea4a0-9ed8-47b6-a16b-eeee653d2290
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 97%

---

# Configuración de ejecución{#execution-settings}



En caso necesario, se pueden especificar los ajustes de ejecución al crear la simulación. Estos ajustes permiten ejecutar la simulación durante un periodo de baja actividad en función de su prioridad o guardar consultas SQL en el registro. Este paso es opcional.

Estos ajustes se pueden cambiar posteriormente en la pestaña **[!UICONTROL General]** de la ventana de simulación.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]**: permite programar la simulación en función de la prioridad elegida (baja, media o alta) para optimizar el rendimiento de Adobe Campaign.
* **[!UICONTROL Priority]**: este es el nivel que se aplica a la simulación para programarla. Cuando se marca la opción **[!UICONTROL Schedule execution for a time of low activity]**, el flujo de trabajo del procesamiento de la campaña selecciona un periodo de actividad baja para iniciarla.
* **[!UICONTROL Log SQL queries in the journal]**: esta opción solo es para usuarios expertos. Permite añadir una pestaña al registro que muestra las consultas SQL para detectar los posibles fallos de funcionamiento, en caso de que la simulación termine con errores.
