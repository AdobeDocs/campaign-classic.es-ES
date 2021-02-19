---
solution: Campaign Classic
product: campaign
title: Consulta de información de entrega
description: Obtenga información sobre cómo consultar la información de entrega.
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 100%

---


# Consulta de información de entrega {#querying-delivery-information}

## Número de clics de una entrega específica {#number-of-clicks-for-a-specific-delivery}

En este ejemplo, se busca recuperar el número de clics de una entrega específica. Estos clics se registran gracias a los registros de seguimiento de destinatarios realizados durante un periodo determinado. El destinatario se identifica mediante su dirección de correo electrónico. Esta consulta utiliza la tabla **[!UICONTROL Recipient tracking logs]**.

* ¿Qué tabla se debe seleccionar?

   La tabla de seguimiento del registro de destinatario (**[!UICONTROL nms:trackingLogRcp]**).

* ¿Campos que se desea seleccionar para las columnas de salida?

   Clave principal (con recuento) y correo electrónico

* ¿En función de qué criterios se filtra la información?

   Un periodo específico y un elemento de la etiqueta de entrega.

Para llevar a cabo este ejemplo, aplique los siguientes pasos:

1. Abra el **[!UICONTROL Generic query editor]** y seleccione el esquema **[!UICONTROL Recipient tracking logs]**.

   ![](assets/query_editor_tracklog_05.png)

1. En la ventana **[!UICONTROL Data to extract]**, se desea crear un acumulado para recopilar información. Para ello, añada la clave primaria (ubicada encima del elemento **[!UICONTROL Recipient tracking logs]** principal): el recuento de registros de seguimiento se realiza en este campo **[!UICONTROL Primary key]**. La expresión editada es **[!UICONTROL x=count(primary key)]**. Vincula la suma de diversos registros de seguimiento a una sola dirección de correo electrónico.

   Para ello:

   * A la derecha del campo **[!UICONTROL Add]**, haga clic en el icono **[!UICONTROL Output columns]**. En la ventana **[!UICONTROL Formula type]**, seleccione la opción **[!UICONTROL Edit the formula using an expression]** haciendo clic en **[!UICONTROL Next]**. En la ventana **[!UICONTROL Field to select]**, haga clic en **[!UICONTROL Advanced selection]**.

      ![](assets/query_editor_tracklog_06.png)

   * En la ventana **[!UICONTROL Formula type]**, ejecute un proceso en la función de acumulado. Este proceso es un recuento de clave principal.

      Seleccione **[!UICONTROL Process on an aggregate function]** en la sección **[!UICONTROL Aggregate]** y haga clic en **[!UICONTROL Count]**.

      ![](assets/query_editor_nveau_18.png)

      Haga clic en **[!UICONTROL Next]**.

   * Seleccione el campo **[!UICONTROL Primary key (@id)]**. Se configura la columna de salida **[!UICONTROL count (primary key)]**.

      ![](assets/query_editor_nveau_19.png)

1. Seleccione el otro campo que se desea mostrar en la columna de salida. En la columna **[!UICONTROL Available fields]**, abra el nodo **[!UICONTROL Recipient]** y elija **[!UICONTROL Email]**. Marque la casilla **[!UICONTROL Group]** en **[!UICONTROL Yes]** para agrupar los registros de seguimiento por dirección de correo electrónico: este grupo relaciona cada registro con su destinatario.

   ![](assets/query_editor_nveau_20.png)

1. Configure la ordenación de columnas para que se muestren primero los destinatarios más activos (con la mayoría de registros de seguimiento). Marque **[!UICONTROL Yes]** en la columna **[!UICONTROL Descending sort]**.

   ![](assets/query_editor_nveau_64.png)

