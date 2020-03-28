---
title: Integración de una oferta mediante el asistente
seo-title: Integración de una oferta mediante el asistente
description: Integración de una oferta mediante el asistente
seo-description: null
page-status-flag: never-activated
uuid: 0d8cf0b5-fc27-4bf4-bd1d-892fe6e3257b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
discoiquuid: 181fcb70-9394-4091-93df-92c39273ec3d
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Integración de una oferta mediante el asistente{#integrating-an-offer-via-the-wizard}

Al crear una entrega, existen dos métodos posibles para la integración de ofertas:

* Visualizar el motor de oferta en el cuerpo de una entrega.
* Hacer referencia a ofertas a través de las descripciones del envío de una campaña. Este método se utiliza generalmente para campañas en papel.

## Envío con visualización del motor de oferta {#delivering-with-a-call-to-the-offer-engine}

Para presentar una oferta durante una campaña de marketing, simplemente cree una acción de envío clásica basada en el canal elegido. El motor de oferta se visualiza cuando se define el contenido de la entrega haciendo clic en el icono **[!UICONTROL Ofertas]** disponible en la barra de herramientas.

![](assets/offer_delivery_009.png)

Para obtener más información sobre las entregas y las campañas de marketing, consulte [Envío](../../delivery/using/about-direct-mail-channel.md) y [Campaña](../../campaign/using/setting-up-marketing-campaigns.md).

### Pasos principales para insertar una oferta en una entrega {#main-steps-for-inserting-an-offer-into-a-delivery}

Para insertar las propuestas de oferta en una entrega, siga los siguientes pasos:

1. En la ventana de envío, haga clic en el icono Ofertas.

   ![](assets/offer_delivery_001.png)

1. Seleccione el espacio que coincida con el entorno de la oferta.

   ![](assets/offer_delivery_002.png)

1. Para perfeccionar la elección de las ofertas de motor, seleccione la categoría desde la que se presentan las ofertas, o bien uno o varios temas. Solo se recomienda utilizar uno de estos campos a la vez para evitar sobrecargar las restricciones.

   ![](assets/offer_delivery_003.png)

   ![](assets/offer_delivery_004.png)

1. Especifique el número de ofertas que desea insertar en el cuerpo de la entrega.

   ![](assets/offer_delivery_005.png)

1. Seleccione la opción **[!UICONTROL Excluir destinatarios no elegibles]** si es necesario. Para obtener más información sobre esto, consulte [Parámetros para llamar al motor de ofertas](#parameters-for-calling-offer-engine).

   ![](assets/offer_delivery_006.png)

1. Si es necesario, seleccione la opción **[!UICONTROL No mostrar nada si no se seleccionan ofertas]**. Para obtener más información sobre esto, consulte [Parámetros para llamar al motor de ofertas](#parameters-for-calling-offer-engine).

   ![](assets/offer_delivery_007.png)

1. Inserte las propiedades en el contenido de la entrega mediante los campos combinados. El número de propuestas disponibles depende del modo en que se configura la visualización del motor y su orden depende de la prioridad de las ofertas.

   ![](assets/offer_delivery_008.png)

1. Finalice el contenido y realice la entrega de la forma habitual.

   ![](assets/offer_delivery_010.png)

### Parámetros para llamar al motor de oferta {#parameters-for-calling-offer-engine}

* **[!UICONTROL Espacio]** : espacio del entorno de oferta que debe seleccionarse para activar el motor de oferta.
* **[!UICONTROL Categoría]** : carpeta específica en la que se ordenan las ofertas. Si no se especifica ninguna categoría, el motor de oferta llevará a cabo todas las ofertas contenidas en el entorno, a menos que se seleccione un tema.
* **[!UICONTROL Temas]** : las palabras clave se definen hacia arriba en las categorías. Estos actúan como un filtro y permiten refinar la cantidad de ofertas que se presentarán seleccionándolas de un conjunto de categorías.
* **[!UICONTROL Número de proposiciones]** : número de ofertas que devuelve el motor que se puede insertar en el cuerpo de la entrega. Si no se insertan en el mensaje, las ofertas se generarán, pero no se presentarán.
* **[!UICONTROL Excluir destinatarios no elegibles]** : Esta opción permite activar o desactivar la exclusión de destinatarios para los que no haya suficientes ofertas aptas. El número de propuestas puede ser inferior al número solicitado de propuestas. Si se selecciona este cuadro, los destinatarios que no tengan suficientes propuestas se excluirán de la entrega. Si no selecciona esta opción, estos destinatarios no se excluirán, pero no tendrán el número solicitado de propuestas.
* **[!UICONTROL No mostrar nada si no se selecciona ninguna oferta]** : Esta opción le permite elegir cómo se procesará el mensaje en caso de que una de las propuestas no exista. Cuando se activa esta casilla, no se muestra la representación de la propuesta que falta y no aparecerá ningún contenido en el mensaje para esta propuesta. Si el cuadro no está activado, el mensaje en sí se cancela durante la entrega y los destinatarios ya no recibirán ningún mensaje.

### Inserción de una propuesta de oferta en una entrega.{#inserting-an-offer-proposition-into-a-delivery}

La descripción de las ofertas a presentar se inserta en el cuerpo de la entrega a través de los campos combinados. El número de propuestas se define en los parámetros de acceso al motor de oferta.

El envío se puede personalizar utilizando los campos de la oferta o, en el caso de un email, en las funciones de renderización.

![](assets/offer_delivery_011.png)

## Entrega con descripción de la entrega {#delivering-with-delivery-outlines}

También se pueden presentar ofertas en una entrega utilizando la descripción de la entrega.

Para obtener más información sobre la descripción de las entregas, consulte la guía [Campaign - MRM](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. Cree una nueva campaña o acceda a una campaña existente.
1. Acceda a los esquemas de entrega a través de la pestaña campaña **[!UICONTROL Editar]** > **[!UICONTROL Documentos]**.
1. Añada una descripción e inserte tantas ofertas como desee haciendo clic con el botón derecho en la descripción y seleccione **[!UICONTROL Nuevo]** > **[!UICONTROL Oferta]**, a continuación, guarde la campaña.

   ![](assets/int_compo_offre1.png)

1. Cree una entrega que tenga acceso a la descripción del mismo (por ejemplo, una entrega de correo postal).
1. Al editar la entrega, haga clic en **[!UICONTROL Seleccione un esquema de entrega]**.

   >[!NOTE]
   >
   >En función del tipo de envío, esta opción se puede encontrar en el menú **[!UICONTROL Propiedades]** > **[!UICONTROL Avanzado]** (por ejemplo, en envíos de correo postal).

   ![](assets/int_compo_offre2.png)

1. Con el botón **[!UICONTROL Ofertas]**, se puede configurar el espacio de oferta y el número de ofertas que se presentan en la entrega.

   ![](assets/int_compo_offre3.png)

1. Añada las propuestas al cuerpo de la entrega mediante los campos de personalización (para más información, consulte la sección [Insertar una propuesta de oferta en una entrega](#inserting-an-offer-proposition-into-a-delivery)), o en el caso de una entrega de correo postal, editando el formato del archivo extraíble.

   Las propuestas se seleccionan entre las ofertas especificadas en la descripción de la entrega.

   >[!NOTE]
   >
   >La información relativa a las clasificaciones y relevancia de la oferta solo se guarda en la lista de propuestas si las ofertas son generadas directamente en la entrega.

