---
solution: Campaign Classic
product: campaign
title: Ciclo de vida de datos
description: Obtenga más información sobre el ciclo de vida de los datos en flujos de trabajo
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '509'
ht-degree: 100%

---


# Ciclo de vida de datos {#data-life-cycle}

## Tabla de trabajo {#work-table}

En los flujos de trabajo, los datos que pasan de una actividad a otra se almacenan en una tabla de trabajo temporal.

Estos datos se pueden mostrar y analizar haciendo clic con el botón derecho en la transición correspondiente.

![](assets/wf-right-click-analyze.png)

Para ello, seleccione el menú correspondiente:

* Visualización del público objetivo

   Este menú muestra los datos disponibles del público objetivo así como la estructura de la tabla de trabajo (la pestaña **[!UICONTROL Schema]**).

   ![](assets/wf-right-click-display.png)

   Para obtener más información, consulte [Esquema de tablas de trabajo y flujo de trabajo](../../workflow/using/monitoring-workflow-execution.md#worktables-and-workflow-schema).

* Análisis del público objetivo

   Este menú permite acceder al asistente de análisis descriptivo que permite producir las estadísticas y los informes sobre los datos de transición.

   Para obtener más información, consulte [esta sección](../../reporting/using/using-the-descriptive-analysis-wizard.md).

Los datos del público objetivo se depuran mientras se ejecuta el flujo de trabajo. Solo se puede acceder a la última tabla de trabajo. Puede configurar el flujo de trabajo para que todas las tablas de trabajo permanezcan accesibles: marque la opción **[!UICONTROL Keep the result of interim populations between two executions]** en las propiedades del flujo de trabajo.

Sin embargo, recomendamos que evite activar esta opción en caso de cantidades importantes de datos.

![](assets/wf-purge-data-option.png)

## Datos de destino {#target-data}

Los datos almacenados en la tabla de trabajo del flujo de trabajo están accesibles en los campos personalizados.

Esto permite utilizar datos recopilados mediante una lista o basados en las respuestas a una encuesta en una entrega. Para ello, utilice la siguiente sintaxis:

```
%= targetData.FIELD %
```

Los elementos personalizados de tipo **[!UICONTROL Target extension]** (targetData) no están disponibles para flujos de trabajo de objetivos. El objetivo de la entrega debe generarse en el flujo de trabajo y especificarse en la transición entrante de la entrega.

Si desea crear pruebas de entrega, el objetivo de la prueba debe crearse en función del modo **[!UICONTROL Address substitution]** para poder introducir los datos personalizados. Para obtener más información, consulte [esta sección](../../delivery/using/steps-defining-the-target-population.md#using-address-substitution-in-proof).

En el siguiente ejemplo, recopilamos una lista de información sobre los clientes para utilizar en un correo electrónico personalizado.

Siga estos pasos:

1. Cree un flujo de trabajo para recopilar información, reconciliarla con los datos que ya se encuentran en la base de datos y, a continuación, iniciar una entrega.

   ![](assets/wf-targetdata-sample-1.png)

   En nuestro ejemplo, el contenido del archivo es el siguiente:

   ```
   Music,First name,Last name,Account,CD/DVD,Card
   Pop,David,BLAIR,4323,CD,0
   Rock,Daniel,ARCARI,3222,DVD,1
   Disco,Uma,ALTON,0488,DVD,0
   Jazz,Paul,BOLES,6475,CD,1
   Jazz,David,BOUKHARI,0841,DVD,1
   [...]
   ```

   Para cargar el archivo, siga los siguientes pasos:

   ![](assets/wf-targetdata-sample-2.png)

1. Configure la actividad de tipo **[!UICONTROL Enrichment]** para reconciliar los datos recopilados con la base de datos de Adobe Campaign.

   En este caso, la clave de la reconciliación es el número de cuenta:

   ![](assets/wf-targetdata-sample-3.png)

1. A continuación, configure el **[!UICONTROL Delivery]**: se crea en función de una plantilla y la transición entrante especifica los destinatarios.

   ![](assets/wf-targetdata-sample-4.png)

   >[!CAUTION]
   >
   >Solo se pueden utilizar datos contenidos en la transición para personalizar la entrega. Los campos personalizados de tipo **targetData** solo están disponibles para la población entrante de la actividad **[!UICONTROL Delivery]**.

1. En la plantilla de entrega, utilice los campos recopilados en el flujo de trabajo.

   Para ello, inserte los campos personalizados de tipo **[!UICONTROL Target extension]**.

   ![](assets/wf-targetdata-sample-5.png)

   Aquí, queremos insertar el género musical favorito del cliente y el tipo de medio (CD o DVD) como se indica en el archivo recopilado por el flujo de trabajo.

   Además, vamos a añadir un cupón para los titulares de la tarjeta de fidelidad. Por ejemplo, para los destinatarios para los que el valor “Tarjeta” sea igual a 1.

   ![](assets/wf-targetdata-sample-6.png)

   El tipo de datos **[!UICONTROL Target extension]** (targetData) se inserta en las entregas utilizando las mismas características que en todos los campos personalizados. También pueden utilizarse en el asunto, en las etiquetas de los vínculos o en los propios vínculos.

   Los mensajes dirigidos a los destinatarios recopilados contienen los datos siguientes:

   ![](assets/wf-targetdata-sample-7.png)
