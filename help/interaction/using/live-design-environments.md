---
title: Entornos en directo/de diseño
seo-title: Entornos en directo/de diseño
description: Entornos en directo/de diseño
seo-description: null
page-status-flag: never-activated
uuid: 38ee2f6a-e446-4ac6-b962-40b648eeaf66
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 3cea2be4-4da4-4ebd-a241-1bbaa5abb16e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Entornos en directo/de diseño{#live-design-environments}

## Principio de funcionamiento {#operating-principle}

La interacción funciona con dos tipos de entornos de oferta:

* **[!UICONTROL Design]** ofrecen entornos que incluyen ofertas que se están editando y que se pueden modificar. Estas ofertas no han pasado a través del ciclo de aprobación y no se entregan a los contactos.
* **[!UICONTROL Live]** ofrecer entornos que incluyan ofertas aprobadas a medida que se presentan a los contactos. Las ofertas de este entorno son de solo lectura.

![](assets/offer_environments_overview_001.png)

Cada **[!UICONTROL Design]** entorno está vinculado a un **[!UICONTROL Live]** entorno. Cuando se completa una oferta, sus reglas de contenido y de idoneidad están sujetas a un ciclo de aprobación. Once this cycle is complete, the concerned offer is automatically deployed to the **[!UICONTROL Live]** environment. A partir de este momento, estará disponible para su envío.

By default, Interaction comes with a **[!UICONTROL Design]** environment and a **[!UICONTROL Live]** environment linked to it. Ambos entornos están preconfigurados para seleccionar la tabla de destinatarios predeterminada.

>[!NOTE]
>
>Para dirigirse a otra tabla (tabla de visitante para ofertas anónimas o una tabla de destinatarios específica), debe utilizar el asistente de asignación de destino para crear los entornos. Para obtener más información sobre esto, consulte [Creación de un entorno](#creating-an-offer-environment)de ofertas.

![](assets/offer_environments_overview_002.png)

Los gestores de oferta y los gestores de envío tienen acceso a diferentes vistas del entorno. Delivery managers can only view the **[!UICONTROL Live]** offer environment and use offers to deliver them. Offer managers can view and alter the **[!UICONTROL Design]** environment and view the **[!UICONTROL Live]** environment. For more on this, refer to [Operator profiles](../../interaction/using/operator-profiles.md).

## Creación de un entorno de oferta {#creating-an-offer-environment}

De forma predeterminada, la interacción viene con un entorno preconfigurado para dirigirse la tabla de destinatarios (ofertas identificadas). Si desea dirigirse a otra tabla (tabla de visitante para ofertas anónimas o a una tabla de destinatarios específica), debe aplicar las siguientes configuraciones:

1. Sitúe el cursor en el nodo **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]** . Haga clic con el botón derecho en la asignación de entrega que desee utilizar (**[!UICONTROL Visitors]** si desea utilizar ofertas anónimas) y seleccione **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. Haga clic en **[!UICONTROL Next]** para pasar a la siguiente pantalla del asistente, marque la **[!UICONTROL Generate a storage schema for propositions]** casilla y haga clic en **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Si el casilla ya está marcada, quite la marca y vuelva a seleccionarla.

1. Adobe Campaign creates two environments (**[!UICONTROL Design]** and **[!UICONTROL Live]** ) with targeting information from the previously enabled target mapping. El entorno está preconfigurado con la información de objetivo.

   Si ha activado **[!UICONTROL Visitor]** la asignación, la **[!UICONTROL Environment dedicated to incoming anonymous interactions]** casilla se marca automáticamente en la **[!UICONTROL General]** ficha del entorno.

   Esta opción permite activar funciones específicas de interacción anónimas, especialmente al configurar espacios de oferta de entorno. También puede configurar opciones que le permiten cambiar de un entorno “identificado” a un entorno “anónimo”.

   Por ejemplo, puede vincular un entorno de destinatario con espacio de ofertas (contacto identificado) con un espacio de oferta que coincida con un entorno de visitante (contacto no identificado). De esta manera, se ponen a disposición del contacto distintas ofertas en función de si está, o no, identificado. Para obtener más información sobre esto, consulte [Creación de espacios](../../interaction/using/creating-offer-spaces.md)de ofertas.

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>For more information on anonymous interactions on an inbound channel, refer to [Anonymous interactions](../../interaction/using/anonymous-interactions.md).

