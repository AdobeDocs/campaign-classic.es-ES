---
solution: Campaign Classic
product: campaign
title: Dimensión cambiante
description: Dimensión cambiante
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 100%

---


# Dimensión cambiante{#change-dimension}

La actividad para cambiar dimensión permite cambiar la dimensión de segmentación durante el ciclo de construcción del mismo. El desplazamiento de ejes depende de la plantilla de datos y de la dimensión de entrada. Esto permite, por ejemplo, cambiar de la dimensión “contratos” a la dimensión “clientes”.

También se puede utilizar esta actividad para definir las columnas adicionales del nuevo destino.

Es posible definir criterios de deduplicación de datos.

## Modo de configuración {#configuration-mode}

Para configurar la actividad de la dimensión de cambio, siga los pasos siguientes:

1. Seleccione la nueva dimensión de destino mediante el campo **[!UICONTROL Change dimension]**.

   ![](assets/s_user_change_dimension_param1.png)

1. Durante el cambio de dimensión, se pueden mantener todos los elementos o seleccionar los que desea conservar en la salida. En el ejemplo siguiente, el número máximo de duplicados se establece en 2.

   ![](assets/s_user_change_dimension_limit.png)

   Cuando decide mantener un solo registro, se muestra una colección en el esquema de trabajo: Esta colección representa todos los registros que no van a ser objetivo en el resultado final (ya que solo se guarda un registro). Al igual que todas las demás colecciones, este permite calcular las agregaciones o recuperar información en columnas.

   Por ejemplo: si se cambia la dimensión **[!UICONTROL Customers]** a la dimensión **[!UICONTROL Recipients]**, es posible dirigirse a los clientes de un almacén específico, al mismo tiempo que se añade el número de compras realizadas.

1. Si elige no conservar toda esta información, puede configurar el modo de gestión del duplicado.

   ![](assets/s_user_change_dimension_param2.png)

   Las flechas azules permiten definir la prioridad de procesamiento duplicada.

   En el ejemplo anterior, los destinatarios se deduplicarán en su dirección de correo electrónico primero, luego, si es necesario, en su número de cuenta.

1. La pestaña **[!UICONTROL Result]** permite añadir información adicional.

   Por ejemplo, se puede recuperar el municipio en función del código postal utilizando una función de tipo **Substring**. Para ello:

   * Haga clic en el vínculo **[!UICONTROL Add data...]** y seleccione **[!UICONTROL Data linked to the filtering dimension]**.

      ![](assets/wf_change-dimension_sample_01.png)

      >[!NOTE]
      >
      >Para obtener más información sobre la creación y administración de columnas adicionales, consulte [Adición de datos](../../workflow/using/query.md#adding-data).

   * Seleccione la dimensión de segmentación anterior (antes del cambio de eje) y, en el subárbol **[!UICONTROL Zip Code]** del destinatario, seleccione **[!UICONTROL Location]** y haga clic en **[!UICONTROL Edit expression]**.

      ![](assets/wf_change-dimension_sample_02.png)

   * Haga clic en **[!UICONTROL Advanced selection]** y elija **[!UICONTROL Edit the formula using an expression]**.

      ![](assets/wf_change-dimension_sample_03.png)

   * Utilice las funciones ofrecidas en la lista y especifique el cálculo que se va a realizar.

      ![](assets/wf_change-dimension_sample_04.png)

   * Finalmente, introduzca la etiqueta de la columna que acaba de crear.

      ![](assets/wf_change-dimension_sample_05.png)

1. Ejecute el flujo de trabajo para ver el resultado de esta configuración. Compare los datos de las tablas antes y después de la actividad de dimensión cambiante y compare la estructura de las tablas de flujo de trabajo, como se muestra en los ejemplos siguientes:

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)

