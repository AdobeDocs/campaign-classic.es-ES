---
title: Optimizar el envío de mensajes
seo-title: Optimizar el envío de mensajes
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 31%

---


# Optimización del envío {#optimize-delivery}

Antes de empezar a crear envíos, puede realizar varias acciones para proteger y optimizar el proceso de envío de forma ascendente.

En la siguiente sección se describen las prácticas recomendadas y los procedimientos recomendados para una configuración óptima de Adobe Campaign. Si sigue estas prácticas, se minimizarán los problemas que podría tener que afrontar en la fase posterior.

## Rendimiento de la plataforma

Varios factores pueden afectar directamente al rendimiento del servidor y ralentizar la plataforma:

* Número y tipo de elementos de personalización: la personalización en correos electrónicos extrae datos de la base de datos para cada destinatario. Si hay muchos elementos de personalización, esto aumenta la cantidad de datos necesarios para preparar la entrega.  Más información sobre personalización en [esta sección](../../delivery/using/about-personalization.md)

* Carga del servidor: cuando el servidor de mercadotecnia gestiona muchas tareas diferentes al mismo tiempo, puede ralentizar el rendimiento. El servidor de mercadotecnia debe coordinar todos los datos entrantes y salientes de todos los envíos para garantizar que los datos sean correctos y estén a tiempo.

   **SUGERENCIA** : Para evitar esto, coordine la programación de envíos con los demás miembros de su equipo para garantizar el mejor rendimiento.

* Ejecución del flujo de trabajo: la supervisión de sus flujos de trabajo es esencial para evitar problemas de rendimiento de la plataforma. Siga las directrices enumeradas [en este documento](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* Como cliente alojado, puede aprovechar las funciones [del panel de control de](https://docs.adobe.com/content/help/es-ES/control-panel/using/discover-control-panel/key-features.html) Campaña para supervisar su plataforma mediante funciones de supervisión [del](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/about-performance-monitoring.html) rendimiento.

## Comprobación de la configuración de red {#network-config}

Para optimizar el envío al administrar correos electrónicos en grandes volúmenes y evitar que se confunda con un spam, asegúrese de tener una configuración de red legítima que no intente ocultar la identidad del servidor.

**Sugerencia**:  Utilice una dirección de remitente transparente correspondiente al sitio web de la marca. Por ejemplo, la compañía TravelAgency gestiona la cadena hotelera Valentino. Dispone de su propio dominio valentino.com para su sitio web. Para promocionar el hotel Valentino en París, utiliza el subdominio paris.valentino.com. Por lo tanto, una dirección de remitente relevante puede ser hotel@paris.valentino.com.

## Administración de la capacidad de entrega {#deliverability-management}

Para llegar a la bandeja de entrada de sus destinatarios sin rebotar ni ser marcado como correo no deseado, debe mejorar la tasa de entrega de sus mensajes.

* ¿Qué es la capacidad de entrega?

   * Hace referencia a los factores de un mensaje de correo electrónico que determinan su capacidad para ser aceptado por el servidor de un destinatario. Los ISP (Proveedores de servicio de Internet) filtran los correos electrónicos que identifican como SPAM o bloquean la descarga de imágenes. Si determinan que un determinado dominio está enviando demasiados correos electrónicos, establecerán un límite en el número de correos electrónicos que aceptarán de ese remitente.

   * Al comprobar la tasa de envíos de sus correos electrónicos, debe centrarse en cuatro categorías principales: calidad de los datos, mensaje y contenido, infraestructuras de envío y reputación. Para profundizar en este tema, consulte [esta sección](../../delivery/using/about-deliverability.md).

* Aplicar las recomendaciones detalladas [en este documento](../../delivery/using/deliverability-key-points.md).

* Póngase en contacto con su representante de Adobe para obtener ayuda.

## Administración de cuarentenas {#quarantine-management}

Le conviene mantener buenos procesos de gestión de cuarentenas.

Al comenzar a enviar correos electrónicos en una nueva plataforma, puede utilizar una lista de direcciones que no esté totalmente confirmada. Si realiza envíos a direcciones no válidas o a direcciones honeypot (bandejas de entrada creadas únicamente para engañar a remitentes de correo electrónico no deseado), la reputación de su plataforma comenzará a reducirse. Los buenos procesos de administración de cuarentenas ayudan a: mantenga la calidad de la dirección, evite la lista de bloqueados de los proveedores de acceso a Internet y reduzca la tasa de errores, acelerando los envíos y el rendimiento.

**Sugerencias**

* Si tiene una lista de direcciones no válidas, Adobe recomienda importarlas a la tabla de cuarentenas, a través de **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* Los destinatarios cuyas direcciones están en cuarentena se excluyen de forma predeterminada durante el análisis de envío: no están segmentados. Esto acelera las entregas, ya que la tasa de error afecta significativamente a la velocidad de entrega. Una dirección de correo electrónico se puede poner en cuarentena, por ejemplo, cuando el buzón está lleno o si la dirección no existe. [Más información](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign administra las direcciones erróneas según el tipo de error devuelto. Para obtener más información, consulte [esta sección](../../delivery/using/understanding-quarantine-management.md).


* Algunos proveedores de acceso a Internet consideran automáticamente los correos electrónicos como no deseados si la tasa de direcciones no válidas es demasiado alta. Por lo tanto, la cuarentena le permite evitar ser agregado a una lista de bloqueados por estos proveedores.

* La administración de cuarentenas también ayudará a reducir los costos de envío de SMS al excluir los números de teléfono erróneos de los envíos.

## Mecanismo de selección de dobles {#double-opt-in}

Para evitar el envío de mensajes a direcciones no válidas, limitar las comunicaciones incorrectas y mejorar la reputación del remitente, Adobe recomienda implementar un mecanismo de selección de dobles para la confirmación posterior a la suscripción. Esto ayuda a garantizar la suscripción intencionada de un destinatario.

Los detalles para la implementación de este mecanismo se describen en [esta sección](../../web/using/use-cases--web-forms.md).