1. A continuación, se debe filtrar los registros de interés, es decir, aquellos que tengan menos de 2 semanas y que impliquen envíos relacionados con ventas.

   Para ello:

   * Configure el filtrado de datos. Para ello, seleccione **[!UICONTROL Filter conditions]** y haga clic en **[!UICONTROL Next]**.

      ![](assets/query_editor_nveau_22.png)

   * Recupere los registros de seguimiento durante un periodo determinado para una entrega específica. Se necesitan tres condiciones de filtrado: dos condiciones de fecha para establecer el periodo de búsqueda entre 2 semanas antes de la fecha actual y el día antes de la fecha actual; y otra condición para restringir la búsqueda a una entrega específica.

      En la ventana **[!UICONTROL Target element]**, configure la fecha empezando desde la cual se deben tomar en cuenta los registros de seguimiento. Haga clic en **[!UICONTROL Add]**. Se muestra una línea de condición. Edite la columna **[!UICONTROL Expression]** haciendo clic en la función **[!UICONTROL Edit expression]**. En la ventana **[!UICONTROL Field to select]**, elija **[!UICONTROL Date (@logDate)]**.

      ![](assets/query_editor_nveau_23.png)

      Seleccione el operador **[!UICONTROL greater than]**. En la columna **[!UICONTROL Value]**, haga clic en **[!UICONTROL Edit expression]** y, en la ventana **[!UICONTROL Formula type]**, seleccione **[!UICONTROL Process on dates]**. Finalmente, en **[!UICONTROL Current date minus n days]**, escriba &quot;15&quot;.

      Haga clic en **[!UICONTROL Finish]**.

      ![](assets/query_editor_nveau_24.png)

   * Para seleccionar la fecha de finalización de la búsqueda del registro de seguimiento, cree una segunda condición haciendo clic en **[!UICONTROL Add]**. En la columna **[!UICONTROL Expression]**, elija **[!UICONTROL Date (@logDate)]** nuevamente.

      Seleccione el operador **[!UICONTROL less than]**. En la columna **[!UICONTROL Value]**, haga clic en **[!UICONTROL Edit expression]**. Para el procesamiento de fechas, vaya a la ventana **[!UICONTROL Formula type]** y escriba “1” en **[!UICONTROL Current date minus n days]**.

      Haga clic en **[!UICONTROL Finish]**.

      ![](assets/query_editor_nveau_65.png)

      Ahora, se desea configurar la tercera condición de filtro; es decir, la etiqueta de envío que abarca la consulta.

   * Haga clic en la función **[!UICONTROL Add]** para crear otra condición de filtrado. En la columna **[!UICONTROL Expression]**, haga clic en **[!UICONTROL Edit expression]**. En la ventana **[!UICONTROL Field to select]**, elija **[!UICONTROL Label]** en el nodo **[!UICONTROL Delivery]**.

      Haga clic en **[!UICONTROL Finish]**.

      ![](assets/query_editor_nveau_66.png)

      Busque una entrega que contenga la palabra “ventas”. Como no recuerda su etiqueta exacta, puede elegir el operador **[!UICONTROL contains]** e introducir “sales” en la columna **[!UICONTROL Value]**.

      ![](assets/query_editor_nveau_25.png)

1. Haga clic en **[!UICONTROL Next]** hasta que llegue a la ventana **[!UICONTROL Data preview]**: no se requiere formato alguno.
1. En la ventana **[!UICONTROL Data preview]**, haga clic en **[!UICONTROL Start the preview of the data]** para ver el número de registros de seguimiento para cada destinatario de la entrega.

   El resultado se muestra en orden descendente.

   ![](assets/query_editor_tracklog_04.png)

   El número mayor de registros para un usuario es 6 para esta entrega. Cinco usuarios diferentes han abierto el correo electrónico de entrega o han hecho clic en uno de los vínculos del mismo.

## Destinatarios que no han abierto ninguna entrega {#recipients-who-did-not-open-any-delivery}

En este ejemplo, se desea filtrar los destinatarios que no hayan abierto un correo electrónico en los últimos 7 días.

Para crear este ejemplo, aplique los pasos siguientes:

