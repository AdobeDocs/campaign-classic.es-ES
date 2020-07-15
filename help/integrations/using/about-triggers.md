---
title: Acerca de Adobe Experience Manager
seo-title: Acerca de Adobe Experience Manager
description: Acerca de Adobe Experience Manager
seo-description: null
page-status-flag: never-activated
uuid: c523822f-8178-4989-bd88-ab402470e540
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 0d617f1c-0d0b-489f-9027-a92b1f1eee37
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0112d5bd052ad66169225073276d1da4f3c245d8
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 3%

---


# Acerca de los activadores de Adobe Experience Cloud{#about-adobe-experience-triggers}

[!DNL Triggers] es una integración entre Adobe Campaign y Adobe Analytics que utiliza la canalización. La canalización recupera las acciones o activadores de los usuarios desde el sitio web. El abandono del carro de compras es un ejemplo de activador. Los activadores se procesan en Adobe Campaign para enviar correos electrónicos en tiempo casi real.

[!DNL Triggers] ejecutar acciones de marketing en un corto intervalo de tiempo tras la acción de un usuario. El tiempo de respuesta típico es inferior a una hora.

Permite integraciones más ágiles, ya que la configuración es mínima y un tercero no participa.
También admite grandes volúmenes de tráfico sin afectar el rendimiento de las actividades de marketing. Como ejemplo, la integración puede procesar un millón de activadores por hora.

## [!DNL Triggers] arquitectura {#triggers-architecture}

### ¿Qué es Pipeline? {#pipeline-explanation}

>[!CAUTION]
>
>Solo las soluciones de Adobe Cloud pueden producir y consumir eventos de los servicios de canalización de Adobe. Los sistemas externos a Adobe no pueden.

Pipeline es un sistema de mensajería alojado en el Experience Cloud que utiliza [Apache Kafka](http://kafka.apache.org/). Es una forma de pasar fácilmente datos entre soluciones. Además, Pipeline es una cola de mensajes en lugar de una base de datos. Los productores impulsan los eventos y los consumidores escuchan el flujo y hacen lo que quieren con el evento. Los Eventos se conservan durante unos días pero no más. El propósito es escuchar las 24 horas del día, los 7 días de la semana y procesar eventos inmediatamente.

![](assets/triggers_1.png)

### ¿Cómo funciona Pipeline? {#how-pipeline-work}

El [!DNL pipelined] proceso siempre se está ejecutando en el servidor de marketing de Adobe Campaign. Se conecta a la canalización, recupera los eventos y los procesa inmediatamente.

![](assets/triggers_2.png)

El [!DNL pipelined] proceso inicia sesión en el Experience Cloud mediante un servicio de autenticación y envía una clave privada. El servicio de autenticación devuelve un token. El token se utiliza para autenticarse al recuperar los eventos. [!DNL Triggers] se recuperan de un servicio web REST mediante una simple solicitud GET. La respuesta es formato JSON. Los parámetros de la solicitud incluyen el nombre del activador y un puntero que indica el último mensaje recuperado. El [!DNL pipelined] proceso lo gestiona automáticamente.

## Uso de la integración de Adobe Experience Cloud Triggers con Adobe Campaign Classic

Estas son algunas [!DNL Triggers] prácticas recomendadas:

* Los [!DNL Trigger] datos deben almacenarse a medida que llegan en Campaña. No debería procesarse directamente, ya que crearía latencia.
* La marca de tiempo debe comprobarse desde el mensaje y no desde la base de datos.
* Utilice TriggerTimestamp y el ID de activación para eliminar duplicados.

>[!CAUTION]
>
>El ejemplo siguiente no se proporciona de forma predeterminada. Este es un ejemplo específico de varias implementaciones posibles.

Los eventos de canalización se descargan automáticamente. Estos eventos se pueden supervisar mediante un formulario.

![](assets/triggers_3.png)

El nodo Evento de canalización no está integrado y debe agregarse, así como el formulario relacionado debe crearse en Campaña. Estas operaciones están restringidas únicamente a usuarios expertos. Para obtener más información sobre esto, consulte estas secciones: [Jerarquía](../../configuration/using/about-navigation-hierarchy.md) de navegación y [edición de formularios](../../configuration/using/editing-forms.md).

Un flujo de trabajo de campaña recurrente consulta en activadores y, si coinciden con los criterios de marketing, inicio un envío.

![](assets/triggers_4.png)
