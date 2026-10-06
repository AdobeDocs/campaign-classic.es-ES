---
product: campaign
title: Configuración de ejecución
description: Configuración de ejecución
feature: Interaction, Offers
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: e2dea4a0-9ed8-47b6-a16b-eeee653d2290
TQID: 'https://experienceleague.adobe.com/k2-e-laXDXtVyBJnoiyKAdNHKiS3nB-t1X1cEaqeudM'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
    internal-label: Offer Management
  - id: 65702805-0026-5ca1-843a-144fa79f0883
    internal-label: Interaction
  - id: ea08db70-4682-59a2-9408-9aedd9548e07
    internal-label: Offers
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 100%
---
# Configuración de ejecución{#execution-settings}



En caso necesario, se pueden especificar los ajustes de ejecución al crear la simulación. Estos ajustes permiten ejecutar la simulación durante un periodo de baja actividad en función de su prioridad o guardar consultas SQL en el registro. Este paso es opcional.

Estos ajustes se pueden cambiar posteriormente en la pestaña **[!UICONTROL General]** de la ventana de simulación.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]**: permite programar la simulación en función de la prioridad elegida (baja, media o alta) para optimizar el rendimiento de Adobe Campaign.
* **[!UICONTROL Priority]**: este es el nivel que se aplica a la simulación para programarla. Cuando se marca la opción **[!UICONTROL Schedule execution for a time of low activity]**, el flujo de trabajo del procesamiento de la campaña selecciona un periodo de actividad baja para iniciarla.
* **[!UICONTROL Log SQL queries in the journal]**: esta opción solo es para usuarios expertos. Permite añadir una pestaña al registro que muestra las consultas SQL para detectar los posibles fallos de funcionamiento, en caso de que la simulación termine con errores.