1. Arrastre y suelte una actividad **[!UICONTROL Query]** en un flujo de trabajo y ábrala.
1. Haga clic en **[!UICONTROL Edit query]** y configure las dimensiones de objetivo y filtrado en **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Seleccione **[!UICONTROL Filtering conditions]**, luego haga clic en **[!UICONTROL Next]**.
1. Haga clic en el botón **[!UICONTROL Add]** y seleccione **[!UICONTROL Tracking logs]**.
1. Defina el **[!UICONTROL Operator]** de la expresión **[!UICONTROL Tracking logs]** en **[!UICONTROL Do not exist such as]**.

   ![](assets/query_open_1.png)

1. Agregue otra expresión. Seleccione **[!UICONTROL Type]** en la categoría **[!UICONTROL URL]**.
1. A continuación, configure su **[!UICONTROL Operator]** en **[!UICONTROL equal to]** y su **[!UICONTROL Value]** en **[!UICONTROL Open]**.

   ![](assets/query_open_2.png)

1. Añada otra expresión y seleccione **[!UICONTROL Date]**. **[!UICONTROL Operator]** se debe configurar en **[!UICONTROL on or after]**.

   ![](assets/query_open_3.png)

1. Para configurar el valor los últimos 7 días, haga clic en el botón **[!UICONTROL Edit expression]** del campo **[!UICONTROL Value]**.
1. En la categoría **[!UICONTROL Function]**, seleccione **[!UICONTROL Current date minus n days]** y añada el número de días que desee establecer como objetivo. En este caso, se busca fijar como objetivo los últimos 7 días.

   ![](assets/query_open_4.png)

La transición saliente contiene destinatarios que no han abierto un correo electrónico en los últimos 7 días.

Si, por el contrario, se desea filtrar los destinatarios que hayan abierto al menos un correo electrónico, la consulta debe ser la siguiente: Tenga en cuenta que, en este caso, **[!UICONTROL Filtering dimension]** se debe configurar en **[!UICONTROL Tracking logs (Recipients)]**.

![](assets/query_open_5.png)

## Destinatarios que han abierto una entrega {#recipients-who-have-opened-a-delivery}

El ejemplo siguiente muestra cómo dirigirse a perfiles que han abierto una entrega en las últimas 2 semanas:

1. Para segmentar perfiles que hayan abierto una entrega, debe utilizar los registros de seguimiento. se almacenan en una tabla relacionada: comience seleccionando esta tabla en la lista desplegable del campo **[!UICONTROL Filtering dimension]**, como se muestra a continuación:

   ![](assets/s_advuser_query_sample1.0.png)

1. Con respecto a las condiciones de filtrado, haga clic en el icono **[!UICONTROL Edit expression]** de los criterios que se muestran en la estructura de sub-árbol de los registros de seguimiento. Seleccione el campo **[!UICONTROL Date]**.

   ![](assets/s_advuser_query_sample1.1.png)

   Haga clic en **[!UICONTROL Finish]** para confirmar la selección.

   Para recuperar únicamente los registros de seguimiento con menos de dos semanas, seleccione el operador **[!UICONTROL Greater than]**.

   ![](assets/s_advuser_query_sample1.4.png)

   A continuación, haga clic en el icono **[!UICONTROL Edit expression]** de la columna **[!UICONTROL Value]** para definir la fórmula de cálculo que se desea aplicar. Seleccione la fórmula **[!UICONTROL Current date minus n days]** y escriba 15 en el campo relacionado.

   ![](assets/s_advuser_query_sample1.5.png)

   Haga clic en el botón **[!UICONTROL Finish]** de la ventana de la fórmula. En la ventana de filtrado, haga clic en la pestaña **[!UICONTROL Preview]** para comprobar los criterios de objetivo.

   ![](assets/s_advuser_query_sample1.6.png)

## Filtrado del comportamiento de los destinatarios después de una entrega {#filtering-recipients--behavior-folllowing-a-delivery}

En un flujo de trabajo, las casillas **[!UICONTROL Query]** y **[!UICONTROL Split]** permiten seleccionar un comportamiento después de una entrega previa. Esta selección se realiza mediante el filtro **[!UICONTROL Delivery recipient]**.

* Objetivo del ejemplo

   En un flujo de trabajo de entrega, hay varias formas de realizar seguimiento a una primera comunicación por correo electrónico. Este tipo de operación implica el uso de la casilla **[!UICONTROL Split]**.

