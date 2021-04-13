---
solution: Campaign Classic
product: campaign
title: Acerca de las integraciones de Campaign
description: Utilice otras soluciones de Adobe y combine sus diferentes capacidades con Campaign.
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
translation-type: tm+mt
source-git-commit: 326ccbad77f3bd03a8eba22d7714084d52d2f02b
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 100%

---

# Introducción a las integraciones de Adobe Campaign {#about-campaign-integrations}

Adobe Experience Cloud es un conjunto completo de las mejores soluciones integradas en una plataforma de datos común con un conjunto de servicios principales potentes.

Obtenga información sobre las integraciones funcionales disponibles entre Adobe Campaign y [Soluciones Adobe Experience Cloud](https://docs.adobe.com/content/help/es-ES/core-services/interface/marketing-cloud-integrations.html) y [servicios principales](https://docs.adobe.com/content/help/es-ES/core-services/interface/about-core-services/core-services.html). Puede modernizar las implementaciones de soluciones e implementar Experience Cloud para que pueda utilizar funciones como atributos y audiencias del cliente.

![](assets/ExCloud-solutions.png)

Descubra la lista completa de soluciones de Adobe y los servicios principales que se pueden integrar con Adobe Campaign, así como la documentación asociada, en [esta sección](#experience-cloud-integrations).

>[!CAUTION]
>
>La mayoría de estas integraciones requieren implementar Adobe Identity Management System (IMS) para iniciar sesión con Adobe ID. [Obtenga más información en esta página](../../integrations/using/about-adobe-id.md).


## Vinculación de soluciones {#working-with-experience-cloud-solutions}

Se pueden vincular varias soluciones a Adobe Experience Cloud. La **organización** es la entidad del cliente que permite a un administrador configurar grupos y usuarios y controlar el inicio de sesión único (SSO) en Adobe Experience Cloud. La organización funciona como una empresa de inicio de sesión que abarca todos los productos y soluciones de Experience Cloud. Generalmente, la organización es el nombre de la empresa. Sin embargo, una empresa puede tener muchas organizaciones.

Se detalla la administración de la organización y los vínculos de las cuentas de Adobe Experience Cloud en el [portal de ayuda de Adobe Experience Cloud](https://docs.adobe.com/content/help/es-ES/core-services/interface/manage-users-and-products/organizations.html).

## Administración de cookies e identidades {#id-and-cookies}

Cuando se instala Adobe Campaign o se integra una instalación existente con Adobe Experience Cloud, se activa el [Servicio de identidad de Adobe Experience Cloud](https://docs.adobe.com/content/help/es-ES/id-service/using/home.html). Este servicio reemplaza la cookie permanente que utiliza principalmente Adobe Campaign para las funciones de seguimiento.

El Servicio de identidad de Adobe Experience Cloud (servicio de ID) proporciona un ID universal y persistente que identifica sus visitantes en todas las soluciones de Experience Cloud.

Se asigna una ID único de visitante a los destinatarios que generen registros de seguimiento. Esta ID se guarda en el campo **[!UICONTROL Requester UUID (@sourceID)]** de la tabla **[!UICONTROL nms:trackingLogRcp]**. **Por lo tanto, ya no se pueden utilizar los datos de seguimiento de los destinatarios existentes antes de implementar el servicio de ID de visitante**.

Las otras soluciones de Adobe Experience Cloud reconocen entonces la ID con el mismo [CNAME](https://docs.adobe.com/content/help/es-ES/id-service/using/reference/analytics-reference/cname.html).

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
   <td> <strong>Plataforma de datos de clientes en tiempo real de Adobe (RTCDP)</strong><br /> </td> 
   <td> La integración entre Adobe Campaign y la plataforma de datos del cliente en tiempo real de Adobe (RTCDP) le permite compartir datos de segmentos e importar audiencias a Adobe Campaign.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">Obtenga más información</a> sobre Campaign: integración de la plataforma de datos del cliente en tiempo real de Adobe.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management System (IMS), Adobe ID</strong><br /> </td> 
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
 </tbody> 
</table>
