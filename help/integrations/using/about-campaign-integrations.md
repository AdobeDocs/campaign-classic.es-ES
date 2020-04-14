---
title: Acerca de las integraciones de Campaign
description: Obtenga información sobre las integraciones funcionales disponibles entre la versión actual de Adobe Campaign y las soluciones de Adobe Experience Cloud.
page-status-flag: never-activated
uuid: 087abdf0-b4b2-45e6-be21-b03bf85ddf83
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: campaign-integrations
discoiquuid: 0af1fd96-48ef-43c9-a03b-0f9a6e0e02fe
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0a4272ae13b469c7c17b8c3afa9748cbfbcf07ff

---


# Acerca de las integraciones de Campaign {#about-campaign-integrations}

Adobe Experience Cloud es un conjunto completo de soluciones integradas óptimas en una plataforma de datos común con un conjunto de servicios principales potentes.

Learn about functional integrations available between Adobe Campaign and [Adobe Experience Cloud solutions](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) and [core services](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html). A continuación, puede modernizar las implementaciones de soluciones e implementar Experience Cloud para que pueda utilizar funciones como atributos y audiencias del cliente.

The full list of Adobe solutions and core services which can be integrated with Adobe Campaign, as well as associated documentation, is available in [this section](#experience-cloud-integrations).

![](assets/ExCloud-solutions.png)


>[!CAUTION]
>
>La mayoría de estas integraciones requieren que inicie sesión con un Adobe ID (IMS). Para obtener más información sobre esta implementación, consulte [esta página](../../integrations/using/about-adobe-id.md).
>
>Tenga en cuenta que la implementación de IMS es un proceso complejo, que puede ser largo. Está estrictamente reservado para los administradores técnicos de Adobe.

## Vinculación de soluciones {#working-with-experience-cloud-solutions}

Según el entorno, varias soluciones se pueden vincular con Adobe Experience Cloud. Estas se vinculan como organizaciones. Una **organización** es la entidad que permite a un administrador configurar grupos y usuarios y controlar el inicio de sesión único en Experience Cloud. La organización funciona como una empresa de inicio de sesión que abarca todos los productos y soluciones de Experience Cloud. Generalmente, la organización es el nombre de la empresa. Sin embargo, una empresa puede tener muchas organizaciones.

Se detalla la administración de la organización y los vínculos de las cuentas de Adobe Experience Cloud en el [portal de ayuda de Adobe Experience Cloud](https://marketing.adobe.com/resources/help/es_ES/mcloud/organizations.html).

>[!CAUTION]
>
>Cuando se instala Adobe Campaign o se integra una instalación existente con Adobe Experience Cloud, se activa el [servicio de Experience Cloud ID. ](https://marketing.adobe.com/resources/help/es_ES/mcvid/) Este servicio reemplaza la cookie permanente que utiliza principalmente Adobe Campaign para las funciones de seguimiento.
>
>A continuación, se asigna una ID de visitante única a los destinatarios que generen “logs” de seguimiento. This ID will be saved in the **[!UICONTROL Requester UUID (@sourceID)]** field of the **[!UICONTROL nms:trackingLogRcp]** table. Por lo tanto, ya no se pueden utilizar los datos de seguimiento de los destinatarios existentes antes de implementar el servicio de ID de visitante.
>
>Las otras soluciones de Adobe Experience Cloud reconocen entonces la ID con el mismo [CNAME](https://marketing.adobe.com/resources/help/es_ES/mcvid/mcvid_cname.html).

## Integraciones de Experience Cloud {#experience-cloud-integrations}

La siguiente tabla permite acceder a la documentación de integración de Experience Cloud disponible.

<table> 
 <thead> 
  <tr> 
   <th> Servicios principales y de soluciones<br /> </th> 
   <th> Ejemplos de uso<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Plataforma de datos de clientes en tiempo real de Adobe</strong><br /> </td> 
   <td> La integración entre Adobe Campaign y la plataforma de datos del cliente en tiempo real de Adobe le permite compartir datos de segmentos e importar audiencias a Adobe Campaign.<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">Obtenga más información</a> sobre Campaign: integración de la plataforma de datos del cliente en tiempo real de Adobe.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>IMS - Adobe ID</strong><br /> </td> 
   <td> Permite conectarse a Adobe Campaign con la misma Adobe ID que para las otras soluciones de Adobe Experience Cloud.<br /> Se debe utilizar una Adobe ID para iniciar sesión con el objetivo de utilizar ciertas funcionalidades vinculadas a las integraciones de Adobe Experience Cloud, especialmente los servicios principales.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Obtenga más información</a> sobre la implementación de la Adobe ID con Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Permite crear contenido de correo electrónico o formularios asignados a la base de datos de Adobe Campaign directamente en <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Obtenga más información</a> sobre la integración de Adobe Campaign con Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Permite insertar imágenes que <strong>Adobe Target</strong> calcula dinámicamente cuando se abre el correo electrónico que Adobe Campaign crea y envía.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Obtenga más información</a> sobre la integración de Adobe Campaign con Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Servicio principal Personas</strong><br /> <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Permite compartir audiencias entre las soluciones de Adobe Experience Cloud y el servicio principal que utiliza.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Obtenga más información</a> sobre Adobe Campaign: integraciones del servicio principal Personas y Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Servicio principal de activos</strong><br /> </td> 
   <td> Permite insertar activos de la biblioteca de Adobe Experience Cloud en correos electrónicos y páginas de destino creadas en Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Obtenga más información</a> sobre la integración de Adobe Campaign con el servicio principal de activos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Permite insertar activos de la biblioteca de <strong>AEM Assets</strong> en correos electrónicos y páginas de destino creadas en Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Obtenga más información</a> sobre la integración de Adobe Campaign con AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Activadores de Experience Cloud</strong><br /> </td> 
   <td> La integración entre <strong>el servicio principal de activadores</strong> y Adobe Campaign permite enviar mensajes de correo electrónico personalizados a sus clientes como una reacción ante comportamientos específicos rastreados en el sitio web mediante Adobe Analytics.<br /> <p><a href="https://helpx.adobe.com/es/campaign/kb/triggers-and-campaign.html">Obtenga más información</a> sobre la integración de Adobe Campaign con los activadores de Experience Cloud.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics: Conectores de datos</strong><br /> </td> 
   <td> <strong>Conectores de datos</strong> (anteriormente conocidos como Adobe Genesis) permite que Adobe Campaign y Adobe Analytics interactúen mediante segmentos en relación con el comportamiento del usuario tras una campaña de correos electrónicos. Por el contrario, envía indicadores y atributos de las campañas de correo electrónico que envía Adobe Campaign a Adobe Analytics: conector de datos.<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">Obtenga más información</a> sobre la integración de Campaign con los conectores de datos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Campaign Standard</strong> (oferta Prime)<br /> </td> 
   <td> Permite replicar datos en <strong>Campaign Standard</strong>, uniendo lo mejor de ambas aplicaciones. Campaign Classic v7 cuenta con herramientas avanzadas para administrar la base de datos principal de marketing. La duplicación de datos de Campign Classic v7 permite a Campaign Standard aprovechar los datos enriquecidos en un entorno fácil de usar.<br /><p> <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">Obtenga más información</a> sobre la integración de Adobe Campaign Classic - Adobe Campaign Standard.</p><br /></td> 
  </tr> 
 </tbody> 
</table>

