---
title: Carga de datos (RDBMS)
description: Más información sobre la actividad del flujo de trabajo de carga de datos (RDBMS)
page-status-flag: never-activated
uuid: d5ec30f2-398a-4b16-9232-924437da146a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: a128caac-5740-4dac-b14d-1d2fcef3cc69
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 95%

---


# Carga de datos (RDBMS){#data-loading-rdbms}

La actividad **[!UICONTROL Data loading (RDBMS)]** permite acceder a esta base de datos externa directamente y recopilar solamente los datos necesarios para el objetivo.

Para mejorar el rendimiento, recomendamos utilizar la actividad de consulta (donde se pueden utilizar los datos de una base de datos externa). Para obtener más información, consulte [Acceso a una base de datos externa (FDA)](../../workflow/using/accessing-an-external-database--fda-.md).

La operación es la siguiente:

1. Seleccione el origen de los datos de la lista e introduzca el nombre de la tabla que contiene los datos que se van a extraer.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   El nombre de la tabla introducida en el campo correspondiente se utiliza como plantilla para recopilar datos en la base de datos externa. El nombre de la tabla procesada por el flujo de trabajo se puede calcular o transmitir mediante la transición de entrada de la actividad de carga de datos. Para seleccionar la tabla que se va a utilizar, haga clic en **[!UICONTROL Advanced..]**. vínculo y seleccione la opción **[!UICONTROL Specified in the transition]** o **[!UICONTROL Explicit]**.

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Haga clic en el vínculo **[!UICONTROL Select the columns to extract...]** para elegir los datos que se deben recopilar en la base de datos.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. Puede definir un filtro en estos datos. Para ello, haga clic en el vínculo **[!UICONTROL Edit query....]**.

   Los datos recopilados de esta manera se pueden utilizar en todo el ciclo de vida del flujo de trabajo.

