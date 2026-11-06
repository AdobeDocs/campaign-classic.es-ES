---
product: campaign
title: Procesamiento de la bandeja de entrada en Campaign
description: Obtenga información sobre cómo capturar las representaciones de correo electrónico y ponerlas a disposición en un informe dedicado
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Inbox Rendering, Monitoring, Email Rendering
role: User
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
TQID: 'https://experienceleague.adobe.com/d0fFXi4Ma-PwY8vsSBOmvbhRD4631kUoagNXlf4Rmek'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: 2317b1ea-6db4-58c7-851f-717a69c0f5c0
    internal-label: Inbox Rendering
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
  - id: aef0b685-fc31-54d4-b831-a87fdb9d69de
    internal-label: Email Rendering
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: cce1f22c34cbd13d063850a7ca636a3b0dfc62f6
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 81%
---
# Representación de la bandeja de entrada{#inbox-rendering}

Adobe Campaign aprovecha la solución de prueba de correo electrónico basada en web [Litmus](https://litmus.com/email-testing) para capturar las renderizaciones de correo electrónico y ponerlas a disposición en un informe específico.

Como parte del proceso de transición de la versión 7 a 8 de Campaign, toda la documentación de Campaign Classic se ha optimizado y reorganizado. Ahora, las funciones comunes solo están disponibles en el conjunto de documentación de Campaign v8. Para obtener más información sobre la renderización de la bandeja de entrada, consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/deliverability-management/inbox-rendering){target=_blank}.

[![imagen](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/deliverability-management/inbox-rendering){target=_blank}

## Activación del renderizado de la bandeja de entrada {#activating-inbox-rendering}

[!BADGE On-Premise e híbrido]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"}

Para los clientes alojados e híbridos, el servicio de asistencia técnica y consultores de Adobe configuran la renderización de la Bandeja de entrada en la instancia. Para obtener más información, póngase en contacto con su administrador de cuentas de Adobe.

Para las instalaciones in situ, siga los pasos a continuación para configurar la renderización de la Bandeja de entrada.

1. Mediante el menú **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**, instale el paquete **[!UICONTROL Inbox rendering (IR)]**. Para obtener más información, consulte [Instalación de paquetes estándar de Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).
1. Configure una cuenta externa del tipo HTTP mediante el nodo **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**. Para obtener más información, consulte [Creación de una cuenta externa](../../installation/using/external-accounts.md#creating-an-external-account).
1. Defina los parámetros de cuenta externa de la siguiente manera:
   * **[!UICONTROL Label]**: Información del servidor de envío
   * **[!UICONTROL Internal name]**: deliverabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**: https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**: Ninguno
   * Marque la opción **[!UICONTROL Enabled]**.

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. Vaya al nodo **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. Busque la opción **[!UICONTROL DmRendering_cuid]** y póngase en contacto con el servicio de soporte técnico para obtener el identificador de los informes de envío que debe copiarse en el campo **[!UICONTROL Value (text)]**.
1. Edite el archivo **serverConf.xml** para permitir una llamada al servidor Litmus. Añada la siguiente línea a la sección `<urlPermission>`:

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. Vuelva a cargar la configuración con el siguiente comando:

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>Es posible que tenga que cerrar la sesión desde la consola y volver a iniciarla para poder utilizar la renderización de la Bandeja de entrada.
