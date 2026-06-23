---
product: campaign
title: Acerca de las integraciones de Campaign
description: Utilice otras soluciones de Adobe y combine sus diferentes capacidades con Campaign
feature: Overview
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
TQID: https://experienceleague.adobe.com/PUFoWjnwax8oHM3dH-FJDH7b26p4qNBMaJfm2qWGNz0
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 740
ht-degree: 100%

---

# Introducción a las integraciones de Adobe Campaign {#about-campaign-integrations}

Adobe Experience Cloud es un conjunto completo de las mejores soluciones integradas en una plataforma de datos común con un conjunto común de potentes soluciones y aplicaciones.

Obtenga más información sobre las integraciones funcionales disponibles entre las soluciones de Adobe Campaign y de Adobe Experience Cloud en [esta página](https://experienceleague.adobe.com/es/docs/core-services/interface/administration/integrations){_blank}.

La lista completa de soluciones y servicios de aplicaciones de Adobe que se pueden integrar con Adobe Campaign, así como la documentación asociada, está disponible en [esta sección](#experience-cloud-integrations).

>[!CAUTION]
>
>Estas integraciones requieren implementar Adobe Identity Management System (IMS) para iniciar sesión con un Adobe ID. [Obtenga más información en esta página](../../integrations/using/about-adobe-id.md).
>

## Vinculación de soluciones {#working-with-experience-cloud-solutions}

Se pueden vincular varias soluciones a Adobe Experience Cloud. La **organización** es la entidad del cliente que permite a un administrador configurar grupos y usuarios y controlar el inicio de sesión único (SSO) en Adobe Experience Cloud. La organización funciona como una empresa de inicio de sesión que abarca todos los productos y soluciones de Experience Cloud. Generalmente, la organización es el nombre de la empresa. Sin embargo, una empresa puede tener muchas organizaciones.

Se detalla la administración de la organización y los vínculos de las cuentas de Adobe Experience Cloud en el [portal de ayuda de Adobe Experience Cloud](https://experienceleague.adobe.com/es/docs/core-services/interface/administration/organizations){_blank}.

## Administración de cookies e identidades {#id-and-cookies}

Cuando se instala Adobe Campaign o se integra una instalación existente con Adobe Experience Cloud, se habilita el [Servicio de identidad de Adobe Experience Cloud](https://experienceleague.adobe.com/es/docs/id-service/using/home){_blank}. Este servicio reemplaza la cookie permanente que utiliza principalmente Adobe Campaign para las funciones de seguimiento.

El Servicio de identidad de Adobe Experience Cloud (servicio de ID) proporciona un ID universal y persistente que identifica sus visitantes en todas las soluciones de Experience Cloud.

Se asigna un ID de visitante único a los destinatarios que generen registros de seguimiento. Esta ID se guarda en el campo **[!UICONTROL Requester UUID (@sourceID)]** de la tabla **[!UICONTROL nms:trackingLogRcp]**. **Por lo tanto, ya no se pueden utilizar los datos de seguimiento de los destinatarios existentes antes de implementar el servicio de ID de visitante**.

Las otras soluciones de Adobe Experience Cloud reconocen, por consiguiente, el ID con el mismo CNAME. [Más información](https://experienceleague.adobe.com/es/docs/id-service/using/reference/analytics-reference/cname){_blank}.

## Integraciones de Experience Cloud {#experience-cloud-integrations}

La siguiente tabla permite acceder a la documentación de integración de Experience Cloud disponible.

<table> 
 <thead> 
  <tr> 
   <th> Soluciones y aplicaciones<br /> </th> 
   <th> Ejemplos de uso<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Plataforma de datos de clientes en tiempo real de Adobe (RTCDP)</strong><br /> </td> 
   <td> Configure la integración entre Adobe Campaign y Adobe Real-time Customer Data Platform (RTCDP) para compartir datos de segmentos e importar públicos a Adobe Campaign.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">Obtenga más información</a> sobre Campaign: integración de la plataforma de datos del cliente en tiempo real de Adobe.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management System (IMS), Adobe ID</strong><br /> </td> 
   <td>Configure Adobe IMS para conectarse a Adobe Campaign con el mismo Adobe ID que para las demás soluciones de Adobe Experience Cloud.<br /> Debe utilizar un Adobe ID para iniciar sesión con el objetivo de utilizar determinadas funcionalidades vinculadas a las integraciones de Adobe Experience Cloud.<br /><p><a href="../../integrations/using/about-adobe-id.md">Obtenga más información</a> sobre la implementación de la Adobe ID con Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Configure esta integración para crear contenido de correo electrónico o formularios asignados a la base de datos de Adobe Campaign directamente en <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Obtenga más información</a> sobre la integración de Adobe Campaign con Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Configure esta integración para insertar imágenes que <strong>Adobe Target</strong> calcula dinámicamente cuando se abre el correo electrónico que Adobe Campaign crea y envía<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Obtenga más información</a> sobre la integración de Adobe Campaign con Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Configure esta integración para compartir públicos entre las soluciones de Adobe Experience Cloud y las aplicaciones que utilice.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Obtenga más información</a> sobre las integraciones de Adobe Campaign y Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Recursos</strong><br /> </td> 
   <td> Configure esta integración para insertar recursos de la biblioteca de Adobe Experience Cloud en correos electrónicos y páginas de destino creados en Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Más información</a> sobre la integración de Adobe Campaign y Assets</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Configure esta integración para insertar recursos de su biblioteca de <strong>AEM Assets</strong> en correos electrónicos y páginas de destino creados en Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Obtenga más información</a> sobre la integración de Adobe Campaign con AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Activadores de Experience Cloud</strong><br /> </td> 
   <td> Configure la integración entre los <strong>Activadores de Adobe Experience Cloud</strong> y Adobe Campaign para enviar mensajes de correo electrónico personalizados a sus clientes como reacción ante comportamientos específicos que se rastrean en el sitio web de Adobe Analytics.<br /> <p><a href="about-triggers.md">Obtenga más información</a> sobre la integración de Adobe Campaign con los activadores de Experience Cloud.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Conector de Adobe Analytics</strong><br /> </td> 
   <td> Configure esta integración para que Adobe Campaign y Adobe Analytics puedan interactuar mediante segmentos en relación con el comportamiento del usuario tras una campaña de correo electrónico. A la inversa, envía indicadores y atributos de las campañas de correo electrónico que envía Adobe Campaign a Adobe Analytics.<br /> <p><a href="../../integrations/using/gs-aa.md">Obtenga más información</a> acerca de la integración de conectores Campaign - Analytics.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
