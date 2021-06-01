---
product: campaign
title: Uso de plantillas de envíos
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: a5da3f29-5eab-428c-b7c3-d9e4243fe628
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 100%

---

# Uso de plantillas {#use-templates}

Las plantillas de envíos ofrecen una mayor eficiencia al proporcionar escenarios listos para usar para los tipos de actividades más comunes. Con las plantillas, los especialistas en marketing pueden implementar nuevas campañas con una personalización mínima en un período de tiempo más corto.

Obtenga más información sobre las plantillas de envíos en [esta sección](../../delivery/using/creating-a-delivery-template.md).

## Introducción a las plantillas de envíos {#gs-templates}

Una [plantilla de envíos](../../delivery/using/creating-a-delivery-template.md) le permite definir una vez un conjunto de propiedades técnicas y funcionales que se adaptan a sus necesidades y pueden reutilizarse en futuros envíos. A continuación, puede ahorrar tiempo y estandarizar envíos cuando sea necesario.

Cuando se gestionan varias marcas en Adobe Campaign, Adobe recomienda tener un subdominio por marca. Por ejemplo, un banco puede tener varios subdominios correspondientes a cada una de sus agencias regionales. Si un banco posee el dominio bluebank.com, sus subdominios pueden ser @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com, etc. Tener una plantilla de envíos para cada subdominio le permite utilizar los parámetros preconfigurados adecuados para cada una de sus marcas, lo que evita errores y le ahorra tiempo.

**Sugerencia**: Para evitar errores de configuración, se recomienda duplicar una plantilla nativa y modificar sus propiedades, en lugar de crear una plantilla nueva.

## Configuración de direcciones

* La dirección del remitente es obligatoria para permitir que se envíe un mensaje de correo electrónico.

* Algunos ISP (proveedores de servicios de Internet) comprueban la validez de la dirección del remitente antes de aceptar mensajes.

* Una dirección mal formada puede resultar en que el servidor receptor la rechace. Debe asegurarse de que se proporciona una dirección correcta.

* La dirección debe identificar explícitamente al remitente. El dominio debe ser propiedad del remitente y estar registrado en él.

* Adobe recomienda crear cuentas de correo electrónico que se correspondan con las direcciones especificadas para envíos y respuestas. Consulte con el administrador del sistema de mensajería.

Para configurar direcciones en la interfaz de Campaign, siga los pasos a continuación:

1. En la [plantilla de envíos](../../delivery/using/creating-a-delivery-template.md), haga clic en el vínculo **[!UICONTROL From]**. En la ventana **[!UICONTROL Email header parameters]**, rellene los campos siguientes:

   ![](assets/d_best_practices_email_header.png)

1. En el campo **[!UICONTROL Sender address]**, asegúrese de que el dominio de dirección sea el mismo que el subdominio que delegó en Adobe. Puede cambiar la parte que precede a &#39;@&#39;, pero no la dirección de dominio.

1. En el campo **[!UICONTROL From]**, utilice un nombre fácilmente identificable por los destinatarios, como el nombre de su marca, para aumentar la velocidad de apertura de sus envíos. Para mejorar aún más la experiencia del destinatario, puede agregar el nombre de una persona como, por ejemplo, &quot;Emma de Megastore&quot;.

1. En los campos **[!UICONTROL Reply address text]**, la dirección del remitente se utiliza de forma predeterminada para las respuestas. Sin embargo, Adobe recomienda utilizar una dirección real existente, como el servicio de atención al cliente de su marca. En este caso, si un destinatario envía una respuesta, el servicio de atención al cliente podrá atenderla.

### Configuración de un grupo de control

Una vez entregado el envío, puede comparar el comportamiento de los destinatarios excluidos con el de los destinatarios que sí recibieron el envío. Puede medir la eficacia de sus campañas. Obtenga más información sobre los grupos de control [en esta sección](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Para configurar un grupo de control, haga clic en el vínculo **[!UICONTROL To]**. En la ventana **[!UICONTROL Select target]**, seleccione la pestaña **[!UICONTROL Control group]**. Puede extraer una parte de los destinatarios como, por ejemplo, una muestra aleatoria del 5 %.

![](assets/d_best_practices_control_group.png)

## Uso de tipologías para aplicar filtros o reglas de control

Una tipología contiene reglas de comprobación que se aplican durante la fase de análisis antes de enviar un mensaje.

En la pestaña **[!UICONTROL Typology]** de las propiedades de la plantilla, cambie la tipología predeterminada según sus necesidades.

Por ejemplo, para controlar mejor el tráfico saliente, puede definir qué direcciones IP se pueden utilizar definiendo una afinidad por subdominio y creando una tipología por afinidad. Las afinidades se definen en el archivo de configuración de la instancia. Póngase en contacto con el administrador de Adobe Campaign.

Para obtener más información sobre tipologías, consulte [esta sección](../../campaign/using/about-campaign-typologies.md).