* Contexto

   Se envía una “Oferta de deportes de verano”. Cuatro días después de la entrega, se realizan otras dos entregas. Uno de ellos es “Oferta de deportes acuáticos”, el otro es un seguimiento de la primera entrega “Oferta de deportes de verano”.

   La entrega “Oferta de deportes acuáticos” se realiza a los destinatarios que han hecho clic en el vínculo “Deportes acuáticos” en la primera entrega. Estos clics muestran que el destinatario está interesado en el tema. Esto tiene sentido para dirigirlos a ofertas similares. Sin embargo, los destinatarios que no hayan hecho clic en “Oferta de deportes de verano” reciben el mismo contenido nuevamente.

Los siguientes pasos muestran cómo configurar la casilla **[!UICONTROL Split]** integrando dos comportamientos diferentes:

1. Inserte la casilla **[!UICONTROL Split]** en el flujo de trabajo. Esta casilla desglosa los destinatarios de la primera entrega en los dos envíos siguientes. El desglose se produce en función de las condiciones de filtrado vinculadas al comportamiento del destinatario durante la primera entrega.

   ![](assets/query_editor_ex_09.png)

1. Abra la casilla **[!UICONTROL Split]**. En la pestaña **[!UICONTROL General]**, introduzca una etiqueta: **Split based on behavior**, por ejemplo.

   ![](assets/query_editor_ex_04.png)

1. En la pestaña **[!UICONTROL Subsets]**, defina la primera rama de división. Por ejemplo, introduzca la etiqueta en los que se ha hecho **clic** para esta rama.
1. Seleccione la opción **[!UICONTROL Add a filtering condition on the incoming population]**. Haga clic en **[!UICONTROL Edit]**.
1. En la ventana **[!UICONTROL Targeting and filtering dimension]**, haga doble clic en el filtro **[!UICONTROL Recipients of a delivery]**.

   ![](assets/query_editor_ex_05.png)

1. En la ventana **[!UICONTROL Target element]**, seleccione el comportamiento que desee aplicar a esta rama: **[!UICONTROL Recipients having clicked (email)]**.

   A continuación, seleccione la opción **[!UICONTROL Delivery specified by the transition]**. Esta funcionalidad recupera automáticamente a los destinatarios segmentados durante la primera entrega.

   Este es la entrega “Oferta de deportes acuáticos”.

   ![](assets/query_editor_ex_08.png)

1. Defina la segunda rama. Esta rama incluye el correo electrónico de seguimiento con el mismo contenido que para la primera entrega. Vaya a la pestaña **[!UICONTROL Subsets]** y haga clic en **[!UICONTROL Add]** para crearlo.

   ![](assets/query_editor_ex_06.png)

1. Se muestra otra subpestaña. Denomínela “**No han hecho clic**”.
1. Haga clic en **[!UICONTROL Add a filtering condition for the incoming population]**. A continuación, haga clic en **[!UICONTROL Edit...]**.

   ![](assets/query_editor_ex_07.png)

1. Haga clic **[!UICONTROL Delivery recipients]** en la **[!UICONTROL Targeting and filtering dimension]** ventana.
1. En la ventana **[!UICONTROL Target element]**, seleccione el comportamiento **[!UICONTROL Recipients who did not click (email)]**. Seleccione la opción **[!UICONTROL Delivery specified by the transition]** como se muestra para la última rama.

   La casilla **[!UICONTROL Split]** ahora está totalmente configurada.

   ![](assets/query_editor_ex_03.png)

A continuación, se muestra la lista de los distintos componentes configurados de forma predeterminada:

* **[!UICONTROL All recipients]**
* **[!UICONTROL Recipients of successfully sent messages,]**
* **[!UICONTROL Recipients who opened or clicked (email),]**
* **[!UICONTROL Recipients who clicked (email),]**
* **[!UICONTROL Recipients of a failed message,]**
* **[!UICONTROL Recipients who didn't open or click (email),]**
* **[!UICONTROL Recipients who didn't click (email).]**

   ![](assets/query_editor_ex_02.png)
