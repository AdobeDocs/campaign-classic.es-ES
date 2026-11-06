---
keywords: Campaign Classic;inicio;temas populares
product: campaign
title: Documentación del producto de Adobe Campaign Classic v7
exl-id: 6b3f1689-80de-49fd-b7ee-7a2a1931d157
TQID: 'https://experienceleague.adobe.com/Q6Oc24mo-1qDAxCWu2lGT4UvRLXB78Tr5X4sb2kHFw8'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
    internal-label: APIs
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: fbeb3bb6f89cd0b03d1fb4551496f96eda0cbf10
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 41%
---
# Documentación de Campaign Classic v7 {#campaign-classic-documentation}

Esta documentación cubre Campaign Classic v7 para **implementaciones locales e híbridas**: instalación, configuración, actualizaciones, operaciones y las funciones específicas de v7. Si su instancia está alojada en Adobe (Managed Cloud Services), consulte la [Documentación de Campaign v8](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/campaign-home){target="_blank"}. El contenido que documenta Campaign v8 de la misma manera ya no se duplica aquí: consulte [De la v7 a la v8](#from-v7-to-v8).

<!--![](platform/using/assets/do-not-localize/banner_acc_doc.jpg) -->

## Novedades

Echa un vistazo a las mejoras más recientes del producto y la documentación de la versión 7 de Adobe Campaign Classic. Para obtener una lista completa de funciones, mejoras y correcciones, consulte las [Notas de la versión](rn/using/latest-release.md) detalladas.

>[!BEGINTABS]


>[!TAB ¡La versión de octubre de 2026 está activa!]

La versión 7.4.5 de Campaign Classic de octubre de 2026 (compilación 9420) ofrece correcciones para la cuenta externa de Analytics, los envíos atascados en el estado pendiente de personalización, el uso de CPU del servidor, los errores intermitentes de actualización del modelo de datos, el error de comprobación de correo no deseado en la creación de envíos y la cuarentena de los rechazos leves recurrentes.

[![imagen](assets/do-not-localize/learn-more-button.svg)](rn/using/latest-release.md)

>[!TAB Pasarse a Adobe IMS]

Para reforzar la seguridad y el proceso de autenticación, Adobe Campaign recomienda migrar el modo de autenticación del usuario final de la autenticación nativa de inicio de sesión/contraseña al sistema de administración de identidades (IMS) de Adobe.

[![imagen](assets/do-not-localize/learn-more-button.svg)](technotes/using/ac-ims.md)


>[!ENDTABS]

## Empieza con los conceptos básicos

<table style="table-layout:fixed">
  <tr style="border: 0;">
    <td>
    <a href="platform/using/launching-adobe-campaign.md"><img src="assets/do-not-localize/start-launch.png"></a></a>
    <div><strong>Iniciar Adobe Campaign</strong><br/> Obtenga información sobre cómo iniciar la consola del cliente de Campaign y conectarse a los servidores de aplicaciones de Campaign.</div>
    </td>
    <td>
    <a href="platform/using/about-profiles.md"><img src="assets/do-not-localize/start-profiles.png"></a>
    <div><strong>Adición y administración de perfiles</strong><br/> Explora fácilmente la administración de perfiles en la base de datos de la versión 7 de Adobe Campaign. Añade perfiles manualmente o importándolos para refinar los datos de los clientes y personalizar las campañas sin complicaciones.</div>
    </td>
    <td>
    <a href="https://experienceleague.adobe.com/es/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank"><img src="assets/do-not-localize/start-workflows.jpeg"></a>
    <div><strong>Automatización con flujos de trabajo</strong><br/> Aprende a aprovechar el flujo de trabajo para crear procesos, incluyendo, entre otros, segmentación, ejecución de campañas, procesamiento de archivos y participación humana.
    </div></td>
    <td>
    <a href="delivery/using/communication-channels.md"><img src="assets/do-not-localize/start-deliveries.jpeg"></a>
    <div><strong>Creación de envíos</strong><br/> Aprende a enviar mensajes a través de varios canales, como correo electrónico, SMS, notificaciones push, etc.</div>
    </td>
  </tr>
  <tr style="border: 0;">
    <td align="center"><a href="platform/using/launching-adobe-campaign.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="platform/using/about-profiles.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="https://experienceleague.adobe.com/es/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="delivery/using/communication-channels.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    </tr>
</table>

## Explora la documentación

<table style="table-layout:auto">
  <tr style="border: 0;">
    <td>
      <img src="assets/do-not-localize/icon-configure.svg" width="35px">
      <br/>
      <strong>Administradores</strong><br/><a href="production/using/architecture-and-open-ports.md">Principios de arquitectura</a> - <a href="production/using/syslogd-port-and-security-zones.md">Configurar Campaign</a> - <a href="platform/using/launching-adobe-campaign.md">Conectarse a Campaign</a> - <a href="installation/using/external-accounts.md">Conectarse a sistemas externos</a> - <a href="platform/using/access-management.md">Permisos</a> - <a href="platform/using/privacy-management.md">Privacidad y consentimiento</a> - <a href="production/using/build-upgrade.md">Realizando una actualización de compilación</a> - <a href="delivery/using/about-deliverability.md">Capacidad de entrega</a>
    </td>
    <td>
      <img src="assets/do-not-localize/icon-send.svg" width="35px">
      <br/>
      <strong>Especialistas en marketing</strong><br/><a href="https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/new/campaign-ui" target="_blank">Interfaz de usuario</a> (documentación de Campaign v8) - <a href="https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/data/import" target="_blank">Importar y exportar datos</a> (documentación de Campaign v8) - <a href="https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/audience/create-audiences/create-audiences" target="_blank">Crear listas</a> (documentación de Campaign v8) - <a href="delivery/using/about-services-and-subscriptions.md">Servicios y suscripciones</a> - <a href="delivery/using/communication-channels.md">Canales de comunicación</a> - <a href="delivery/using/about-personalization.md">Personalization</a> - <a href="https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/send/create-message" target="_blank">Enviar pruebas</a> (documentación de Campaign v8) - <a href="delivery/using/get-started-a-b-testing.md">Pruebas A/B</a> - <a href="message-center/using/about-transactional-messaging.md">Transaccional mensajería</a> - <a href="interaction/using/interaction-and-offer-management.md">Interacción y administración de ofertas</a> - <a href="https://experienceleague.adobe.com/es/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank">Automatización con flujos de trabajo</a> (documentación de Campaign v8) - <a href="https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=es" target="_blank">Campaña de marketing</a> - <a href="https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/analytics/tracking/tracking" target="_blank">Seguimiento de mensajes</a> (documentación de Campaign v8) - <a href="https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/analytics/reports/gs-reporting" target="_blank">Creación de informes</a> (documentación de Campaign v8)
    </td>
    <td>
      <img src="assets/do-not-localize/icon-dev.svg" width="35px">
      <br/>
      <strong>Desarrolladores</strong><br/><a href="https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/developer/datamodel" target="_blank">Descripción del modelo de datos</a> (documentación de Campaign v8) - <a href="configuration/using/about-schema-reference.md">Estructura del esquema</a> - <a href="configuration/using/editing-forms.md">Formularios de entrada</a> - <a href="configuration/using/about-web-services.md">API</a> - <a href="https://experienceleague.adobe.com/es/tools/campaign-api" target="_blank">Documentación de referencia de JSAPI</a> - <a href="configuration/using/about-custom-recipient-table.md">Tabla de destinatarios personalizada</a>
    </td>
  </tr>
</table>

## De la versión 7 a la versión 8 {#from-v7-to-v8}

El contenido que se documenta en la documentación de Campaign v8 se ha eliminado de la documentación de Campaign v7. Utilice esta tabla para encontrarla.

| Si usted está buscando... | Vaya a la documentación de Campaign v8 |
| --- | --- |
| La interfaz de usuario | [Descubra la interfaz de usuario](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/new/campaign-ui){target="_blank"} |
| Perfiles, listas, importación y exportación | [Importar perfiles y datos](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/data/import){target="_blank"} |
| Flujos de trabajo | [Acerca de los flujos de trabajo](https://experienceleague.adobe.com/es/docs/campaign/automation/workflows/introduction/about-workflows){target="_blank"} |
| Campañas de marketing | [Introducción a las campañas de marketing](https://experienceleague.adobe.com/es/docs/campaign/automation/campaign-orchestration/set-up-campaigns){target="_blank"} |
| Creación y entrega de envíos | [Crear un mensaje](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/send/create-message){target="_blank"} |
| Informes integrados | [Introducción a los informes](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/analytics/reports/gs-reporting){target="_blank"} |
| Permisos | [Introducción a los permisos](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/permissions/gs-permissions){target="_blank"} |
| Formularios de entrada | [Introducción a los formularios de entrada](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/developer/schemas-forms/forms){target="_blank"} |

## Recursos adicionales

[Descripción del producto Adobe Campaign](https://helpx.adobe.com/es/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"} - [Matriz de compatibilidad](rn/using/compatibility-matrix.md) - [Tutoriales](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=es){target="_blank"} - [Panel de control de Campaign](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=es){target="_blank"} - [Píxeles de seguimiento de correo electrónico y Guía de la CNIL](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/new/cnil-pixel-tracking){target="_blank"}
