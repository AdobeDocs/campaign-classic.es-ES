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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 86%

---


# Entornos en directo/de diseño{#live-design-environments}

## Principio de funcionamiento {#operating-principle}

La interacción funciona con dos tipos de entornos de oferta:

* Entornos de oferta **[!UICONTROL Design]** que incluyen ofertas que se están editando y pueden modificarse. Estas ofertas no han pasado a través del ciclo de aprobación y no se entregan a los contactos.
* Entornos de oferta **[!UICONTROL Live]** que incluyen ofertas aprobadas a medida que se presentan a los contactos. Las ofertas de este entorno son de solo lectura.

![](assets/offer_environments_overview_001.png)

Each **[!UICONTROL Design]** environment is linked to a **[!UICONTROL Live]** environment. Cuando se completa una oferta, sus reglas de contenido y de idoneidad están sujetas a un ciclo de aprobación. Una vez completado este ciclo, la oferta correspondiente se implementa automáticamente en el entorno **[!UICONTROL Live]**. A partir de este momento, estará disponible para su envío.

De forma predeterminada, la interacción viene con un entorno **[!UICONTROL Design]** y un entorno **[!UICONTROL Live]** relacionado con él. Ambos entornos están preconfigurados para seleccionar la tabla de destinatarios predeterminada.

>[!NOTE]
>
>Para dirigirse a otra tabla (tabla de visitante para ofertas anónimas o una tabla de destinatarios específica), debe utilizar el asistente de asignación de destino para crear los entornos. Para obtener más información, consulte [Creación de un entorno de ofertas](#creating-an-offer-environment).

![](assets/offer_environments_overview_002.png)

Los gestores de oferta y los gestores de envío tienen acceso a diferentes vistas del entorno. Los administradores de envío solo pueden ver el entorno de oferta **[!UICONTROL Live]** y utilizar ofertas para enviarlas. Los administradores de ofertas pueden ver y modificar el entorno **[!UICONTROL Design]** y ver el entorno **[!UICONTROL Live]**. Para obtener más información, consulte [Perfiles de operadores](../../interaction/using/operator-profiles.md).

## Creación de un entorno de oferta {#creating-an-offer-environment}

De forma predeterminada, la interacción viene con un entorno preconfigurado para dirigirse la tabla de destinatarios (ofertas identificadas). Si desea dirigirse a otra tabla (tabla de visitante para ofertas anónimas o a una tabla de destinatarios específica), debe aplicar las siguientes configuraciones:

1. Place your cursor on the **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]** node. Right-click the delivery mapping you want to use (**[!UICONTROL Visitors]** if you want to use anonymous offers) and select **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. Click **[!UICONTROL Next]** to proceed to the next screen in the wizard, check the **[!UICONTROL Generate a storage schema for propositions]** box and click **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Si la casilla ya está marcada, quite la marca y vuelva a seleccionarla.

1. Adobe Campaign crea dos entornos (**[!UICONTROL Design]** y **[!UICONTROL Live]**) con información de objetivo de la asignación de destino habilitada anteriormente. El entorno está preconfigurado con la información de objetivo.

   If you have activated **[!UICONTROL Visitor]** mapping, the **[!UICONTROL Environment dedicated to incoming anonymous interactions]** box is automatically checked in the environment&#39;s **[!UICONTROL General]** tab.

   Esta opción permite activar funciones específicas de interacción anónimas, especialmente al configurar espacios de oferta de entorno. También puede configurar opciones que le permiten cambiar de un entorno “identificado” a un entorno “anónimo”.

   Por ejemplo, puede vincular un entorno de destinatario con espacio de ofertas (contacto identificado) con un espacio de oferta que coincida con un entorno de visitante (contacto no identificado). De esta manera, se ponen a disposición del contacto distintas ofertas en función de si está, o no, identificado. Para obtener más información, consulte [Creación de espacios de ofertas](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>Para obtener más información sobre interacciones anónimas en un canal entrante, consulte [Interacciones anónimas](../../interaction/using/anonymous-interactions.md).

