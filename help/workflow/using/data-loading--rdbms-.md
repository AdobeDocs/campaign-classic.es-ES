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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Carga de datos (RDBMS){#data-loading-rdbms}

The **[!UICONTROL Data loading (RDBMS)]** activity lets you access this external database directly and to collect only the data required for targeting.

Para mejorar el rendimiento, recomendamos utilizar la actividad de consulta (donde se pueden utilizar los datos de una base de datos externa). Para obtener más información sobre esto, consulte [Acceso a una base de datos externa (FDA)](../../workflow/using/accessing-an-external-database--fda-.md).

La operación es la siguiente:

1. Seleccione el origen de los datos de la lista e introduzca el nombre de la tabla que contiene los datos que se van a extraer.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   El nombre de la tabla introducida en el campo correspondiente se utiliza como plantilla para recopilar datos en la base de datos externa. El nombre de la tabla procesada por el flujo de trabajo se puede calcular o transmitir mediante la transición de entrada de la actividad de carga de datos. Para seleccionar la tabla que se va a utilizar, haga clic en la **[!UICONTROL Advanced..]**. y seleccione la **[!UICONTROL Specified in the transition]** opción o **[!UICONTROL Explicit]** .

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Click the **[!UICONTROL Select the columns to extract...]** link to choose the data to be collected in the database.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. Puede definir un filtro en estos datos. Para ello, haga clic en el **[!UICONTROL Edit query....]** vínculo.

   Los datos recopilados de esta manera se pueden utilizar en todo el ciclo de vida del flujo de trabajo.

