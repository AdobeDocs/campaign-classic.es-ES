---
title: Administración de la presentación de ofertas
seo-title: Administración de la presentación de ofertas
description: Administración de la presentación de ofertas
seo-description: null
page-status-flag: never-activated
uuid: cf4614b9-a322-4170-aa6d-4f138f8ca2d2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: f6e44634-3a13-480e-ab44-f3c744054a96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Administración de la presentación de ofertas{#managing-offer-presentation}

## Información general sobre las reglas de presentación {#presentation-rules-overview}

La interacción permite controlar el flujo de propuestas de ofertas utilizando las reglas de presentación. Estas reglas, que son específicas de la interacción, son reglas de tipología. Permiten excluir ofertas basadas en el historial de propuestas que ya se hayan hecho a un destinatario. Se las menciona en el entorno.

## Creación y referencia de una regla de presentación de oferta {#creating-and-referencing-an-offer-presentation-rule}

1. Vaya al nodo **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** .
1. Create a typology rule and choose the **[!UICONTROL Offer presentation]** type.

   ![](assets/offer_typology_001.png)

1. Especifique el canal al cual se debe aplicar la regla.

   ![](assets/offer_typology_002.png)

1. Configure los criterios de aplicación de la regla. Para obtener más información sobre esto, consulte Configuración de reglas [de presentación](#presentation-rule-settings).
1. Vaya al nodo **[!UICONTROL Administration]** > **[!UICONTROL Campaign execution]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typologies]** y cree una tipología que agrupe todas las reglas **[!UICONTROL Offer presentation]** de tipo.

   ![](assets/offer_typology_003.png)

1. Una vez creada la tipología, coloque el cursor en las reglas de tipología y agrúpelas en la tipología que acaba de crear.

   ![](assets/offer_typology_004.png)

1. En el entorno de oferta, haga referencia a la tipología con la lista desplegable.

   ![](assets/offer_typology_005.png)

## Configuración de la regla de presentación {#presentation-rule-settings}

### Criterios de aplicación {#application-criteria-}

The application criteria available in the **[!UICONTROL General]** tab lets you specify the offers which the presentation rule will apply to. Para hacer esto, necesita crear una consulta y elegir las ofertas que le interesen, como se describe a continuación.

1. In your typology rule, click the **[!UICONTROL Edit the rule application conditions...]** link to create your query.

   ![](assets/offer_typology_006.png)

1. En la ventana de consulta, puede aplicar un filtro en las ofertas en las que desee aplicar una regla de tipología.

   Por ejemplo, puede seleccionar una categoría de oferta.

   ![](assets/offer_typology_008.png)

### Dimensiones de la oferta {#offer-dimensions}

In the **[!UICONTROL Offer presentation]** tab, you must specify the same dimensions for the presentation rule as those configured in the environment.

The **[!UICONTROL Targeting dimension]** coincides with the table of recipients (by default: nms:recipients) who will receive the offer propositions. The **[!UICONTROL Storage dimension]** coincides with the table which contains the proposition history linked to the targeting dimension (by default:nms:propositionRcp).

![](assets/offer_typology_009.png)

>[!NOTE]
>
>También se puede utilizar tablas no estándar. Si se desea utilizar una dimensión de objetivo específica, se debe crear tablas y un entorno dedicado utilizando la asignación de objetivo. Para obtener más información sobre esto, consulte [Creación de un entorno](../../interaction/using/live-design-environments.md#creating-an-offer-environment)de ofertas.

### Periodo {#period}

Este es un periodo de deslizamiento que comienza en la fecha de presentación de la oferta. Establece un tiempo límite para la validez de la propuesta de ofertas. La regla no se aplica a las propuestas de ofertas realizadas más allá de este periodo.

The period starts **n** days before the proposition date and ends **n** days afterwards, where **n** corresponds to the number entered in the **[!UICONTROL Period considered]** field:

* Para los espacios entrantes, la fecha de la propuesta es la fecha de presentación de la oferta.
* En los espacios salientes, la fecha de la propuesta es la fecha de contacto del envío (por ejemplo, la fecha de envío introducida en un flujo de trabajo de objetivo).

Utilice las flechas para cambiar el número de días o introduzca directamente un período (“2 d 6 h”, por ejemplo).

![](assets/offer_typology_010.png)

### Número de propuestas {#number-of-propositions}

Es posible establecer el número más alto de propuestas que se pueden realizar antes de que se excluyan las respectivas ofertas.

Utilice las flechas para cambiar el número de las propuestas de las ofertas.

![](assets/offer_typology_011.png)

## Definición de propuestas y destinatarios {#defining-propositions-and-recipients}

The **[!UICONTROL Propositions to count]** section lets you specify both the recipients and the propositions which will lead to the exclusion of the offers defined in the **[!UICONTROL General]** tab if they appear a certain number of times in the propositions history.

### Filtrado de las propuestas {#filtering-propositions}

Puede seleccionar los criterios de filtrado para excluir las propuestas en función del canal, las ofertas correspondientes o el estado de las propuestas asignadas anteriormente.

![](assets/offer_typology_014.png)

Estos criterios representan las aplicaciones más frecuentes de las reglas de presentación. To use other criteria, you can create a query using the **[!UICONTROL Limit propositions...]** link. Para obtener más información sobre esto, consulte la sección [Creación de una consulta sobre propuestas](#creating-a-query-on-propositions) .

* **Filtros del canal**

   **[!UICONTROL On the same channel only]** :: permite excluir las propuestas de oferta en el canal especificado en la **[!UICONTROL General]** ficha.

   For instance, the channel specified for the rule in the **[!UICONTROL General]** tab is email. Si las ofertas a las que se aplica la regla solo se ofrecen en el canal web, el motor de interacción puede presentar las ofertas en un envío por email. Sin embargo, una vez que se presentan las ofertas por correo electrónico, el motor de interacción elige un canal diferente para presentar las ofertas.

   >[!NOTE]
   >
   >Se habla del canal y no del espacio. Si la regla excluye una oferta del canal web, la oferta a presentar en un sitio web, en dos espacios (por ejemplo, en un banner y en el cuerpo de la página), no se visualiza en el sitio si ya se ha presentado antes.
   >
   >For a workflow involving offer presentation, the rules are only correctly taken into account if they are configured on **[!UICONTROL All channels]**.

* **Filtro en la oferta**

   Este filtro permite restringir las propuestas de ofertas que se cuentan como determinados conjuntos de ofertas.

   **[!UICONTROL All offers]** :: valor predeterminado. No se aplica ningún filtro a las ofertas.

   **[!UICONTROL Offer being presented]** :: la oferta especificada en la **[!UICONTROL General]** ficha se excluye si ya se ha presentado.

   **[!UICONTROL Offers from the same category]** :: una oferta se excluye si ya se ha presentado una oferta de la misma categoría.

   **[!UICONTROL The offers which the rule applies to]** :: cuando se definen varias ofertas en la **[!UICONTROL General]** ficha, se tiene en cuenta cada propuesta de oferta de este conjunto de ofertas y finaliza con la exclusión de todas las ofertas si se alcanza el umbral de propuesta.

   For instance, offers 2, 3 and 5 are defined in the **[!UICONTROL General]** tab. El número máximo de propuestas se establece en 2. Si las ofertas 2 y 5 se presentan una vez, el número de propuestas contadas será 2. Como resultado, la oferta 3 nunca se presenta.

* **Filtro en el estado de la propuesta**

   Este filtro le permite elegir los estados más frecuentes para que la propuesta de ofertas sea tomada en cuenta en el historial de propuestas.

   **[!UICONTROL Regardless of the proposition status]** :: valor predeterminado. No se aplica ningún filtro al estado de la propuesta.

   **[!UICONTROL Accepted or rejected propositions]** :: permite excluir las ofertas presentadas anteriormente que se hayan aceptado o rechazado.

   **[!UICONTROL Accepted propositions]** :: permite excluir las ofertas presentadas anteriormente que se hayan aceptado.

   **[!UICONTROL Rejected propositions]** :: permite excluir las ofertas presentadas anteriormente que se hayan rechazado.

### Definición de destinatarios {#defining-recipients}

To specify the recipients, click the **[!UICONTROL Edit the query from the targeting dimension...]** link and select the recipients concerned by the rule.

![](assets/offer_typology_012.png)

### Creación de una consulta en propuestas {#creating-a-query-on-propositions}

To specify the propositions to be counted via a query, click the **[!UICONTROL Limit propositions...]** link and specify the criteria to be taken into account.

En el ejemplo siguiente, las propuestas que se van a contar después de dos presentaciones son las de la categoría **Ofertas especiales**, para el espacio del **centro de llamadas**, con un peso inferior a **20**.

![](assets/offer_typology_013.png)

