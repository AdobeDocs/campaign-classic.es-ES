---
title: Seguimiento técnico
seo-title: Seguimiento técnico
description: Seguimiento técnico
seo-description: null
page-status-flag: never-activated
uuid: 44ac7cf0-1d44-4656-b137-f3008be32e1d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 008d6a63-68cd-4e87-8adb-9642e2f9bb2a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 38700b79aeb19c75d10d2f5eb60c1efdb12e62e3

---


# Seguimiento técnico{#technical-monitoring}

## Informe de supervisión de la capacidad de entrega técnica {#technical-deliverability-monitoring}

El informe de supervisión técnica de la capacidad de entrega se actualiza diariamente y está disponible. Para ello, vaya a **[!UICONTROL Monitoring]** > **[!UICONTROL Overview]** y haga clic en el **[!UICONTROL Technical monitoring]** vínculo de la ficha Adobe Campaign **[!UICONTROL Home]** . Incluye una serie de indicadores de calidad de envío para su plataforma.

Estos indicadores se actualizan diariamente a las 9 a. m.

>[!NOTE]
>
>Además, puede recibir un informe diario por correo electrónico en una dirección específica. Infórmenos de la dirección de correo electrónico solicitada por correo electrónico o a través de la Extranet de Adobe Campaign.

![](assets/s_tn_del_monitoring.png)

En el informe se usan los siguientes indicadores:

* **[!UICONTROL Reverse DNS]** : Adobe Campaign comprueba si se ha proporcionado un DNS inverso para una dirección IP y que este señala correctamente a la dirección IP.

* **[!UICONTROL SPF]** (Marco de política del remitente): Mecanismo de autenticación que permite a los ISP y proveedores de buzones de correo comprobar si el remitente del correo electrónico está autorizado en el dominio de envío.

   <!--
    >[!NOTE]
    >
    >The SPF may look **[!UICONTROL Acceptable]** (instead of **[!UICONTROL Good]**) since the report is currently unable to detect the presence of a “redirect” or “include” mechanism. This bug has been submitted to Adobe Campaign R&D to be fixed. In the meantime, please feel free to add 15 points to your global score to obtain your real rating (a **[!UICONTROL Good]** one corresponds to 96 points or higher).
    -->

* **[!UICONTROL DomainKeys]** : Servicio desarrollado por Yahoo! y pensado para certificar la identidad de un remitente de correo electrónico.

* **[!UICONTROL IP and RBL domain]** (Lista negra en tiempo real): Una lista de direcciones IP y dominios que han sido marcados por organizaciones de listas de bloqueo por mala reputación de envío. Estas listas son mantenidas por organizaciones especializadas como Spamhaus, Spampoli, SURBL/URIBL, etc. Adobe Campaign procesa actualmente comprobaciones con RBL que tienen un impacto significativo en la entrega. Estos RBL reflejan la reputación de envío y pueden ser referenciados por los ISP antes de aceptar recibir sus correos electrónicos.

* **[!UICONTROL SNDS]** (Servicios de datos de redes inteligentes): Un servicio [](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx)antispam de Windows Live Hotmail. Hotmail es el único ISP que proporciona este tipo de información. Las puntuaciones comparativas son un resultado de filtro verde, una tasa de quejas de menos del 0,1% y cero trampas no deseadas.

<!--
* **[!UICONTROL Reputation Authority]**: This WatchGuard’s score is calculated in real time according to the feedback received from their network worldwide, and also from the different users who use their software.

    Administrators can use such tools to apply a first level filter on their messaging servers.
    If you click on the IP link within the technical report, it will lead you to reputationauthority.org, where you will have the possibility to clean the IP history and get a neutral score again.
    Nevertheless, this action is limited to a number of times per month.
    Please also be aware there is no support provided by WatchGuard‘s Reputation Authority (sending delisting requests is therefore useless). Otherwise, this scoring is based on the following: 
    * Message content (for example: presence of spam words). 
    * IP/Domains reputation (for example: your IPs are listed on an RBL). 
    * IP configuration (for example: IPs associated to different domains). 
    * Volumes sent by IP (for example: presence of peaks or significant variations).
    
    * **[!UICONTROL Sender Score]** : A database of reputed servers ([https://www.senderscore.org/](https://www.senderscore.org/)) issuing a score created by Return Path about your reputation. Think of it like a credit score, but for email senders.-->

<!--## Delivery Reports - Broadcast Statistics {#delivery-reports-broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability:

![](assets/s_tn_del_monitoring.png)-->
