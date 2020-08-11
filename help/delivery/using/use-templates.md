---
title: Usar Plantillas de envíos
seo-title: Usar Plantillas de envíos
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
source-wordcount: '583'
ht-degree: 14%

---


# Uso de plantillas {#use-templates}

Las Plantillas de envíos permiten una mayor eficiencia al proporcionar escenarios listos para usar para los tipos de actividades más comunes. Con las plantillas, los especialistas en marketing pueden implementar nuevas campañas con una personalización mínima en un período de tiempo más corto.

Obtenga más información sobre Plantillas de envíos en [esta sección](../../delivery/using/creating-a-delivery-template.md).

## Introducción a las Plantillas de envíos {#gs-templates}

Una [Plantilla de envíos](../../delivery/using/creating-a-delivery-template.md) le permite definir una vez un conjunto de propiedades técnicas y funcionales que se adapten a sus necesidades y que pueden reutilizarse para futuros envíos. A continuación, puede ahorrar tiempo y estandarizar envíos cuando sea necesario.

Cuando se gestionan varias marcas en Adobe Campaign, Adobe recomienda tener un subdominio por marca. Por ejemplo, un banco puede tener varios subdominios correspondientes a cada una de sus agencias regionales. Si un banco posee el dominio bluebank.com, sus subdominios pueden ser @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com, etc. Tener una plantilla de envíos para cada subdominio le permite utilizar los parámetros preconfigurados adecuados para cada una de sus marcas, lo que evita errores y le ahorra tiempo.

**Sugerencia**:  Para evitar errores de configuración en Campaign Standard, se recomienda que duplicado una plantilla nativa y modifique sus propiedades en lugar de crear una nueva plantilla.

## Configuración de direcciones

* La dirección del remitente es obligatoria para permitir el envío de un correo electrónico.

* Algunos ISP (Proveedores de servicio de Internet) comprueban la validez de la dirección del remitente antes de aceptar mensajes.

* Una dirección mal formada puede resultar en que el servidor receptor la rechace. Debe asegurarse de que se proporciona una dirección correcta.

* La dirección debe identificar explícitamente al remitente. El dominio debe ser propiedad del remitente y estar registrado en él.

* Adobe recomienda crear cuentas de correo electrónico que se correspondan con las direcciones especificadas para envíos y respuestas. Consulte con el administrador del sistema de mensajería.

Para configurar direcciones en la interfaz de Campaña, siga los pasos a continuación:

1. En la [Plantilla de envíos](../../delivery/using/creating-a-delivery-template.md), haga clic en el **[!UICONTROL From]** vínculo. En la **[!UICONTROL Email header parameters]** ventana, rellene los campos siguientes:

   ![](assets/d_best_practices_email_header.png)

1. En el **[!UICONTROL Sender address]** campo, asegúrese de que el dominio de dirección es el mismo que el subdominio que delegó en Adobe. Puede cambiar la parte que precede a &#39;@&#39; pero no la dirección de dominio.

1. En el **[!UICONTROL From]** campo, utilice un nombre fácilmente identificable por los destinatarios, como el nombre de su marca, para aumentar la velocidad de apertura de sus envíos. Para mejorar aún más la experiencia del destinatario, puede agregar el nombre de una persona, por ejemplo &quot;Emma de Megastore&quot;.

1. En los **[!UICONTROL Reply address text]** campos, la dirección del remitente se utiliza de forma predeterminada para las respuestas. Sin embargo, Adobe recomienda utilizar una dirección real existente, como el servicio de atención al cliente de su marca. En este caso, si un destinatario envía una respuesta, el servicio de atención al cliente podrá atenderla.

### Configuración de un grupo de control

Una vez enviado el envío, puede comparar el comportamiento de los destinatarios excluidos con los destinatarios que sí recibieron el envío. Puede medir la eficacia de sus campañas. Obtenga más información sobre grupos de control en [esta sección](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Para configurar un grupo de control, haga clic en el **[!UICONTROL To]** vínculo. En la **[!UICONTROL Select target]** ventana, seleccione la **[!UICONTROL Control group]** ficha. Puede extraer una parte del destinatario, por ejemplo, una muestra aleatoria del 5 %.

![](assets/d_best_practices_control_group.png)

## Usar tipologías para aplicar filtros o reglas de control

Una tipología contiene reglas de comprobación que se aplican durante la fase de análisis antes de enviar un mensaje.

En la **[!UICONTROL Typology]** ficha de las propiedades de la plantilla, cambie la tipología predeterminada según sus necesidades.

Por ejemplo, para controlar mejor el tráfico saliente, puede definir qué direcciones IP se pueden utilizar definiendo una afinidad por subdominio y creando una tipología por afinidad. Las afinidades se definen en el archivo de configuración de la instancia. Póngase en contacto con el administrador de Adobe Campaign.

For more on typologies, refer to [this section](../../campaign/using/about-campaign-typologies.md).
