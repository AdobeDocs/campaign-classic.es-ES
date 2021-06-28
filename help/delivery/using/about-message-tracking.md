---
product: campaign
title: Introducción al seguimiento
description: Obtenga más información sobre las directrices generales para el seguimiento en Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: ee3d643e4ba607b3d7ca816eabf862b867d1f3f4
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 97%

---

# Introducción al seguimiento de mensajes {#get-started-tracking}

Gracias a sus funciones de seguimiento, Adobe Campaign le permite realizar un seguimiento adicional de los mensajes enviados y comprobar el comportamiento de los destinatarios: aperturas de mensajes, clics en vínculos, bajas, etc.

Esta información se recupera en la pestaña **[!UICONTROL Tracking]** del perfil de cada destinatario de la entrega. Esta pestaña presenta todos los vínculos de URL rastreados y seleccionados por el destinatario seleccionado de la lista. Esta es la acumulación de todas las direcciones URL rastreadas en las entregas que aún están presentes en la pantalla de envío. La lista se puede configurar y normalmente contiene: la dirección URL donde se hizo clic, la fecha y la hora del clic y el documento en el que se encontró la URL. Para obtener más información, consulte [esta sección](../../platform/using/editing-a-profile.md#tracking-tab).

El **panel de envío** es fundamental para monitorizar los envíos y los problemas que se puedan detectar durante el envío de mensajes. Para obtener más información, consulte [esta sección](delivery-dashboard.md).

El siguiente diagrama muestra las etapas del diálogo entre el usuario y los distintos servidores.

![](assets/tracking-diagram.png)

## Configuración del seguimiento {#configure-tracking}

<img src="assets/do-not-localize/icon-configure.svg" width="60px">

**Principio de funcionamiento**

Antes de usar el seguimiento, primero debe configurarlo para su instancia. [Obtenga más información](../../installation/using/deploying-an-instance.md#operating-principle)

**Servidor de seguimiento**

Para configurar el seguimiento, la instancia debe declararse y registrarse en los servidores de seguimiento. [Obtenga más información](../../installation/using/deploying-an-instance.md#tracking-server)

**Guardado del seguimiento**

Una vez configurado el seguimiento y completadas las direcciones URL, se debe registrar el servidor de seguimiento. [Obtenga más información](../../installation/using/deploying-an-instance.md#saving-tracking)

## Seguimiento de mensajes {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**Vínculos seguidos**

Puede realizar un seguimiento de la recepción de mensajes y de la activación de los vínculos insertados en el contenido del mensaje para comprender mejor el comportamiento de los destinatarios. [Obtenga más información](how-to-configure-tracked-links.md)

**Seguimiento de URL**

Las opciones de seguimiento se pueden configurar activando o desactivando las direcciones URL rastreadas. [Obtenga más información](personalizing-url-tracking.md)

**Personalización de vínculos rastreados**

Las funciones de seguimiento de Campaign Classic le permiten añadir vínculos en correos electrónicos que se pueden personalizar y que admiten el seguimiento. [Obtenga más información](tracking-personalized-links.md)

**Registros de seguimiento**

El flujo de trabajo técnico de seguimiento recupera los datos de seguimiento una vez que se ha enviado el envío y se ha activado el seguimiento. Estos datos se encuentran en la pestaña Seguimiento del envío. [Obtenga más información](accessing-the-tracking-logs.md)

**Seguimiento de pruebas**

Antes de enviar los mensajes con el seguimiento, puede probar el seguimiento en su página espejo, los registros de correo electrónico y los vínculos. [Obtenga más información](testing-tracking.md)

## Seguimiento de aplicaciones web {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**Seguimiento de una aplicación web**

También puede rastrear y medir visitas en páginas de aplicación web con etiquetas de seguimiento. Esta funcionalidad se puede utilizar para todos los tipos de aplicaciones web, como formularios y páginas de aterrizaje. [Obtenga más información](../../web/using/tracking-a-web-application.md)

**Exclusión del seguimiento de aplicaciones web**

La exclusión del seguimiento de aplicaciones web le permite detener el seguimiento de los comportamientos web de los usuarios finales que excluyen el seguimiento de comportamiento. Puede incluir la capacidad de mostrar un banner en aplicaciones web o páginas de destino para permitir que los usuarios puedan excluirse. [Obtenga más información](../../web/using/web-application-tracking-opt-out.md)

## Seguimiento de informes {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**Estadísticas de seguimiento**

Este informe proporciona estadísticas sobre aperturas, clics y transacciones, y le permite rastrear el impacto del envío en marketing. [Obtenga más información](../../reporting/using/delivery-reports.md#tracking-statistics)

**URL y flujos de clics**

Este informe muestra la lista de páginas visitadas después de un envío. [Obtenga más información](../../reporting/using/delivery-reports.md#urls-and-click-streams)

**Personas y destinatarios**

Comprenda mejor la diferencia de seguimiento entre una persona o personas y un destinatario en Adobe Campaign con este ejemplo. [Obtenga más información](../../reporting/using/person-people-recipients.md)

**Indicadores de seguimiento**

Este informe combina los indicadores clave para rastrear el comportamiento de los destinatarios al recibir el envío, tales como las tasas de pulsaciones abiertas y los flujos de clics. [Obtenga más información](../../reporting/using/delivery-reports.md#tracking-indicators)

**Cálculo de indicador**

Las distintas tablas proporcionan la lista de los indicadores utilizados en los distintos informes y su fórmula de cálculo en función del tipo de envío. [Obtenga más información](../../reporting/using/indicator-calculation.md)

## Solución de problemas de seguimiento {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

Las siguientes sugerencias de solución de problemas le ayudarán a resolver los problemas más comunes que se producen al utilizar el seguimiento en Adobe Campaign Classic. Para obtener información sobre la solución de problemas más avanzada, consulte [esta sección](tracking-troubleshooting.md).

* Compruebe que el proceso trackinglogd se está ejecutando

   Este proceso lee la memoria compartida de IIS/servidor web y escribe los registros de redirección.

   Puede acceder a ella desde la página principal seleccionando la pestaña Supervisión en la instancia. También puede ejecutar el siguiente comando en la instancia: `<user>@<instance>:~$ nlserver pdump`

   Si el proceso trackinglogd no aparece en la lista, inícielo con el siguiente comando en la instancia: `<user>@<instance>:~$ nlserver start trackinglogd`

* Compruebe que el flujo de trabajo técnico de seguimiento se ha estado ejecutando recientemente.

   Puede localizar el flujo de trabajo técnico de seguimiento en las carpetas Administración > Producción > Flujos de trabajo técnicos.
