---
solution: Campaign Classic
product: campaign
title: Introducción al seguimiento
description: Obtenga más información sobre las directrices generales para el seguimiento en Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 55cc09c0446e389029890e45b790bb5ec6ffdc27
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 24%

---


# Introducción al seguimiento de mensajes {#get-started-tracking}

Gracias a sus funciones de seguimiento, Adobe Campaign le permite realizar un seguimiento adicional de los mensajes enviados y comprobar el comportamiento de los destinatarios: abrir, clics en vínculos, bajas, etc.

Esta información se recupera en la pestaña **[!UICONTROL Tracking]** del perfil de cada destinatario de la entrega. Esta pestaña presenta todos los vínculos de URL rastreados y seleccionados por el destinatario seleccionado de la lista. Esta es la acumulación de todas las direcciones URL rastreadas en las entregas que aún están presentes en la pantalla de envío. La lista se puede configurar y normalmente contiene: la dirección URL donde se hizo clic, la fecha y la hora del clic y el documento en el que se encontró la URL. Para obtener más información, consulte [esta sección](../../platform/using/editing-a-profile.md#tracking-tab).

El **panel de envío** también es clave para monitorear sus envíos y posibles problemas encontrados durante el envío de mensajes. Para obtener más información, consulte [esta sección](../../delivery/using/delivery-dashboard.md).

El siguiente diagrama muestra las etapas del diálogo entre el usuario y los distintos servidores.

![](assets/tracking-diagram.png)

## Configurar el seguimiento {#configure-tracking}

<img src="assets/do-not-localize/icon-configure.svg" width="60px">

**Principio de funcionamiento**

Antes de usar el seguimiento, primero debe configurarlo para su instancia. [Obtenga más información](../../installation/using/deploying-an-instance.md#operating-principle)

**Servidor de seguimiento**

Para configurar el seguimiento, la instancia debe declararse y registrarse en los servidores de seguimiento. [Obtenga más información](../../installation/using/deploying-an-instance.md#tracking-server)

**Guardando seguimiento**

Una vez configurado el seguimiento y completadas las direcciones URL, se debe registrar el servidor de seguimiento. [Obtenga más información](../../installation/using/deploying-an-instance.md#tracking-configuration#saving-tracking)

## Seguimiento de mensajes {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**Vínculos seguidos**

Puede realizar un seguimiento de la recepción de mensajes y de la activación de los vínculos insertados en el contenido del mensaje para comprender mejor el comportamiento de los destinatarios. [Obtenga más información](../../delivery/using/how-to-configure-tracked-links.md)

**Seguimiento de URL**

Las opciones de seguimiento se pueden configurar activando o desactivando las direcciones URL rastreadas. [Obtenga más información](../../delivery/using/personalizing-url-tracking.md)

**Personalización de vínculos rastreados**

Las funciones de seguimiento de Campaign Classic le permiten agregar vínculos en correos electrónicos que se pueden personalizar y que admiten el seguimiento. [Obtenga más información](https://helpx.adobe.com/campaign/kb/tracking-personnalized-links.html)

**Registros de seguimiento**

El flujo de trabajo técnico de seguimiento recupera los datos de seguimiento una vez que se ha enviado el envío y se ha activado el seguimiento. Estos datos se encuentran en la ficha Seguimiento del envío. [Obtenga más información](../../delivery/using/accessing-the-tracking-logs.md)

**Seguimiento de pruebas**

Antes de enviar los mensajes con el seguimiento, puede probar el seguimiento en su página espejo, los registros de correo electrónico y los vínculos. [Obtenga más información](../../delivery/using/testing-tracking.md)

## Seguimiento de aplicaciones web {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**Seguimiento de una aplicación web**

También puede rastrear y medir visitas en páginas de Aplicación web con etiquetas de seguimiento. Esta funcionalidad se puede utilizar para todos los tipos de Aplicaciones web, como formularios y encuestas en línea. [Obtenga más información](../../web/using/tracking-a-web-application.md)

**Exclusión del seguimiento de aplicaciones web**

La exclusión del seguimiento de Aplicaciones web le permite detener el seguimiento de los comportamientos web de los usuarios finales que desactivan el seguimiento de comportamiento. Puede incluir la capacidad de mostrar un letrero en aplicaciones web o páginas de aterrizaje para permitir que los usuarios puedan excluirse. [Obtenga más información](../../web/using/web-application-tracking-opt-out.md)

## Seguimiento de informes {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**Estadísticas de seguimiento**

Este informe proporciona estadísticas sobre aperturas, clics y transacciones, y le permite rastrear el impacto del envío en la mercadotecnia. [Obtenga más información](../../reporting/using/delivery-reports.md#tracking-statistics)

**URL y flujos de clics**

Este informe muestra la lista de páginas visitadas después de una entrega. [Obtenga más información](../../reporting/using/delivery-reports.md#urls-and-click-streams)

**Personas y destinatarios**

Comprender mejor la diferencia de seguimiento entre una persona o personas y un destinatario en Adobe Campaign con este ejemplo. [Obtenga más información](../../reporting/using/person-people-recipients.md)

**Indicadores de seguimiento**

Este informe combina los indicadores clave para rastrear el comportamiento de los destinatarios al recibir el envío, tales como las tasas de pulsaciones abiertas y los flujos de clics. [Obtenga más información](../../reporting/using/delivery-reports.md#tracking-indicators)

**Cálculo de indicador**

Las distintas tablas proporcionan la lista de los indicadores utilizados en los distintos informes y su fórmula de cálculo en función del tipo de envío. [Obtenga más información](../../reporting/using/indicator-calculation.md)

## Seguimiento de la solución de problemas {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

Las siguientes sugerencias de solución de problemas le ayudarán a resolver los problemas más comunes que se producen al utilizar el seguimiento en Adobe Campaign Classic. Para obtener información sobre la solución de problemas más avanzada, consulte [esta sección](../../delivery/using/tracking-troubleshooting.md).

* Compruebe que el proceso trackinglogd se está ejecutando

   Este proceso lee la memoria compartida de IIS/servidor Web y escribe los registros de redirección.

   Puede acceder a ella desde la página principal seleccionando la ficha Supervisión en la instancia. También puede ejecutar el siguiente comando en la instancia: `<user>@<instance>:~$ nlserver pdump`

   Si el proceso trackinglogd no aparece en la lista, inícielo con el siguiente comando en la instancia: `<user>@<instance>:~$ nlserver start trackinglogd`

* Compruebe que el flujo de trabajo técnico de seguimiento se ha estado ejecutando recientemente.

   Puede localizar el flujo de trabajo técnico de seguimiento en las carpetas Administración > Producción > Flujos de trabajo técnicos.
