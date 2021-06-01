---
product: campaign
title: Administración de la presentación de ofertas
description: Administración de la presentación de ofertas
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: 6158ffaa-cb08-4f77-82b8-b3e5e1bf7fd7
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '996'
ht-degree: 100%

---

# Administración de la presentación de ofertas{#managing-offer-presentation}

## Información general sobre las reglas de presentación {#presentation-rules-overview}

La interacción permite controlar el flujo de propuestas de ofertas utilizando las reglas de presentación. Estas reglas, que son específicas de la interacción, son reglas de tipología. Permiten excluir ofertas basadas en el historial de propuestas que ya se hayan hecho a un destinatario. Se las menciona en el entorno.

## Creación y referencia de una regla de presentación de oferta {#creating-and-referencing-an-offer-presentation-rule}

1. Vaya al nodo **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]**.
1. Cree una regla de tipología y elija el tipo **[!UICONTROL Offer presentation]**.

   ![](assets/offer_typology_001.png)

1. Especifique el canal al cual se debe aplicar la regla.

   ![](assets/offer_typology_002.png)

1. Configure los criterios de aplicación de la regla. Para obtener más información, consulte [Presentation rule settings](#presentation-rule-settings),
1. Vaya al nodo **[!UICONTROL Administration]** > **[!UICONTROL Campaign execution]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typologies]** y cree una tipología que agrupe todas las reglas del tipo **[!UICONTROL Offer presentation]**.

   ![](assets/offer_typology_003.png)

1. Una vez creada la tipología, coloque el cursor en las reglas de tipología y agrúpelas en la tipología que acaba de crear.

   ![](assets/offer_typology_004.png)

1. En el entorno de oferta, haga referencia a la tipología con la lista desplegable.

   ![](assets/offer_typology_005.png)

## Configuración de la regla de presentación {#presentation-rule-settings}

### Criterios de aplicación {#application-criteria-}

Los criterios de aplicación disponibles en la pestaña **[!UICONTROL General]** le permiten especificar las ofertas a las que se aplica la regla de presentación. Para hacer esto, necesita crear una consulta y elegir las ofertas que le interesen, como se describe a continuación.

1. En las reglas de tipología, haga clic en el vínculo **[!UICONTROL Edit the rule application conditions...]** para crear la consulta.

   ![](assets/offer_typology_006.png)

1. En la ventana de consulta, puede aplicar un filtro en las ofertas en las que desee aplicar una regla de tipología.

   Por ejemplo, puede seleccionar una categoría de oferta.

   ![](assets/offer_typology_008.png)

### Dimensiones de la oferta {#offer-dimensions}

En la pestaña **[!UICONTROL Offer presentation]** debe especificar las mismas dimensiones para la regla de presentación que las configuradas en el entorno.

La **[!UICONTROL Targeting dimension]** coincide con la tabla de destinatarios (de forma predeterminada: nms:recipients) que recibirán las propuestas de las ofertas. **[!UICONTROL Storage dimension]** coincide con la tabla que contiene el historial de propuestas vinculado a la dimensión de destino (de forma predeterminada: nms:propositionRcp).

![](assets/offer_typology_009.png)

