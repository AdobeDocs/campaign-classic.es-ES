---
title: Acceso a la información de las entregas
seo-title: Acceso a la información de las entregas
description: Acceso a la información de las entregas
seo-description: null
page-status-flag: never-activated
uuid: dc8f0267-1884-4a39-9a7d-d5ef21932928
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: d2631c67-7781-4baa-b24e-e7921353d131
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 631e29bd6e59b8ae46084dee3a1d470916a2032b
workflow-type: ht
source-wordcount: '421'
ht-degree: 100%

---


# Acceso a la información de las entregas{#accessing-deliveries-information}

## Acceso a la lista de envíos {#accessing-the-list-of-deliveries}

Para acceder a la lista de envíos, vaya al entorno de **[!UICONTROL Campaigns]** y haga clic en el vínculo **[!UICONTROL Deliveries]**.

Si se utiliza [la vista del explorador](../../platform/using/adobe-campaign-workspace.md#about-adobe-campaign-explorer), se puede acceder a todas las entregas a través del nodo **[!UICONTROL Campaign management > Deliveries]** del árbol.

>[!NOTE]
>
>El espacio de trabajo de Adobe Campaign se muestra en [esta sección](../../platform/using/adobe-campaign-workspace.md).

Esta página permite acceder a una vista general de las entregas: muestra todas las entregas de la base de datos. Se puede ver su estado, su tasa de éxito y las fechas de modificación.

![](assets/d_ncs_user_filter_interface_delivery01.png)

>[!NOTE]
>
>El filtrado de información se muestra en [esta sección](../../platform/using/filtering-options.md).

El asistente de envío permite configurar las entregas, iniciar el proceso de aprobación y enviarlos. El contenido del asistente depende del canal de comunicación (correo electrónico, móvil, push, correo postal) y de los derechos de los operadores.

Para manipular las entregas en la lista, haga clic en una entrega. Se abre en una ventana nueva donde puede confirmar su envío o pausarlo, por ejemplo.

![](assets/s_ncs_user_interface_delivery02.png)

Dependiendo del escenario del ciclo de envío, los principales estados posibles son:

* Cancelado
* Error
* Pendiente
* Finalizado
* En pausa
* Reintento pendiente
* En curso
* Listo para distribución
* Preparación en curso
* Cálculo del destino
* Edición en curso

Cada estado tiene su propio color y etiqueta.

![](assets/s_ncs_user_status_campaigns_120.png)

La lista desplegable junto al botón **[!UICONTROL Create]** permite filtrar las entregas según su estado.

![](assets/delivery_filter_status.png)

## Acceso al calendario de envíos {#accessing-the-delivery-calendar}

Para acceder al calendario de envíos, vaya al entorno **[!UICONTROL Campaign]** y haga clic en el vínculo **[!UICONTROL Campaign calendar]**. Este calendario muestra el desglose de las campañas a lo largo del tiempo. Se puede personalizar la pantalla por mes, semana o día.

![](assets/s_ncs_user_interface_delivery04.png)

Haga clic en el nombre de una entrega para visualizar la información principal sobre el mismo. También puede abrir la campaña en caso necesario haciendo clic en **[!UICONTROL Open]**.

![](assets/s_ncs_user_interface_delivery05.png)

## Acceso a la información de rendimiento de las entregas {#accessing-deliveries-throughput-information}

La información de la página **[!UICONTROL Delivery throughput]** afecta a todas las entregas de la plataforma. Para medir la velocidad a la que se envían los mensajes, los criterios son la cantidad de mensajes enviados por hora y el tamaño de los mensajes (en bits por segundo). En el siguiente ejemplo, el primer gráfico muestra las entregas correctas en azul y la cantidad de entregas incorrectas en naranja.

Puede elegir el periodo en el que se calcula el rendimiento. Para esto, seleccione el valor de la lista desplegable y haga clic en **[!UICONTROL Refresh]**.

![](assets/s_ncs_user_interface_delivery06.png)

>[!NOTE]
>
>En el caso de instalaciones alojadas o híbridas, si ha actualizado al MTA mejorado, la página **[!UICONTROL Delivery throughput]** ya no mostrará el rendimiento a los destinatarios de correo electrónico. Muestra la velocidad de rendimiento para el reenvío de sus mensajes desde Campaign hasta el MTA mejorado.
>
>Para obtener más información sobre el MTA mejorado de Adobe Campaign, consulte este [documento](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html).