---
product: campaign
title: Optimización del envío de mensajes
description: Aprenda a optimizar la entrega de mensajes
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Deliverability
role: User
hide: true
exl-id: 24b2ee47-bec7-43ce-81b3-0b2d1a5cebae
TQID: https://experienceleague.adobe.com/XiK0I9mZTlGWACRL-TTdDO5pByzBg-6oFdfcTNfhX44
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: b4dd41a7-ccf8-4e9d-918e-acaab534a307
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 758
ht-degree: 100%

---

# Optimización de las entregas {#optimize-delivery}

Antes de empezar a crear envíos, puede realizar varias acciones para proteger y optimizar el proceso de envío de forma ascendente.

En la siguiente sección se describen las prácticas recomendadas y los procedimientos recomendados para una configuración óptima de Adobe Campaign. Si sigue estas prácticas, se minimizarán los problemas que podría tener que afrontar en la fase posterior.

## Rendimiento de la plataforma

Varios factores pueden afectar directamente al rendimiento del servidor y ralentizar la plataforma:

* Número y tipo de elementos de personalización: la personalización en correos electrónicos extrae datos de la base de datos para cada destinatario. Si hay muchos elementos de personalización, esto aumenta la cantidad de datos necesarios para preparar la entrega.  Obtenga más información sobre personalización en [esta sección](about-personalization.md)

* Carga del servidor: Cuando el servidor de marketing gestiona muchas tareas diferentes al mismo tiempo, puede ralentizar el rendimiento. El servidor de marketing debe coordinar todos los datos entrantes y salientes de todos los envíos para garantizar que los datos sean correctos y oportunos.

  **SUGERENCIA:** Para evitar esto, coordine la programación de las envíos con los demás miembros de su equipo para garantizar el mejor rendimiento.

* Ejecución del flujo de trabajo: La monitorización de sus flujos de trabajo es esencial para evitar problemas de rendimiento de la plataforma. Siga las directrices enumeradas [en este documento](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* Como cliente elegible, puede impulsar las [funciones del Panel de control de Campaign](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=es) para monitorizar su plataforma mediante funciones de [monitorización del rendimiento](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/about-performance-monitoring.html?lang=es).

## Comprobar configuración de red {#network-config}

Para optimizar el envío al administrar correos electrónicos en grandes volúmenes y evitar que se confunda con spam, asegúrese de tener una configuración de red legítima que no intente ocultar la identidad del servidor.

**Sugerencia**: Utilice una dirección de remitente transparente correspondiente al sitio web de la marca. Por ejemplo, la compañía TravelAgency gestiona la cadena hotelera Valentino. Dispone de su propio dominio valentino.com para su sitio web. Para promocionar el hotel Valentino en París, utiliza el subdominio paris.valentino.com. Por lo tanto, una dirección de remitente relevante puede ser hotel@paris.valentino.com.

## Administración de la capacidad de entrega {#deliverability-management}

Para llegar a la bandeja de entrada de sus destinatarios sin rebotar ni ser marcado como correo no deseado, debe mejorar la capacidad de envío de sus mensajes.

* ¿Qué es la capacidad de envío?

   * Hace referencia a los factores de un mensaje de correo electrónico que determinan su capacidad para ser aceptado por el servidor de un destinatario. Los ISP (proveedores de servicios de Internet) filtran los correos electrónicos que se identifican como SPAM o bloquean la descarga de imágenes. Si determinan que cierto dominio está enviando demasiados correos electrónicos, establecerán un límite en el número de correos electrónicos que aceptarán de ese remitente.

   * Al comprobar la tasa de envíos de sus correos electrónicos, debe centrarse en cuatro categorías principales: calidad de los datos, mensaje y contenido, infraestructuras de envío y reputación. Para profundizar en este tema, consulte [esta sección](about-deliverability.md).

* Aplique las recomendaciones detalladas [en este documento](about-deliverability.md).

* Póngase en contacto con su representante de Adobe para obtener ayuda.

## Administración de cuarentena {#quarantine-management}

Le conviene mantener buenos procesos de gestión de cuarentenas.

Al comenzar a enviar correos electrónicos en una nueva plataforma, puede utilizar una lista de direcciones que no esté totalmente confirmada. Si realiza envíos a direcciones no válidas o a direcciones honeypot (bandejas de entrada creadas únicamente para engañar a remitentes de correo electrónico no deseado), la reputación de su plataforma comenzará a reducirse. Unos procesos de administración de cuarentena adecuados ayudan a mantener la calidad de la dirección, evitar la lista de bloqueados de los proveedores de acceso a internet, y reducir la tasa de errores para acelerar los envíos y el rendimiento.

**Sugerencias**

* Si tiene una lista de direcciones no válidas, Adobe recomienda importarlas a la tabla de cuarentenas, a través de **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* Los destinatarios cuyas direcciones están en cuarentena se excluyen de forma predeterminada durante el análisis de envío: no están segmentados. Esto acelera las entregas, ya que la tasa de error afecta significativamente a la velocidad de entrega. Una dirección de correo electrónico se puede poner en cuarentena, por ejemplo, cuando el buzón está lleno o si la dirección no existe. [Más información](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign administra las direcciones erróneas según el tipo de error devuelto. Para obtener más información, consulte [esta sección](delivery-failures-quarantine.md).


* Algunos proveedores de acceso a Internet consideran automáticamente los correos electrónicos como no deseados si la tasa de direcciones no válidas es demasiado alta. Por lo tanto, la cuarentena le permite evitar ser incluido en la lista de bloqueados de bloqueados por estos proveedores.

* Además, la gestión de cuarentenas ayuda a reducir el coste de envío de SMS mediante la exclusión en los envíos de los números de teléfono incorrectos.

## Mecanismo de inclusión doble {#double-opt-in}

Para evitar el envío de mensajes a direcciones no válidas, limitar las comunicaciones incorrectas y mejorar la reputación del remitente, Adobe recomienda implementar un mecanismo de inclusión doble para la confirmación posterior a la suscripción. Esto ayuda a garantizar la suscripción intencionada de un destinatario.

Los detalles para la implementación de este mecanismo se describen en [esta sección](../../web/using/use-cases-web-forms.md).
