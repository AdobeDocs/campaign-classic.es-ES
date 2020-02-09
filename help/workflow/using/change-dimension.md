---
title: Dimensión cambiante
seo-title: Dimensión cambiante
description: Dimensión cambiante
seo-description: null
page-status-flag: never-activated
uuid: 6cb309c0-4096-47ce-b1d4-37a3ddafaaa1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 61583062-2349-4ab3-a3bf-310d21894f34
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Dimensión cambiante{#change-dimension}

La actividad de dimensión cambiante permite cambiar la dimensión de segmentación durante el ciclo de construcción del objetivo. El desplazamiento de ejes depende de la plantilla de datos y de la dimensión de entrada. Esto permite, por ejemplo, cambiar de la dimensión “contratos” a la dimensión “clientes”.

También se puede utilizar esta actividad para definir las columnas adicionales del nuevo destino.

Es posible definir criterios de deduplicación de datos.

## Modo de configuración {#configuration-mode}

Para configurar la actividad de la dimensión de cambio, siga los pasos siguientes:

1. Select the new targeting dimension via the **[!UICONTROL Change dimension]** field.

   ![](assets/s_user_change_dimension_param1.png)

1. Durante el cambio de dimensión, se pueden mantener todos los elementos o seleccionar los que desea conservar en la salida. En el ejemplo siguiente, el número máximo de duplicados se establece en 2.

   ![](assets/s_user_change_dimension_limit.png)

   Cuando decide mantener un solo registro, se muestra una colección en el esquema de trabajo: Esta colección representa todos los registros que no serán objetivo en el resultado final (ya que solo se guarda un registro). Al igual que todas las demás colecciones, este permite calcular las agregaciones o recuperar información en columnas.

   For example, if you change the **[!UICONTROL Customers]** dimension to the **[!UICONTROL Recipients]** dimension, it will be possible to target customers of a specific store, while adding the number of purchases made.

1. Si elige no conservar toda esta información, puede configurar el modo de gestión del duplicado.

   ![](assets/s_user_change_dimension_param2.png)

   Las flechas azules permiten definir la prioridad de procesamiento duplicada.

   En el ejemplo anterior, los destinatarios se deduplicarán en su dirección de correo electrónico primero, luego, si es necesario, en su número de cuenta.

1. The **[!UICONTROL Result]** tab lets you add additional information.

   For example, you can recover the county based on the zip code by using a **Substring** type function. Para ello:

   * Haga clic en el **[!UICONTROL Add data...]** vínculo y seleccione **[!UICONTROL Data linked to the filtering dimension]**.

      ![](assets/wf_change-dimension_sample_01.png)

      >[!NOTE]
      >
      >For information on creating and managing additional columns, refer to [Adding data](../../workflow/using/query.md#adding-data).

   * Seleccione la dimensión de objetivo anterior (antes del conmutador de eje) y seleccione la **[!UICONTROL Zip Code]** en el **[!UICONTROL Location]** subárbol del destinatario y, a continuación, haga clic en **[!UICONTROL Edit expression]**.

      ![](assets/wf_change-dimension_sample_02.png)

   * Haga clic **[!UICONTROL Advanced selection]** y elija **[!UICONTROL Edit the formula using an expression]**.

      ![](assets/wf_change-dimension_sample_03.png)

   * Utilice las funciones ofrecidas en la lista y especifique el cálculo que se va a realizar.

      ![](assets/wf_change-dimension_sample_04.png)

   * Finalmente, introduzca la etiqueta de la columna que acaba de crear.

      ![](assets/wf_change-dimension_sample_05.png)

1. Ejecute el flujo de trabajo para ver el resultado de esta configuración. Compare los datos de las tablas antes y después de la actividad de dimensión cambiante y compare la estructura de las tablas de flujo de trabajo, como se muestra en los ejemplos siguientes:

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)

