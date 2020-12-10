---
solution: Campaign Classic
product: campaign
title: Informes de entrega
description: Informes de entrega
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '1443'
ht-degree: 97%

---


# Informes de entrega {#delivery-reports}

Se puede realizar un seguimiento de la ejecución de los envíos a través de diversos informes accesibles desde la información general de entrega. Para visualizar informes, siga el siguiente procedimiento:

1. Vaya al entorno **[!UICONTROL Campaigns]** y haga clic en el vínculo **[!UICONTROL Delivery]** para mostrar la lista de envíos.
1. Haga clic en el nombre de la entrega que desee visualizar para mostrar sus detalles.

   ![](assets/s_ncs_user_detailled_report.png)

1. Seleccione la pestaña **[!UICONTROL Summary]** y haga clic en el vínculo **[!UICONTROL Reports]** para acceder a los informes específicos de la entrega.

   ![](assets/s_ncs_user_detailled_report2.png)

   De manera predeterminada, están disponibles los siguientes informes:

   * **[!UICONTROL Delivery throughput]**: consulte [Rendimiento de entrega](../../reporting/using/global-reports.md#delivery-throughput).
   * **[!UICONTROL Sharing to social networks]**: consulte [Uso compartido en redes sociales](../../reporting/using/global-reports.md#sharing-to-social-networks).
   * **[!UICONTROL Statistics on sharing activities]**: consulte [Estadísticas sobre actividades de uso compartido](../../reporting/using/global-reports.md#statistics-on-sharing-activities).
   * **[!UICONTROL Hot clicks]**: consulte [Clics activos](#hot-clicks).
   * **[!UICONTROL Tracking statistics]**: consulte las [Estadísticas de seguimiento](#tracking-statistics)
   * **[!UICONTROL URLs and click streams]**: consulte [Direcciones URL y flujos de clics](#urls-and-click-streams).
   * **[!UICONTROL Tracking indicators]**: consulte [Seguimiento de indicadores](#tracking-indicators).
   * **[!UICONTROL Non-deliverables and bounces]**: consulte [No entregables y devoluciones](../../reporting/using/global-reports.md#non-deliverables-and-bounces).
   * **[!UICONTROL User activities]**: consulte [Actividades de usuario](../../reporting/using/global-reports.md#user-activities).
   * **[!UICONTROL Delivery summary]**: consulte [Resumen de entregas](#delivery-summary).
   * **[!UICONTROL Subscription tracking]**: consulte [Seguimiento de suscripciones](../../reporting/using/global-reports.md#subscription-tracking).
   * **[!UICONTROL Delivery statistics]**: consulte las [Estadísticas de entrega](../../reporting/using/global-reports.md#delivery-statistics).
   * **[!UICONTROL Breakdown of opens]**: consulte [Desglose de aperturas](../../reporting/using/global-reports.md#breakdown-of-opens).

## Indicadores de seguimiento {#tracking-indicators}

Este informe combina los indicadores clave para realizar un seguimiento del comportamiento de los destinatarios al recibir la entrega. Permite el acceso a las estadísticas de entrega y recepción, las tasas de apertura y clics, los flujos de clics generados, el seguimiento web y las actividades de uso compartido en redes sociales.

>[!NOTE]
>
>Los valores calculados en función de los mensajes abiertos siempre son estimaciones, debido al margen de error vinculado a los correos electrónicos en formato de texto. Los indicadores **[!UICONTROL Distinct opens/Sum of opens for the population reached]** tienen en cuenta este margen de error. Para obtener más información sobre el seguimiento de las aperturas, consulte [Seguimiento de aperturas](../../reporting/using/indicator-calculation.md#tracking-opens-).

![](assets/s_ncs_user_tracking_synth_report.png)

**[!UICONTROL 1. Delivery statistics]**

* **[!UICONTROL Messages to deliver]** : Número total de mensajes que desea enviar después del análisis de envío.
* **[!UICONTROL Success]** : número de mensajes procesados correctamente.

**[!UICONTROL 2. Reception statistics]**

>[!NOTE]
>
>Los porcentajes relacionados se calculan según el número de mensajes reenviados correctamente.

* **[!UICONTROL Distinct opens for the population reached]** : Estimación del número de destinatarios objetivo que han abierto un mensaje al menos una vez. Se tienen en cuenta los clics en los vínculos de baja de suscripción y en las páginas espejo.
* **[!UICONTROL Sum of opens for the population reached]** : Estimación del número total de aperturas de los destinatarios objetivo.
* **[!UICONTROL Clicks on opt-out link]** : Número de clics en el vínculo de baja de suscripción.
* **[!UICONTROL Clicks on the mirror page link]** : Número de clics en el vínculo de página espejo. Para que se tenga en cuenta un vínculo, este debe definirse como tal en el asistente de envíos (direcciones URL rastreadas). Consulte [esta página](../../delivery/using/about-delivery-monitoring.md).
* **[!UICONTROL Estimation of forwards]** : Estimación del número de correos electrónicos reenviados por los destinatarios objetivo. Este valor se calcula restando el número de personas diferentes y el número de destinatarios diferentes que hicieron clic en el correo electrónico.

   >[!NOTE]
   >
   >Para obtener más información sobre la diferencia entre personas diferentes y destinatarios objetivo, consulte [Personas / destinatarios objetivo](../../reporting/using/indicator-calculation.md#targeted-persons---recipients).

**[!UICONTROL 3. Open and click-through rate]**

Esta tabla de valores muestra el desglose de envíos, aperturas, clics y reacciones sin procesar por dominio de Internet. Se utilizan los siguientes indicadores:

* **[!UICONTROL Sent]** : número total de mensajes enviados en este dominio.
* **[!UICONTROL Complaints]** : número de mensajes de este dominio que el destinatario ha notificado como no deseados. La tasa se calcula en función del número total de mensajes enviados en este dominio.
* **[!UICONTROL Opens]** : número de destinatarios objetivo diferentes para este dominio que han abierto un mensaje al menos una vez. La tasa se calcula en función del número total de mensajes enviados en este dominio.
* **[!UICONTROL Clicks]** : número de destinatarios objetivo diferentes que hicieron clic en el mismo entrega al menos una vez. La tasa se calcula en función del número total de mensajes enviados en este dominio
* **[!UICONTROL Raw reactivity]** : porcentaje del número de destinatarios que hicieron clic en una entrega al menos una vez comparado con el número de destinatarios que abrieron una entrega al menos una vez.

>[!NOTE]
>
>Los nombres de dominio mostrados en este informe se definen en la lista desglosada utilizada al nivel de cubo. Para cambiar, añadir o quitar dominios predeterminados, edite la lista desglosada **[!UICONTROL Domains]** y modifique los valores y alias. Para obtener más información, consulte [esta sección](../../platform/using/managing-enumerations.md). La categoría **[!UICONTROL Others]** incluye nombres de dominio que no pertenecen a ningún valor de la lista desglosada.

**[!UICONTROL 4. Generated click streams]**

>[!NOTE]
>
>Los porcentajes relacionados se calculan según el número de mensajes reenviados correctamente.

* **[!UICONTROL Distinct clicks for the population reached]** : Número de personas diferentes que han hecho clic en un envío al menos una vez.
* **[!UICONTROL Cumulated clicks]** : número total de clics de los destinatarios objetivo, sin contar los vínculos de baja de suscripción y las páginas espejo.
* **[!UICONTROL Recipient clicks]** : número de destinatarios objetivo diferentes que hicieron clic en el mismo entrega al menos una vez.
* **[!UICONTROL Estimated recipient reactivity]** : proporción del número de destinatarios que han hecho clic al menos una vez en una entrega en comparación con el número estimado de destinatarios que han abierto una entrega al menos una vez. No se tienen en cuenta los clics en los vínculos de exclusión ni de la página espejo.

**[!UICONTROL 5. Web tracking]**

* **[!UICONTROL Visited pages]** : Número de páginas web visitadas después de la recepción del mensaje.
* **[!UICONTROL Transactions]** : número de compras después de recibir el mensaje.
* **[!UICONTROL Total amount]** : Cantidad total de compras después de recibir el mensaje.
* **[!UICONTROL Average transaction amount]** : Compras medias realizadas por distintos destinatarios de envíos.
* **[!UICONTROL Articles]** : número de artículos adquiridos por los destinatarios de la entrega.
* **[!UICONTROL Average count of articles per transaction]** : Cantidad media de elementos por compra realizada por distintos destinatarios.
* **[!UICONTROL Average amount per message]** : Cantidad media de compras generadas por mensaje.

   >[!NOTE]
   >
   >Para que se tenga en cuenta la transacción, la cantidad, el artículo o la página visitada, debe insertarse una etiqueta de seguimiento web en la página web correspondiente. La configuración de seguimiento web se muestra en [esta sección](../../configuration/using/about-web-tracking.md).

**[!UICONTROL 6. Sharing activities to email and social networks]**

Esta sección muestra el número de mensajes compartidos en cada red social. Para obtener más información sobre esto, consulte [Compartir en redes sociales](../../reporting/using/global-reports.md#sharing-to-social-networks).

## URL y flujos de clics {#urls-and-click-streams}

Este informe muestra la lista de páginas visitadas después de una entrega.

![](assets/s_ncs_user_url_report.png)

Puede configurar el contenido de este informe seleccionando: el gráfico de puntuación que se va a mostrar, el filtro de tiempo (desde el inicio de la acción, durante las primeras 6 horas después del inicio, etc.) y el modo de visualización de datos (por etiqueta, por dirección URL, por categoría). Haga clic en **[!UICONTROL Refresh]** para confirmar la selección.

Las siguientes tasas se muestran en la sección superior del informe:

* **[!UICONTROL Reactivity]** : la proporción del número de destinatarios objetivo que han hecho clic en una entrega en relación con el número estimado de destinatarios objetivo que han abierto una entrega. No se tienen en cuenta los clics en el vínculo de exclusión ni de la página espejo.

   >[!NOTE]
   >
   >Para obtener más información sobre el seguimiento de las aperturas, consulte [Seguimiento de aperturas](../../reporting/using/indicator-calculation.md#tracking-opens-).

* **[!UICONTROL Distinct clicks]** : número de personas diferentes que han hecho clic al menos una vez (excepto en el vínculo de baja de suscripción y de la página espejo) en una entrega. La tasa mostrada se calcula según el número de mensajes enviados correctamente.
* **[!UICONTROL Cumulated clicks]** : número total de clics por destinatarios objetivo (excepto el vínculo de baja de suscripción y de la página espejo). La tasa mostrada se calcula según el número de mensajes reenviados correctamente.

**[!UICONTROL Platform average]** : la tasa promedio, mostrada debajo de cada tasa (reacción, distintos clics y clics acumulados), se calcula para los envíos realizados durante los seis meses anteriores. Solo se tienen en cuenta los envíos con la misma tipología y en el mismo canal. Se excluyen las pruebas.

La tabla central ofrece la siguiente información:

* **[!UICONTROL Clicks]** : número de clics acumulados, por vínculo.
* **[!UICONTROL Clicks (in %)]** : desglose del número de clics por vínculo en relación con la cantidad total de clics acumulados.

**[!UICONTROL Breakdown of clicks in time]**

Este gráfico muestra el desglose de los clics acumulados por día.

## Resumen de entregas {#delivery-summary}

Este informe proporciona toda la información principal sobre la entrega.

![](assets/s_ncs_user_synth_report.png)

**[!UICONTROL Target population]**

Esta sección tiene dos indicadores:

* **[!UICONTROL Initial population]** : Número total de destinatarios a quienes se realizó la entrega.
* **[!UICONTROL Messages rejected by the rule]** : número de direcciones ignoradas durante el análisis al aplicar las reglas de tipología: dirección no disponible, en cuarentena, en lista de bloqueados, etc. Para obtener más información sobre reglas de tipología, consulte esta [página](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).

**[!UICONTROL Causes of exclusion]**

El gráfico central muestra el desglose por regla de mensajes rechazados durante el análisis.

**[!UICONTROL Delivery statistics]**

Esta sección incluye los siguientes indicadores:

* **[!UICONTROL Messages to be delivered]** : Número total de mensajes que desea enviar después del análisis de envío.
* **[!UICONTROL Success]** : Número de mensajes procesados correctamente. La tasa asociada es la proporción respecto al número de mensajes que desea enviar.
* **[!UICONTROL Errors]** : Número total de errores acumulados durante los envíos y el procesamiento automático de los rechazos. La tasa asociada es la proporción respecto al número de mensajes que desea enviar.
* **[!UICONTROL New quarantines]** : Número de direcciones en cuarentena después de un envío fallido (usuario desconocido, dominio no válido). La tasa asociada es la proporción respecto al número de mensajes que desea enviar.

## Clics activos {#hot-clicks}

Este informe muestra el contenido del mensaje (HTML o texto) con el porcentaje de clics en los vínculos, por cada vínculo. Los bloques personalizados, los vínculos de cancelación de suscripción, los vínculos de páginas espejo y los vínculos de ofertas se tienen en cuenta en el total de clics acumulados, pero no se muestran en el informe.

>[!NOTE]
>
>Si la entrega contiene ofertas (interacción), aparece un cuadro en la parte superior del informe que muestra el porcentaje de clics en las ofertas.

![](assets/s_ncs_user_clic_report.png)

## Estadísticas de seguimiento {#tracking-statistics}

Este informe ofrece estadísticas sobre las aperturas, los clics y las transacciones.

![](assets/s_ncs_user_stat_report.png)

Permite realizar un seguimiento del impacto de marketing de la entrega. Se puede configurar el modo en que se muestran los valores cambiando la escala temporal (vista de 1 hora, de 3 horas, de 24 horas, etc.). Haga clic en **[!UICONTROL Refresh]** para confirmar la selección.

Este informe proporciona una tabla de valores y un gráfico de Pareto que muestra el tiempo necesario para que la entrega llegue a su máxima eficiencia. Se utilizan los siguientes indicadores:

* **[!UICONTROL Opens]** : Estimación del tiempo necesario para alcanzar un porcentaje del número total de mensajes abiertos. No se tienen en cuenta los correos electrónicos en formato de texto. Para obtener más información sobre el seguimiento de las aperturas, consulte [Seguimiento de aperturas](../../reporting/using/indicator-calculation.md#tracking-opens-).
* **[!UICONTROL Clicks]** : Estimación del tiempo necesario para alcanzar un porcentaje del número total de clics registrados. No se tienen en cuenta los clics en el vínculo de exclusión ni de la página espejo.
* **[!UICONTROL Transactions]** : Tiempo necesario para obtener un porcentaje del número total de transacciones después de la recepción del mensaje. Para que se pueda tener en cuenta una transacción, debe insertarse una etiqueta de seguimiento web de tipo de transacción en la página web correspondiente. La configuración de seguimiento web se muestra en [esta sección](../../configuration/using/about-web-tracking.md).
