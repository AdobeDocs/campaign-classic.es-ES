---
solution: Campaign Classic
product: campaign
title: Acerca de la capacidad de envío en Campaign
description: Conozca las prácticas recomendadas sobre la capacidad de entrega
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
translation-type: tm+mt
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 12%

---

# ¿Qué es la capacidad de envío{#about-deliverability}?

La capacidad de entrega permite medir el éxito de las campañas que llegan a la bandeja de entrada de los destinatarios sin rebotar o marcadas como correo no deseado. [Descubra por qué la capacidad de envío importa](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters).

Más precisamente, la capacidad de envío de correo electrónico se refiere al conjunto de características que determinan la capacidad de un mensaje para llegar a su destino a través de una dirección de correo electrónico personal, en poco tiempo y con la calidad esperada en términos de contenido y formato.

Para profundizar en lo que es la capacidad de envío y obtener más información sobre los términos, conceptos y enfoques clave de la capacidad de envío, consulte la [Guía de prácticas recomendadas de entrega de Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=es).

## Cómo mejorar la capacidad de envío {#deliverability-key-points}

Los problemas de entrega generalmente están vinculados a medidas de protección contra spam implementadas por los proveedores de servicios de Internet y los administradores de servidores de correo.

* Para obtener recomendaciones generales sobre cómo diseñar campañas de marketing por correo electrónico exitosas, consulte [Estrategia de entrega y definición](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html).

* Para obtener recomendaciones más específicas sobre cómo optimizar la entrega de los correos electrónicos de Adobe Campaign, Adobe recomienda utilizar las prácticas recomendadas que se enumeran en esta sección.

>[!NOTE]
>
>Debido a que los ISP están obligados a desarrollar continuamente nuevas técnicas sofisticadas de filtrado para proteger a sus clientes de los remitentes de spam, la capacidad de envío del correo electrónico se caracteriza por criterios y reglas que cambian constantemente. Asegúrese de consultar la [Guía de prácticas recomendadas de entrega de Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html), que se actualiza regularmente.

### Tasa de entrega

La tasa de entrega es el número de mensajes que llegan a las bandejas de entrada de los destinatarios en comparación con el número de mensajes que se entregaron. Para mejorar la capacidad de envío, puede aumentar esta tasa.

Con Adobe Campaign, la tasa de entrega depende de numerosos factores, especialmente:

* Configuración correcta de las instancias: póngase en contacto con su representante del Adobe para obtener ayuda.
* Configuración de red legítima: consulte [esta sección](../../delivery/using/optimize-delivery.md#network-config) y [Configuración y estrategia del dominio](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy).
* Su reputación de dirección IP: consulte [IP strategy](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy).
* Calidad de las direcciones objetivo: consulte [Administración de cuarentena](../../delivery/using/optimize-delivery.md#quarantine-management).
* Baja [quejas](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html) y [tasas de rechazo grave](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces).
* El contenido del mensaje: consulte [Control del contenido del correo electrónico](../../delivery/using/control-message-content.md).
* Autenticación de mensajes (SPF, DKIM, DMARC): consulte [esta sección](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).
* Conocimiento del remitente: para conocer cómo evalúan los principales ISP la reputación de un remitente, consulte [esta sección](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html).

## Herramientas de envío de campañas {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign proporciona varias herramientas para rastrear y mejorar el rendimiento de envío de su plataforma. Esta página también resalta los principios principales que debe tener en cuenta para optimizar la capacidad de envío al utilizar Campaign.

### Cree cuidadosamente su mensaje

Al configurar, diseñar y probar el mensaje, asegúrese de seguir las prácticas recomendadas que se mencionan en las secciones a continuación. El uso de todas las funciones que proporciona Adobe Campaign le ayuda a mejorar la capacidad de envío.

* [Prácticas recomendadas sobre entregas](../../delivery/using/delivery-best-practices.md)
* [Control del contenido del correo electrónico](../../delivery/using/control-message-content.md)
* [Renderización de la bandeja de entrada](../../delivery/using/inbox-rendering.md)
* [Envío de una prueba](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)

### Verifique el consentimiento mediante la doble adhesión {#double-opt-in}

Para evitar el envío de mensajes a direcciones no válidas, limitar las comunicaciones incorrectas y mejorar la reputación del remitente, Adobe recomienda implementar un mecanismo de inclusión doble. Este método le permite asegurarse de que sus destinatarios se hayan suscrito intencionadamente.

Para obtener más información sobre esto, consulte [Creación de un formulario de suscripción con doble adhesión](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).

Para obtener más información sobre las prácticas recomendadas al recopilar datos de sus clientes, consulte la [Guía de prácticas recomendadas de entrega de Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene).

### Aprovechar la administración de cuarentena

Adobe Campaign administra una lista que recopila quejas por correo no deseado, rechazos graves y rechazos leves que se producen de forma coherente.

Para proteger la capacidad de envío, los destinatarios cuyas direcciones están en esa lista se excluyen de forma predeterminada de todos los envíos futuros, ya que el envío a estos contactos podría dañar su reputación de envío.

Algunos proveedores de acceso a Internet consideran automáticamente los correos electrónicos como no deseados si la tasa de direcciones no válidas es demasiado alta. Por lo tanto, la cuarentena le permite evitar ser incluido en la lista de bloqueados de bloqueados por estos proveedores.

Para obtener más información, consulte las secciones siguientes:

* [Comprensión de los errores de entrega](../../delivery/using/understanding-delivery-failures.md)
* [Comprensión de la gestión de la cuarentena](../../delivery/using/understanding-quarantine-management.md)
* [Cuarentena frente a lista de bloqueados](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)

### Uso de herramientas de supervisión y creación de informes

Utilice las funciones que ofrece Adobe Campaign para supervisar la capacidad de envío.

Adobe Campaign le permite comprobar el rendimiento de sus envíos a través de un conjunto de indicadores e informes integrados en tiempo real para obtener una mejor perspectiva de sus envíos.

Para obtener más información, consulte las secciones siguientes:

* [Supervisión de la capacidad de entrega](../../delivery/using/monitoring-deliverability.md)
* [Acerca de la monitorización de entrega](../../delivery/using/about-delivery-monitoring.md)
* [Acerca de los informes integrados de Campaign](../../reporting/using/about-campaign-built-in-reports.md)

<!--TO REMOVE
## Background {#background}

Email deliverability presents a major challenge to marketers - whether they're sending a few thousand messages or several billion. One in five messages never reach the inbox, or their intended recipient.

Once relegated as a "technical issue" for the IT department, email deliverability continues to move higher on the marketing agenda. That's because savvy marketers recognize that although many of its elements are technical in nature, deliverability is ultimately a business issue with significant revenue implications.

Consider the email marketing funnel. Deliverability determines the number of messages received, which in turn impacts each subsequent stage of the funnel. Fewer emails received results in fewer opens, fewer clicks, and fewer conversions. **For companies with a large database, the difference between average and great deliverability could literally mean hundreds of thousands to millions of dollars in revenues.**

![](assets/deliverability_overview_1.png)

By settling for average (80%) deliverability, marketers are leaving significant conversions - and dollars - on the table.

What exactly is email deliverability? And how can marketers improve deliverability rates to widen the mouth of the funnel and squeeze more results from their email campaigns?

Email deliverability refers to the set of characteristics that determine a message's ability to reach its destination, via a personal e-mail address, within a short time, and with the expected quality in terms of content and format. These characteristics fall into four main categories: data quality, message and content, sending infrastructure, and reputation. Together, they form the foundation of a successful email deliverability program. This overview outlines the four fundamentals of email deliverability success and offers best practices for reaching the inbox and driving greater revenues from email marketing programs.

![](assets/deliverability_overview_2.png)-->
