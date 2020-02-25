---
title: Informes globales
seo-title: Informes globales
description: Informes globales
seo-description: null
page-status-flag: never-activated
uuid: 83ea834e-08f7-441b-8f15-a25ec07c4aab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
discoiquuid: cc832666-ad18-49ce-afcc-f9169b683ae8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 18309c190c351cc57f7af24f48b2a772c1840319

---


# Informes globales {#global-reports}

Estos informes hacen referencia a la actividad de los datos de toda la base de datos. To view the reports dashboard, go to the **[!UICONTROL Reports]** tab.

![](assets/s_ncs_user_report_delivery_link.png)

Para mostrar los informes, haga clic en el nombre de cada uno. Los siguientes informes están disponibles de forma predeterminada:

![](assets/s_ncs_user_report_global_list.png)

>[!NOTE]
>
>Esta sección muestra solamente los informes vinculados a los envíos.

* **[!UICONTROL Delivery throughput]** :: consulte Rendimiento [de envío](#delivery-throughput).
* **[!UICONTROL Browsers]** :: consulte [Exploradores](#browsers).
* **[!UICONTROL Sharing to social networks]** :: consulte [Uso compartido en redes](#sharing-to-social-networks)sociales.
* **[!UICONTROL Statistics on sharing activities]** :: consulte [Estadísticas sobre actividades](#statistics-on-sharing-activities)de uso compartido.
* **[!UICONTROL Operating systems]** :: consulte Sistemas [operativos](#operating-systems).
* **[!UICONTROL URLs and click streams]** :: consulte [Direcciones URL y flujos](../../reporting/using/delivery-reports.md#urls-and-click-streams)de clics.
* **[!UICONTROL Tracking indicators]** :: consulte [Seguimiento de indicadores](../../reporting/using/delivery-reports.md#tracking-indicators).
* **[!UICONTROL Non-deliverables and bounces]** :: consulte [No entregables y devoluciones](#non-deliverables-and-bounces).
* **[!UICONTROL User activities]** :: consulte Actividades [de usuario](#user-activities).
* **[!UICONTROL Subscription tracking]** :: consulte Seguimiento [de suscripciones](#subscription-tracking).
* **[!UICONTROL Delivery summary]** :: consulte Resumen [de](../../reporting/using/delivery-reports.md#delivery-summary)envío.
* **[!UICONTROL Delivery statistics]** :: consulte las estadísticas [de envío](#delivery-statistics).
* **[!UICONTROL Breakdown of opens]** :: consulte [Desglose de aperturas](#breakdown-of-opens).

## Rendimiento de envío {#delivery-throughput}

Este informe contiene información sobre el rendimiento de envío de toda la plataforma durante un periodo determinado. Para medir la velocidad a la que se envían los mensajes, los criterios son la cantidad de mensajes enviados por hora y el tamaño de los mensajes (en bits por segundo). En el siguiente ejemplo, el primer gráfico muestra los envíos correctos en azul y la cantidad de envíos incorrectos en naranja.

![](assets/s_ncs_user_report_toolbar.png)

Puede configurar los valores mostrados cambiando la escala temporal: Vista de 1 hora, vista de 3 horas, vista de 24 horas, etc. Haga clic en **[!UICONTROL Refresh]** para confirmar la selección.

## Actividades del usuario {#user-activities}

Este informe muestra el desglose de aperturas, clics y transacciones por media hora, hora o día, en forma de gráfico.

![](assets/s_ncs_user_user_report.png)

Estas son las opciones disponibles:

* **[!UICONTROL Opens]** : Número total de mensajes abiertos. No se tienen en cuenta los correos electrónicos en formato de texto. For more information on tracking opens, refer to [Tracking opens](../../reporting/using/indicator-calculation.md#tracking-opens-).
* **[!UICONTROL Clicks]** : Número total de clics en los vínculos de los envíos. No se tienen en cuenta los clics en los vínculos de baja de suscripción ni en las páginas espejo.
* **[!UICONTROL Transactions]** : Número total de transacciones después de recibir un mensaje. Para que se pueda tener en cuenta una transacción, debe insertarse una etiqueta de seguimiento web de tipo de transacción en la página web correspondiente. La configuración de seguimiento web se muestra en [esta sección](../../configuration/using/about-web-tracking.md).

## Rechazos y no entregables {#non-deliverables-and-bounces}

Este informe muestra el desglose de no entregables, así como un desglose de rechazos por dominio de Internet.

The **[!UICONTROL Number of messages processed]** represents the total number of messages processed by the delivery server. Este valor es inferior al número de mensajes que se desea enviar cuando se han detenido o pausado algunos envíos (antes de que el servidor los procese).

![](assets/s_ncs_user_errors_report.png)

**[!UICONTROL Breakdown of errors by type]**

>[!NOTE]
>
>Los errores que se muestran en este informe activan el proceso de cuarentena. Para obtener más información sobre la administración de la cuarentena, consulte [Administración de cuarentena](../../delivery/using/understanding-quarantine-management.md).

La primera sección de este informe muestra el desglose de no entregables en forma de tabla de valores y de gráfico.

Para cada tipo de error, se cuenta con:

* el número de mensajes de error de este tipo,
* el porcentaje de mensajes con errores de este tipo comparado con el número total de mensajes con errores,
* el porcentaje de mensajes de error de este tipo comparado con el número total de mensajes procesados.

Se utilizan los siguientes indicadores:

* **[!UICONTROL User unknown]** : Tipo de error generado durante el envío para indicar que la dirección de correo electrónico no es válida.
* **[!UICONTROL Invalid domain]** : Tipo de error generado al realizar un envío para indicar que el dominio de la dirección de correo electrónico es incorrecto o no existe.
* **[!UICONTROL Inbox full]** : Tipo de error generado después de cinco intentos de envío para indicar que la bandeja de entrada de los destinatarios contiene demasiados mensajes.
* **[!UICONTROL Account disabled]** : Tipo de error generado al realizar un envío para indicar que la dirección ya no existe.
* **[!UICONTROL Rejected]** : Tipo de error generado cuando el IAP (Proveedor de acceso a Internet) rechaza una dirección, por ejemplo, al aplicar una regla de seguridad (software contra correo no deseado).
* **[!UICONTROL Unreachable]** :: Tipo de error que se produce en la cadena de distribución de mensajes: incidente en el relé SMTP, dominio temporalmente inaccesible, etc.
* **[!UICONTROL Not connected]** : Tipo de error que indica que el teléfono móvil de los destinatarios está apagado o desconectado de la red en el momento del envío.

   >[!NOTE]
   >
   >Este indicador solo incluye los envíos de canales móviles. Para obtener más información, consulte [esta sección](../../delivery/using/sms-channel.md).

   You can open up each line of the value table by clicking the `[+]` symbol. Para cada tipo de error, se puede mostrar el desglose de mensajes de error por dominio.

   ![](assets/s_ncs_user_errors_report_detail.png)

**[!UICONTROL Breakdown of errors per domain]**

La segunda sección de este informe muestra el desglose de errores por dominio de Internet en forma de tabla de valores y de un gráfico.

Para cada nombre de dominio, se muestra:

* el número de mensajes con errores para este dominio,
* el porcentaje de mensajes con errores para este dominio comparado con el número total de mensajes procesados para este dominio,
* el porcentaje de mensajes de error para este dominio comparado con el número total de mensajes de error.

You can open up each line of the value table by clicking the [+] symbol. Para cada tipo de dominio, se puede mostrar el desglose de mensajes de error por tipo de error.

![](assets/s_ncs_user_errors_report_detail2.png)

>[!NOTE]
>
>Los nombres de dominio mostrados en este informe se definen al nivel de cubo. Para cambiar estos valores, edite el **[!UICONTROL Delivery logs (broadlogrcp)]** cubo. Para obtener más información, consulte [esta sección](../../reporting/using/about-cubes.md). The **[!UICONTROL Others]** category includes domain names that don&#39;t belong to a specific class.

## Navegadores {#browsers}

Este informe muestra el desglose de los navegadores de Internet que utilizan los destinatarios del envío durante el periodo correspondiente.

>[!NOTE]
>
>Los valores que se muestran en este informe son estimaciones: solo se tienen en cuenta los destinatarios que han hecho clic en un envío.

**Estadísticas globales**

Las estadísticas globales de uso del navegador se presentan en forma de una tabla de valores y de un gráfico.

![](assets/dlv_explorers_report.png)

Se utilizan los siguientes indicadores:

* **[!UICONTROL Visitors]** : Número total de destinatarios objetivo (por navegador de Internet) y que han hecho clic en un envío al menos una vez.
* **[!UICONTROL Pages viewed]** : Número total de clics en los vínculos de un envío (por navegador de Internet) para todos los envíos.
* **[!UICONTROL Usage rate]** : Esta tasa representa el desglose de los visitantes (por navegador de Internet) en relación con la cantidad total de visitantes.

**Estadísticas por navegador**

En la tabla de valores de estadísticas globales, se puede hacer clic en el nombre de cada navegador para ver sus estadísticas de uso.

![](assets/s_ncs_user_explorers_report2.png)

Las estadísticas se presentan en forma de una curva, un gráfico y una tabla de valores.

The **[!UICONTROL History]** curve represents the attendance rate of this browser per day. La tasa es la relación entre la cantidad de visitantes por día (en este navegador) comparada con el número de visitantes medidos en el día con la tasa de asistencia más alta.

The **[!UICONTROL Breakdown per version]** chart represents the breakdown of visitors per version compared to the total number of visitors (on this browser).

La tabla de valores utiliza los indicadores siguientes:

* **[!UICONTROL Global rate]** : Esta tasa representa el desglose de visitantes por versión comparado con la cantidad total de visitantes (en todos los navegadores).
* **[!UICONTROL Relative rate]** : Esta tasa representa el desglose de visitantes por versión comparado con la cantidad total de visitantes (en este navegador).

### Difusión en redes sociales {#sharing-to-social-networks}

El marketing viral permite que los destinatarios de los envíos compartan información con sus redes de contactos: pueden añadir un vínculo a su perfil (Facebook, Twitter, etc.) o enviar un mensaje a un amigo. Cada difusión y cada acceso a la información compartida se rastrea dentro del envío. Para obtener más información sobre marketing viral, consulte [esta sección](../../delivery/using/viral-and-social-marketing.md).

Este informe muestra el desglose de mensajes compartidos y abiertos por red social (Facebook, Twitter, etc.) y por correo electrónico.

![](assets/s_ncs_user_social_report.png)

**[!UICONTROL Email delivery statistics]**

En las estadísticas de envío de correo electrónico se muestran dos valores:

* **[!UICONTROL Number of messages to be delivered]** : Número total de mensajes procesados durante el análisis de envío.
* **[!UICONTROL Number of successful deliveries]** : Número de mensajes procesados correctamente.

**[!UICONTROL Sharing activities and mail open statistics]**

La tabla central muestra las estadísticas de correos electrónicos compartidos y abiertos.

In the **[!UICONTROL Shares]** column, we have the following indicators:

* **[!UICONTROL No. of sharing activities]** : Número total de mensajes compartidos en cada red social. This value equals the total number of clicks on the icon of the matching **[!UICONTROL Links for sharing to social networks]** personalization block.
* **[!UICONTROL Breakdown]** : Esta tasa representa el desglose de difusiones por red social en relación con el número total de difusiones.
* **[!UICONTROL Sharing rate]** : Esta tasa representa el desglose de difusiones por red social, en relación con el número de mensajes que se desea enviar.

In the **[!UICONTROL Opens]** column, we have the following indicators:

* **[!UICONTROL No. of opens]** :: Número total de mensajes abiertos por personas a las que se reenvió el mensaje (mediante el bloque de **[!UICONTROL Links for sharing to social networks]** personalización). Este valor equivale al número de veces que se mostró la página espejo. No se tienen en cuenta las aperturas de los destinatarios del envío.
* **[!UICONTROL Breakdown]** : Esta tasa representa el desglose de las aperturas por red social en relación con el número total de aperturas.
* **[!UICONTROL Rate of opens]** : Esta tasa representa el desglose de las aperturas por red social en relación con el número total de difusiones.

**[!UICONTROL Breakdown of sharing activities and opens]**

Esta sección incluye dos gráficos que representan el desglose de actividades de difusión y de aperturas por red social.

## Estadísticas de actividades de difusión {#statistics-on-sharing-activities}

Este informe muestra la evolución de las difusiones en redes sociales (Facebook, Twitter, correo electrónico, etc.) en el tiempo.

Para obtener más información sobre marketing viral, consulte [esta sección](../../delivery/using/viral-and-social-marketing.md).

![](assets/s_ncs_user_social_report2.png)

Las estadísticas se presentan en forma de una tabla de valores y de un gráfico.

Se utilizan los siguientes indicadores:

* **[!UICONTROL New contacts]** : Número de nuevas suscripciones tras la recepción de un mensaje compartido por correo electrónico. This value matches the number of people who received a message shared via email, clicked the **[!UICONTROL Subscription link]** and filled in the subscription form.
* **[!UICONTROL Opens]** :: Número total de mensajes abiertos por personas a las que se transfirió el mensaje (a través del bloque de **[!UICONTROL Link for sharing to social networks]** personalización). Este valor equivale al número de veces que se mostró la página espejo. No se tienen en cuenta las aperturas de los destinatarios del envío.
* **[!UICONTROL Sharing activities]** : Número total de mensajes compartidos a través de redes sociales. This value matches the total number of clicks on the icon of the **[!UICONTROL Links for sharing to social networks]** personalization block.

## Sistemas operativos {#operating-systems}

Este informe muestra el desglose de los sistemas operativos utilizados los destinatarios del envío durante el periodo correspondiente.

>[!NOTE]
>
>Los valores que se muestran en este informe son estimaciones: solo se tienen en cuenta los destinatarios que han hecho clic en un envío.

**Estadísticas globales**

Las estadísticas de uso global de los sistemas operativos se presentan en forma de una tabla de valores y de un gráfico.

![](assets/s_ncs_user_os_report.png)

Se utilizan los siguientes indicadores:

* **[!UICONTROL Visitors]** : Promedio diario del número total de destinatarios objetivo (por sistema operativo) que hicieron clic en un envío al menos una vez.
* **[!UICONTROL Pages viewed]** : Promedio diario del número total de clics en los vínculos de envío (por sistema operativo) para todos los envíos.
* **[!UICONTROL Rate of use]** : Esta tasa representa el desglose de visitantes (por sistema operativo) en relación con el número total de visitantes.

**Estadísticas por sistema operativo**

En la tabla de valores de estadísticas globales, haga clic en el nombre de cada sistema operativo para ver las estadísticas por sistema operativo.

![](assets/s_ncs_user_os_report2.png)

Las estadísticas se presentan en forma de una curva, un gráfico y una tabla de valores.

The **[!UICONTROL History]** curve represents the rate of use of this operating system per day. Esta tasa es la relación entre el número de visitantes por día (en este sistema operativo) en relación con el número de visitantes medidos en el día con la mayor asistencia.

The **[!UICONTROL Breakdown by version]** chart represents the breakdown of visitors per version in relation to the total number of visitors on this operating system.

La tabla de valores utiliza los indicadores siguientes:

* **[!UICONTROL Global rate]** : Esta tasa representa el desglose de visitantes (por versión) en relación con la cantidad total de visitantes a través de los sistemas operativos.
* **[!UICONTROL Relative rate]** : Esta tasa representa el desglose de visitantes (por versión) en relación con la cantidad total de visitantes para este sistema operativo.

## Seguimiento de suscripciones {#subscription-tracking}

Este informe permite monitorizar las suscripciones a los servicios de información. Muestra las suscripciones y bajas de suscripción.

![](assets/s_ncs_user_services_report.png)

It can be displayed for a subscription by clicking the **[!UICONTROL Profiles and targets > Services and subscriptions]** node of the home page or the explorer. Select the desired subscription, and then click the **[!UICONTROL Reports]** tab. El **[!UICONTROL Subscriptions tracking]** informe está disponible de forma predeterminada. Permite ver las tendencias de suscripción y de bajas de suscripción y la tasa de fidelidad durante un periodo. Se puede configurar la representación de estos datos a través de la lista desplegable. Click **[!UICONTROL Refresh]** to validate the selected configuration.

Para obtener más información, consulte [esta página](../../delivery/using/managing-subscriptions.md).

The **[!UICONTROL Number subscribed to date]** represents the total number of people currently subscribed.

**[!UICONTROL Overall evolution of subscriptions]**

La tabla de valores utiliza los indicadores siguientes:

* **[!UICONTROL Subscribers]** : Número total de suscriptores durante el periodo correspondiente.
* **[!UICONTROL Subscriptions]** : Número de suscripciones durante el periodo correspondiente.
* **[!UICONTROL Unsubscriptions]** : Número de bajas de suscripción durante el periodo correspondiente.
* **[!UICONTROL Evolution]** : Número de bajas de suscripción menos el número de suscripciones. La tasa se calcula en función del número total de suscriptores.
* **[!UICONTROL Loyalty]** : Tasa de fidelidad de los suscriptores durante el periodo correspondiente.

**[!UICONTROL Subscription evolution curves]**

Este gráfico muestra la evolución de las suscripciones y las bajas de suscripción durante el periodo correspondiente.

## Estadísticas de envío {#delivery-statistics}

Este informe muestra el desglose por dominio de Internet, de todos los mensajes procesados y enviados, de los rechazos graves o leves, aperturas, clics y bajas de suscripción.

![](assets/s_ncs_user_broadcast_report.png)

Se utilizan los siguientes indicadores:

* **[!UICONTROL Emails processed]** : Número total de mensajes que procesa el servidor de envío.
* **[!UICONTROL Delivered]** :: porcentaje del número de mensajes procesados correctamente en comparación con el número total de mensajes procesados.
* **[!UICONTROL Hard bounces]** :: porcentaje del número de devoluciones &quot;duras&quot; en comparación con el número total de mensajes procesados.
* **[!UICONTROL Soft bounces]** :: porcentaje del número de devoluciones &quot;en blanco&quot; en comparación con el número total de mensajes procesados.

   >[!NOTE]
   >
   >Para obtener más información sobre los rechazos graves y leves, consulte [Administración de cuarentena](../../delivery/using/understanding-quarantine-management.md).

* **[!UICONTROL Opens]** : porcentaje del número de destinatarios objetivo que abrieron un mensaje al menos una vez comparado con el número de mensajes procesados correctamente.
* **[!UICONTROL Clicks]** : porcentaje del número de personas que hizo clic en un envío al menos una vez comparado con el número de mensajes procesados correctamente.
* **[!UICONTROL Unsubscription]** :: porcentaje del número de clics en un vínculo de cancelación de suscripción en comparación con el número de mensajes procesados correctamente.

## Desglose de aperturas {#breakdown-of-opens}

Este informe muestra el desglose de aperturas por sistema operativo, dispositivo y navegador durante el periodo correspondiente. Para cada categoría se utilizan dos gráficos. El primero muestra estadísticas relacionadas con las aperturas en un ordenador y en dispositivos móviles. El segundo muestra estadísticas relacionadas únicamente con las aperturas en dispositivos móviles.

El número de aperturas corresponde al número total de mensajes abiertos. No se cuentan los correos electrónicos de formato de texto. For more information on Tracking opens, refer to the [Tracking opens](../../reporting/using/indicator-calculation.md#tracking-opens-) section.

![](assets/dlv_useragent_report.png)

>[!NOTE]
>
>Los nombres de navegador y sistema operativo forman parte de la información que envía el agente de usuario del navegador en el que se ha abierto el correo electrónico. Adobe Campaign deduce el tipo de dispositivo mediante la información del dispositivo.