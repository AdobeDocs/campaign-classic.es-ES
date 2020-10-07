---
title: Carga de datos (RDBMS)
seo-title: Carga de datos (RDBMS)
description: Carga de datos (RDBMS)
seo-description: null
page-status-flag: never-activated
uuid: d5ec30f2-398a-4b16-9232-924437da146a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: a128caac-5740-4dac-b14d-1d2fcef3cc69
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 75%

---


# Carga de datos (RDBMS){#data-loading-rdbms}

The **[!UICONTROL Data loading (RDBMS)]** activity lets you access this external database directly and to collect only the data required for targeting.

Para mejorar el rendimiento, recomendamos utilizar la actividad de consulta (donde se pueden utilizar los datos de una base de datos externa). Para obtener más información, consulte [Acceso a una base de datos externa (FDA)](../../workflow/using/accessing-an-external-database--fda-.md).

La operación es la siguiente:

1. Seleccione el origen de los datos de la lista e introduzca el nombre de la tabla que contiene los datos que se van a extraer.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   El nombre de la tabla introducida en el campo correspondiente se utiliza como plantilla para recopilar datos en la base de datos externa. El nombre de la tabla procesada por el flujo de trabajo se puede calcular o transmitir mediante la transición de entrada de la actividad de carga de datos. To select the table to be used, click the **[!UICONTROL Advanced..]**. y seleccione la **[!UICONTROL Specified in the transition]** opción o **[!UICONTROL Explicit]** .

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Click the **[!UICONTROL Select the columns to extract...]** link to choose the data to be collected in the database.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. Puede definir un filtro en estos datos. Para ello, haga clic en el vínculo **[!UICONTROL Edit query....]**.

   Los datos recopilados de esta manera se pueden utilizar en todo el ciclo de vida del flujo de trabajo.

