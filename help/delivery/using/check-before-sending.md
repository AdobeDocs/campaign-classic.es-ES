---
title: Comprobar antes de enviar
seo-title: Comprobar antes de enviar
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
source-wordcount: '864'
ht-degree: 33%

---


# Realizar todas las comprobaciones antes de enviar {#perform-all-checks}

Cuando el mensaje esté listo, asegúrese de que su contenido se muestra correctamente en todos los dispositivos y no contiene ningún error, como por ejemplo de personalización incorrecta o enlaces rotos.

Antes de enviar el mensaje, compruebe que los parámetros y la configuración se adecuan al envío.

## Por qué la validación es clave {#validation-is-key}

Antes de enviar un envío, debe asegurarse de que sus destinatarios recibirán el mensaje que realmente desea enviarlos. Para ello, debe validar el contenido del mensaje y los parámetros de envío.

Este paso le permite detectar posibles errores y corregirlos antes de enviarlos a su destinatario principal.

Los pasos para validar un envío se presentan [en esta sección](../../delivery/using/steps-validating-the-delivery.md).

## Renderización de la bandeja de entrada {#inbox-and-email-rendering}

El procesamiento de la bandeja de entrada le permite realizar previsualizaciones de sus mensajes en los principales clientes de correo electrónico, analizar el contenido y la reputación, descubrir cómo los destinatarios leen los mensajes.

**Sugerencias**:

* Puede vista del mensaje enviado en los diferentes contextos en los que se puede recibir: webmail, servicio de mensajes, móvil, etc.

* Las funciones de procesamiento de la bandeja de entrada son cruciales para identificar si las campañas de correo electrónico superan con éxito los filtros de los principales ISP (Proveedores de servicio de Internet) y servicios de correo web. Estas herramientas envían una copia de un mensaje de correo electrónico a una red de bandejas de entrada de prueba, lo que le permite ver cómo se muestra el mensaje o cómo se renderiza en estos servicios. También pueden incluir informes y opciones de corrección de código que le ayudan a identificar y realizar correcciones con rapidez para mejorar la capacidad de envío.

Learn more [in this section](../../delivery/using/inbox-rendering.md).

## Mensajes de prueba {#proof-messages}

El envío de pruebas le permite comprobar el vínculo de exclusión, la página espejo y cualquier otro vínculo, validar el mensaje, comprobar que se muestran las imágenes, detectar posibles errores, etc. También es posible que desee comprobar el diseño y el procesamiento en distintos dispositivos.

Learn more [in this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Configuración de envíos de prueba A/B {#a-b-testing-deliveries}

Si tiene varios contenidos para un envío de correo electrónico, puede utilizar la prueba A/B para averiguar qué versión tendrá el mayor impacto en la población objetivo.

**Sugerencias**:

* Envíe las diferentes versiones a algunos de sus destinatarios

* Seleccione el que tenga la tasa de éxito más alta y envíelo al resto del destinatario

Learn more [in this section](../../workflow/using/a-b-testing.md).

## Asegúrese de que el mensaje se haya enviado {#make-sure-your-message-is-delivered}

Finalmente, maximice sus posibilidades y aproveche la potencia de Adobe Campaign Classic para garantizar que su mensaje se envía a los destinatarios relevantes.

### Pase por un proceso de validación

Puede definir un proceso de validación completo, que incluye los operadores y grupos de Adobe Campaign, para validar el contenido del mensaje y el destinatario. Esto garantizará la supervisión y el control plenos de los diversos procesos de la campaña: segmentación, contenido, presupuesto, extracción y envío de una prueba. Según sus permisos, los usuarios pueden recibir notificaciones, recibir pruebas y validar o rechazar el mensaje. Learn more [in this section](../../campaign/using/marketing-campaign-approval.md#approval-process).

### Usar olas

Puede aumentar progresivamente el volumen enviado mediante olas. Esto evitará que sus mensajes se marquen como correo no deseado o cuando desee restringir el número de mensajes por día. Mediante las oleadas puede dividir los envíos en varios lotes en lugar de enviar volúmenes altos de mensajes al mismo tiempo. Learn more [in this section](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

### Priorizar mensajes

Puede configurar el orden de envío de sus envíos indicando el nivel de prioridad. Para ello:

1. Edite las propiedades del envío y seleccione la **[!UICONTROL Delivery]** ficha.

1. Defina el nivel de prioridad del envío en una escala de **[!UICONTROL Very low]** a **[!UICONTROL Very high]**.

>[!NOTE]
>
>No es posible definir el orden de envío de mensajes desde un envío.

### Configurar Afinidades IP

Para controlar mejor el tráfico SMTP saliente, puede administrar afinidades definiendo las direcciones IP específicas que se pueden usar para cada afinidad. Esto permite limitar el número de correos electrónicos para envíos específicos hacia equipos o direcciones de salida. Por ejemplo, puede utilizar una afinidad por país o subdominio. A continuación, puede crear una tipología por país y vincular cada afinidad a la tipología correspondiente.

Se puede:

* Defina las afinidades IP en el archivo de configuración serverConf.xml. [Más información](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Para cada elemento IPAffinity, declare las direcciones IP que se pueden usar. [Más información](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* En la [tipología](../../campaign/using/about-campaign-typologies.md) que elija, utilice el **[!UICONTROL Managing affinities with IP addresses]** campo para vincular envíos al servidor de envío (MTA) que administra dicha afinidad. [Más información](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic).

* Una vez enviado el correo electrónico, compruebe el encabezado para comprobar de qué dirección IP se envió el envío. El administrador de correo electrónico debe ayudarle a obtener la información del encabezado.

>[!NOTE]
>
>La mayoría de estos pasos sólo los puede realizar un usuario experto.

### Usar tipologías

Puede utilizar reglas de tipología para excluir parte del destinatario según criterios específicos. Esto garantiza que los mensajes enviados respondan de la mejor forma a las necesidades y expectativas de los clientes, de acuerdo con las políticas de comunicación de la compañía. Por ejemplo, puede filtrar los destinatarios menores de edad del objetivo de su boletín informativo. Obtenga más información [en este ejemplo](../../campaign/using/filtering-rules.md).

### Evitar archivos adjuntos

Los archivos adjuntos son uno de los vectores más comunes de propagación de software malicioso, especialmente cuando se envían en lotes. Incluya un enlace seguro al documento en lugar de adjuntar el propio documento. Esto garantiza un nivel adicional de seguridad para evitar una redistribución no deseada y reduce considerablemente las posibilidades de que el mensaje se rechace en las puertas de enlace de correo electrónico entrantes por motivos de seguridad o tamaño del mensaje.
