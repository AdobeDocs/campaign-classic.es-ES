---
product: campaign
title: Introducción a la capacidad de entrega en Campaign
description: Conozca las prácticas recomendadas sobre la capacidad de entrega
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Deliverability
role: User
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '665'
ht-degree: 100%

---

# ¿Qué es la capacidad de entrega?{#about-deliverability}

La capacidad de entrega le permite medir el éxito de las campañas que llegan a la bandeja de entrada de los destinatarios sin rechazarse ni marcarse como correo no deseado. [Descubra por qué la capacidad de entrega es importante](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html?lang=es#why-deliverability-matters).

Más concretamente, la capacidad de entrega de correo electrónico hace referencia al conjunto de características que determinan la capacidad de un mensaje para llegar a su destino a través de una dirección de correo electrónico personal, en poco tiempo y con la calidad esperada en términos de contenido y formato.

Para profundizar en lo que es la capacidad de entrega y obtener más información sobre los términos, conceptos y enfoques clave de la capacidad de entrega, consulte la [Guía de prácticas recomendadas de entrega de Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=es).

## Cómo mejorar la capacidad de entrega {#deliverability-key-points}

Los problemas de entrega suelen estar vinculados a medidas de protección contra spam implementadas por los proveedores de servicios de Internet y los administradores de servidores de correo.

* Para obtener recomendaciones generales sobre cómo diseñar campañas de marketing por correo electrónico exitosas, consulte [Estrategia y definición de capacidad de entrega](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html?lang=es).

* Para obtener recomendaciones más específicas sobre cómo optimizar la entrega de los correos electrónicos de Adobe Campaign, Adobe recomienda implementar las prácticas recomendadas que se enumeran en esta sección.

>[!NOTE]
>
>Debido a que los proveedores de servicios de Internet están obligados a desarrollar continuamente nuevas técnicas sofisticadas de filtrado para proteger a sus clientes de los remitentes de spam, la capacidad de envío del correo electrónico se caracteriza por criterios y reglas que cambian constantemente. Asegúrese de consultar la [Guía de prácticas recomendadas de entrega de Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=es), que se actualiza regularmente.

### Tasa de entrega

La tasa de entregabilidad es el número de mensajes que llegan a las bandejas de entrada de los destinatarios en comparación con el número de mensajes que se entregaron. Para mejorar la capacidad de entrega, puede aumentar esta tasa.

Con Adobe Campaign, la tasa de entrega depende de numerosos factores, especialmente:

* Configuración correcta de las instancias: póngase en contacto con su representante de Adobe para obtener ayuda.
* Configuración de red legítima: consulte [esta sección](optimize-delivery.md#network-config) y [Configuración y estrategia del dominio](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=es#domain-setup-and-strategy).
* Su reputación de dirección IP: consulte [Estrategia de IP](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=es#ip-strategy).
* Calidad de las direcciones objetivo: consulte [Administración de cuarentena](optimize-delivery.md#quarantine-management).
* Tasas de [quejas](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html?lang=es) y [rechazos](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html?lang=es#hard-bounces) bajas.
* El contenido del mensaje: consulte [Control del contenido del correo electrónico](control-message-content.md).
* Autenticación de mensajes (SPF, DKIM, DMARC): consulte [esta sección](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=es#authentication).
* Reputación del remitente: para conocer cómo evalúan los principales ISP la reputación de un remitente, consulte [esta sección](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html?lang=es).

## Herramientas de entrega de campañas {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign proporciona varias herramientas para rastrear y mejorar el rendimiento de envío de su plataforma. Esta página también resalta los principios generales que debe tener en cuenta para optimizar la capacidad de envío al utilizar Campaign.

### Cree su mensaje de forma considerada

Al configurar, diseñar y probar el mensaje, asegúrese de seguir las prácticas recomendadas que se mencionan en las secciones a continuación. El uso de todas las funciones que proporciona Adobe Campaign le ayuda a mejorar la capacidad de envío.

* [Prácticas recomendadas de entregas](delivery-best-practices.md)
* [Control del contenido de correo electrónico](control-message-content.md)
* [Procesamiento de la bandeja de entrada](inbox-rendering.md)
* [Envío de una prueba](steps-validating-the-delivery.md#sending-a-proof)

### Verificación del consentimiento mediante la doble inclusión {#double-opt-in}

Para evitar el envío de mensajes a direcciones no válidas, limitar las comunicaciones incorrectas y mejorar la reputación del remitente, Adobe recomienda implementar un mecanismo de inclusión doble. Este método le permite asegurarse de que sus destinatarios se hayan suscrito intencionadamente.

Para obtener más información sobre esto, consulte [Creación de un formulario de suscripción con doble inclusión](../../web/using/use-cases-web-forms.md#create-a-subscription--form-with-double-opt-in).

Para obtener más información sobre las prácticas recomendadas al recopilar datos de sus clientes, consulte la [Guía de prácticas recomendadas de entrega de Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html?lang=es#data-quality-and-hygiene).

### Mejora de la administración de cuarentena

Adobe Campaign administra una lista que recopila quejas por correo no deseado, rechazos graves y rechazos leves que se producen de forma consistente.

Para proteger la capacidad de entrega, los destinatarios cuyas direcciones están en esa lista se excluyen de forma predeterminada de todas las entregas futuras, ya que la entrega a estos contactos podría dañar su reputación de entrega.

Algunos proveedores de acceso a Internet consideran automáticamente los correos electrónicos como no deseados si la tasa de direcciones no válidas es demasiado alta. Por lo tanto, la cuarentena le permite evitar ser incluido en la lista de bloqueados de bloqueados por estos proveedores.

Para obtener más información, consulte las siguientes secciones:

* [Comprensión de los errores de entrega](understanding-delivery-failures.md)
* [Comprensión de la administración de cuarentenas](understanding-quarantine-management.md)
* [Cuarentena frente a lista de bloqueados](understanding-quarantine-management.md#quarantine-vs-denylist)

### Uso de herramientas de supervisión y creación de informes

Utilice las funciones que ofrece Adobe Campaign para monitorizar su capacidad de entrega.

Adobe Campaign le permite comprobar el rendimiento de sus entregas a través de un conjunto de indicadores e informes integrados en tiempo real para obtener un mejor conocimiento de sus entregas.

Para obtener más información, consulte las siguientes secciones:

* [Monitorización de la capacidad de entrega](monitoring-deliverability.md)
* [Introducción a la monitorización de entregas](about-delivery-monitoring.md)
* [Introducción a los informes integrados de Campaign](../../reporting/using/about-campaign-built-in-reports.md)
