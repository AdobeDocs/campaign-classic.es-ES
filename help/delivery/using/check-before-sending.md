---
solution: Campaign Classic
product: campaign
title: Comprobación antes de enviar
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: 50d326b0-3c23-4dbf-9df6-d32b48e30f69
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '861'
ht-degree: 100%

---

# Realice todas las comprobaciones necesarias antes de enviar {#perform-all-checks}

Cuando el mensaje esté listo, asegúrese de que su contenido se muestra correctamente en todos los dispositivos y no contiene ningún error, como por ejemplo de personalización incorrecta o enlaces rotos.

Antes de enviar el mensaje, compruebe que los parámetros y la configuración se adecuan al envío.

## Por qué la validación es clave {#validation-is-key}

Antes de entregar un envío, debe asegurarse de que sus destinatarios recibirán el mensaje que realmente desea enviarlos. Para ello, debe validar el contenido del mensaje y los parámetros de envío.

Este paso le permite detectar posibles errores y corregirlos antes de enviarlos a su destinatario principal.

Los pasos para validar un envío se presentan [en esta sección](../../delivery/using/steps-validating-the-delivery.md).

## Renderización de la bandeja de entrada {#inbox-and-email-rendering}

El procesamiento de la bandeja de entrada le permite realizar previsualizaciones de sus mensajes en los principales clientes de correo electrónico, analizar el contenido y la reputación, y descubrir cómo leen los destinatarios los mensajes.

**Sugerencias**:

* Puede ver el mensaje enviado en los diferentes contextos en los que se puede recibir webmail, servicio de mensajes, móvil, etc.

* Las funciones de renderización de la bandeja de entrada son esenciales para identificar si las campañas de correo electrónico superan correctamente los filtros de los principales ISP (proveedores de servicios de Internet) y servicios de correo electrónico. Estas herramientas envían una copia de un mensaje de correo electrónico a una red de bandejas de entrada de prueba, lo que le permite ver cómo se muestra el mensaje o cómo se renderiza en estos servicios. También pueden incluir informes y opciones de corrección de código que le ayudan a identificar y realizar correcciones con rapidez para mejorar la capacidad de envío.

Obtenga más información [en esta sección](../../delivery/using/inbox-rendering.md).

## Mensajes de prueba {#proof-messages}

El envío de pruebas le permite comprobar el vínculo de no participación, la página espejo y cualquier otro vínculo, validar el mensaje, comprobar que se muestran las imágenes, detectar posibles errores, etc. También es posible que desee comprobar el diseño y el procesamiento en distintos dispositivos.

Obtenga más información [en esta sección](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Configuración de envíos de pruebas A/B {#a-b-testing-deliveries}

Si tiene varios contenidos para un envío de correo electrónico, puede utilizar pruebas A/B para averiguar qué versión tendrá el mayor impacto en la población objetivo.

**Sugerencias**:

* Envíe las diferentes versiones a algunos de sus destinatarios

* Seleccione el que tenga la tasa de éxito más alta y envíelo al resto de destinatarios

Obtenga más información [en esta sección](../../delivery/using/get-started-a-b-testing.md).

## Asegúrese de que el mensaje se haya enviado {#make-sure-your-message-is-delivered}

Finalmente, maximice sus posibilidades y aproveche la potencia de Adobe Campaign Classic para garantizar que su mensaje se envía a los destinatarios relevantes.

### Pase por un proceso de validación

Puede definir un proceso de validación completo, que incluye los operadores y grupos de Adobe Campaign, para validar el contenido del mensaje y el destinatario. Esto garantizará una monitorización y un control completos de los distintos procesos de la campaña: segmentación, contenido, presupuesto, extracción y envío de una prueba. Según sus permisos, los usuarios pueden recibir notificaciones, recibir pruebas y validar o rechazar el mensaje. Obtenga más información [en esta sección](../../campaign/using/marketing-campaign-approval.md).

### Uso de oleadas

Puede aumentar progresivamente el volumen enviado mediante oleadas. Esto evitará que sus mensajes se marquen como correo no deseado o para limitar el número de mensajes por día. Mediante las oleadas puede dividir los envíos en varios lotes en lugar de enviar volúmenes altos de mensajes al mismo tiempo. Obtenga más información [en esta sección](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

### Priorización de mensajes

Puede configurar el orden de envío de sus envíos indicando el nivel de prioridad. Para ello:

1. Edite las propiedades del envío y seleccione la pestaña **[!UICONTROL Delivery]**.

1. Defina el nivel de prioridad del envío en una escala de **[!UICONTROL Very low]** a **[!UICONTROL Very high]**.

>[!NOTE]
>
>No es posible definir el orden de envío de mensajes desde un envío.

### Configuración de afinidades de direcciones IP

Para controlar mejor el tráfico SMTP saliente, puede administrar afinidades definiendo las direcciones IP específicas que se pueden usar para cada afinidad. Esto permite limitar el número de correos electrónicos para envíos específicos hacia equipos o direcciones de salida. Por ejemplo, puede utilizar una afinidad por país o subdominio. A continuación, puede crear una tipología por país y vincular cada afinidad a la tipología correspondiente.

Puede:

* Defina las afinidades de direcciones IP en el archivo de configuración serverConf.xml. [Más información](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Para cada elemento IPAffinity, declare las direcciones IP que se pueden usar. [Más información](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* En la [tipología](../../campaign/using/about-campaign-typologies.md) que elija, utilice el campo **[!UICONTROL Managing affinities with IP addresses]** para vincular envíos al servidor de envío (MTA) que administra dicha afinidad. [Más información](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic).

* Una vez enviado el correo electrónico, compruebe el encabezado para ver desde qué dirección IP se entregó el envío. El administrador de correo electrónico debe ayudarle a obtener la información del encabezado.

>[!NOTE]
>
>La mayoría de estos pasos solo los puede realizar un usuario experto.

### Uso de tipologías

Puede utilizar reglas de tipología para excluir parte del destinatario según criterios específicos. Esto garantiza que los mensajes enviados respondan de la mejor forma a las necesidades y expectativas de los clientes, de acuerdo con las políticas de comunicación de la compañía. Por ejemplo, puede filtrar los destinatarios menores de edad del objetivo de su boletín informativo. Obtenga más información [en este ejemplo](../../campaign/using/filtering-rules.md).

### Prevención de envío de archivos adjuntos

Los archivos adjuntos son uno de los vectores más comunes de propagación de software malicioso, especialmente cuando se envían en lotes. Incluya un enlace seguro al documento en lugar de adjuntar el propio documento. Esto garantiza un nivel adicional de seguridad para evitar una redistribución no deseada y reduce considerablemente las posibilidades de que el mensaje se rechace en las puertas de enlace de correo electrónico entrantes por motivos de seguridad o tamaño del mensaje.
