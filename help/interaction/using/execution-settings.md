---
title: Ajustes de ejecución
seo-title: Ajustes de ejecución
description: Ajustes de ejecución
seo-description: null
page-status-flag: never-activated
uuid: a6549091-0c33-4fe1-adde-de3b285dd456
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: simulating-offers
discoiquuid: 52b5d5a9-10dc-4601-8fe4-962a2334322b
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '140'
ht-degree: 100%

---


# Ajustes de ejecución{#execution-settings}

En caso necesario, se pueden especificar los ajustes de ejecución al crear la simulación. Estos ajustes permiten ejecutar la simulación durante un periodo de baja actividad en función de su prioridad o guardar consultas SQL en el registro. Este paso es opcional.

Estos ajustes se pueden cambiar posteriormente en la pestaña **[!UICONTROL General]** de la ventana de simulación.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]**: permite programar la simulación en función de la prioridad elegida (baja, media o alta) para optimizar el rendimiento de Adobe Campaign.
* **[!UICONTROL Priority]**: este es el nivel que se aplica a la simulación para programarla. Cuando se marca la opción **[!UICONTROL Schedule execution for a time of low activity]**, el flujo de trabajo del procesamiento de la campaña selecciona un periodo de actividad baja para iniciarla.
* **[!UICONTROL Log SQL queries in the journal]**: esta opción solo es para usuarios expertos. Permite añadir una pestaña al registro que muestra las consultas SQL para detectar los posibles fallos de funcionamiento, en caso de que la simulación termine con errores.

