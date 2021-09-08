---
title: Cambiar fuente de datos
description: Descubra más información sobre la actividad Cambiar fuente de datos
audience: workflow
content-type: reference
topic-tags: targeting-activities
source-git-commit: 9fc4add3f12e3f06b031c4969bd8409c67e4359e
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---

# Cambiar fuente de datos {#change-data-source}

>[!NOTE]
>
> La actividad **[!UICONTROL Change data source]** solo está disponible con el paquete **[!UICONTROL Access to external data (Federated Data Access)]** . Para obtener más información sobre los paquetes integrados de Adobe Campaign Classic, consulte esta [página](../../installation/using/installing-campaign-standard-packages.md).

La actividad **[!UICONTROL Change data source]** permite cambiar la fuente de datos de un flujo de trabajo **[!UICONTROL Working table]**. Esto proporciona más flexibilidad para administrar los datos en diferentes fuentes de datos, como FDA, FFDA y bases de datos locales.

El **[!UICONTROL Working table]** permite que el flujo de trabajo de Adobe Campaign Classic gestione datos y comparta datos con las actividades de flujo de trabajo.
De forma predeterminada, el **[!UICONTROL Working table]** se crea en la misma base de datos que el origen de los datos en los que consultamos.

Por ejemplo, al consultar la tabla **[!UICONTROL Profiles]**, almacenada en la base de datos de Cloud, creará un **[!UICONTROL Working table]** en la misma base de datos de Cloud.
Para cambiar esto, puede agregar la actividad **[!UICONTROL Change Data Source]** para elegir una fuente de datos diferente para su **[!UICONTROL Working table]**.

Tenga en cuenta que al utilizar la actividad **[!UICONTROL Change Data Source]** , deberá volver a la base de datos de Cloud para continuar con la ejecución del flujo de trabajo.

Para utilizar la actividad **[!UICONTROL Change Data Source]**:

1. Creación de un flujo de trabajo.

1. Consulte a los destinatarios objetivo con una actividad **[!UICONTROL Query]**.

   Para obtener más información sobre la actividad **[!UICONTROL Query]**, consulte esta [página](../../workflow/using/query.md#creating-a-query).

1. En la pestaña **[!UICONTROL Targeting]**, añada una actividad **[!UICONTROL Change data source]**.

   ![](assets/change-data-source.png)

1. Haga doble clic en la actividad **[!UICONTROL Change data source]** para seleccionar **[!UICONTROL Default data source]**.

   La tabla de trabajo, que contiene el resultado de la consulta, se mueve a la base de datos predeterminada PostgreSQL.

   ![](assets/change-data-source_2.png)

1. En la pestaña **[!UICONTROL Actions]** , arrastre y suelte una actividad **[!UICONTROL JavaScript code]** para realizar operaciones unitarias en la tabla de trabajo.

   Para obtener más información sobre la actividad **[!UICONTROL JavaScript code]** , consulte la página [Código JavaScript y código JavaScript avanzado](../../workflow/using/sql-code-and-javascript-code.md#javascript-code) .

1. Agregue otra actividad **[!UICONTROL Change data source]** para volver a la base de datos de Cloud.

1. Haga doble clic en la actividad y seleccione **[!UICONTROL Active FDA external account]** y luego la cuenta externa **[!UICONTROL External database]** correspondiente.

   ![](assets/change-data-source_3.png)

1. Ahora puede iniciar el flujo de trabajo.