>[!NOTE]
>
>También se puede utilizar tablas no estándar. Si se desea utilizar una dimensión de objetivo específica, se debe crear tablas y un entorno dedicado utilizando la asignación de objetivo. Para obtener más información, consulte [Creación de un entorno de ofertas](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

### Periodo {#period}

Este es un periodo de deslizamiento que comienza en la fecha de presentación de la oferta. Establece un tiempo límite para la validez de la propuesta de ofertas. La regla no se aplica a las propuestas de ofertas realizadas más allá de este periodo.

El periodo comienza **n** días antes de la fecha de la propuesta y finaliza **n** días después, donde **n** corresponde al número introducido en el campo **[!UICONTROL Period considered]**:

* Para los espacios entrantes, la fecha de la propuesta es la fecha de presentación de la oferta.
* En los espacios salientes, la fecha de la propuesta es la fecha de contacto de la entrega (por ejemplo, la fecha de entrega introducida en un flujo de trabajo de objetivo).

Utilice las flechas para cambiar el número de días o introduzca directamente un periodo (“2 d 6 h”, por ejemplo).

![](assets/offer_typology_010.png)

### Número de propuestas {#number-of-propositions}

Es posible establecer el número más alto de propuestas que se pueden realizar antes de que se excluyan las respectivas ofertas.

Utilice las flechas para cambiar el número de las propuestas de las ofertas.

![](assets/offer_typology_011.png)

## Definición de propuestas y destinatarios {#defining-propositions-and-recipients}

La sección **[!UICONTROL Propositions to count]** permite especificar los destinatarios y las propuestas que llevarán a la exclusión de las ofertas definidas en la pestaña **[!UICONTROL General]** si aparecen un determinado número de veces en el historial de las propuestas.

### Filtrado de las propuestas {#filtering-propositions}

Puede seleccionar los criterios de filtrado para excluir las propuestas en función del canal, las ofertas correspondientes o el estado de las propuestas asignadas anteriormente.

![](assets/offer_typology_014.png)

Estos criterios representan las aplicaciones más frecuentes de las reglas de presentación. Para utilizar otros criterios, se puede crear una consulta utilizando el vínculo **[!UICONTROL Limit propositions...]**. Para obtener más información, consulte [Creación de una consulta sobre proposiciones](#creating-a-query-on-propositions).

* **Filtros del canal**

   **[!UICONTROL On the same channel only]**: permite excluir propuestas de oferta en el canal especificado en la pestaña **[!UICONTROL General]**.

   Por ejemplo, el canal especificado para la regla de la pestaña **[!UICONTROL General]** es email. Si las ofertas a las que se aplica la regla solo se ofrecen en el canal web, el motor de interacción puede presentar las ofertas en una entrega por email. Sin embargo, una vez que se presentan las ofertas por correo electrónico, el motor de interacción elige un canal diferente para presentar las ofertas.

   >[!NOTE]
   >
   >Se habla del canal y no del espacio. Si la regla excluye una oferta del canal web, la oferta a presentar en un sitio web, en dos espacios (por ejemplo, en un banner y en el cuerpo de la página), no se visualiza en el sitio si ya se ha presentado antes.
   >
   >En un flujo de trabajo que incluya presentación de oferta, las reglas solo se aplican correctamente si están configuradas en **[!UICONTROL All channels]**.

* **Filtro en la oferta**

   Este filtro permite restringir las propuestas de ofertas que se cuentan como determinados conjuntos de ofertas.

   **[!UICONTROL All offers]** : valor predeterminado. No se aplica ningún filtro a las ofertas.

   **[!UICONTROL Offer being presented]**: la oferta especificada en la pestaña **[!UICONTROL General]** se excluye si ya se ha presentado.

   **[!UICONTROL Offers from the same category]**: se excluye una oferta si ya se ha presentado una oferta de la misma categoría.

   **[!UICONTROL The offers which the rule applies to]**: cuando se definen varias ofertas en la pestaña **[!UICONTROL General]**, cada propuesta de oferta de este conjunto de ofertas se toma en cuenta y finaliza en la exclusión de todas las ofertas si se alcanza el umbral de propuestas.

   Por ejemplo, las ofertas 2, 3 y 5 se definen en la pestaña **[!UICONTROL General]**. El número máximo de propuestas se establece en 2. Si las ofertas 2 y 5 se presentan una vez, el número de propuestas contadas será 2. Como resultado, la oferta 3 nunca se presenta.

* **Filtro en el estado de la propuesta**

   Este filtro le permite elegir los estados más frecuentes para que la propuesta de ofertas sea tomada en cuenta en el historial de propuestas.

   **[!UICONTROL Regardless of the proposition status]** : valor predeterminado. No se aplica ningún filtro al estado de la propuesta.

   **[!UICONTROL Accepted or rejected propositions]**: permite excluir las ofertas presentadas anteriormente que se han aceptado o rechazado.

   **[!UICONTROL Accepted propositions]**: permite excluir las ofertas presentadas anteriormente que se han aceptado.

   **[!UICONTROL Rejected propositions]**: permite excluir las ofertas presentadas anteriormente que se han rechazado.

### Definición de destinatarios {#defining-recipients}

Para especificar los destinatarios, haga clic en el vínculo **[!UICONTROL Edit the query from the targeting dimension...]** y seleccione los destinatarios según la regla.

![](assets/offer_typology_012.png)

### Creación de una consulta en propuestas {#creating-a-query-on-propositions}

Para especificar las propuestas que se van a contar mediante una consulta, haga clic en el vínculo **[!UICONTROL Limit propositions...]** y especifique los criterios que se van a tener en cuenta.

En el ejemplo siguiente, las propuestas que se van a contar después de dos presentaciones son las de la categoría **Ofertas especiales**, para el espacio del **centro de llamadas**, con un peso inferior a **20**.

![](assets/offer_typology_013.png)
