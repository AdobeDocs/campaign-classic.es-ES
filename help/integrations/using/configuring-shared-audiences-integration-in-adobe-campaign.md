---
title: Configuración de la integración de audiencias compartidas en Adobe Campaign
seo-title: Configuración de la integración de audiencias compartidas en Adobe Campaign
description: Configuración de la integración de audiencias compartidas en Adobe Campaign
seo-description: null
page-status-flag: never-activated
uuid: 6ed137e4-027f-4eb0-a0b5-4beb7deef51f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 4443b0ca-80c6-467d-a4df-50864aae8496
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 85%

---


# Configuración de la integración de audiencias compartidas en Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}

Una vez enviada esta solicitud, Adobe procede a ofrecer de la integración y a ponerse en contacto para proporcionar los detalles y la información necesaria para finalizar la configuración:

1. [Paso 1: Configuración o verificación de las cuentas externas en Adobe Campaign](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [Paso 2: Configuración de la fuente de datos](#step-2--configure-the-data-source)
1. [Paso 3: Configuración del servidor de seguimiento de campaña](#step-3--configure-campaign-tracking-server)
1. [Paso 4: Configuración del servicio de ID de visitante](#step-4--configure-the-visitor-id-service)

## Paso 1: Configuración o verificación de las cuentas externas en Adobe Campaign {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

En primer lugar, se deben configurar o verificar las cuentas externas en Adobe Campaign de la siguiente manera:

1. Haga clic en el icono **[!UICONTROL Explorer]**.
1. Vaya a **[!UICONTROL Administration > Platform > External accounts]**. Las cuentas SFTP mencionadas deberían estar ya configuradas por Adobe, y se le debe haber comunicado la información necesaria.

   * **[!UICONTROL importSharedAudience]** : Cuenta SFTP específica para la importación de audiencias.
   * **[!UICONTROL exportSharedAudience]** : Cuenta SFTP específica para la exportación de audiencias.

   ![](assets/aam_config_1.png)

1. Fill in the **[!UICONTROL Server]** field: **ftp-out.demdex.com** domain for the import external account and **ftp-in.demdex.com** domain for the export external account.

   Recuerde que una exportación de Campaign es una importación para Audience Manager o el servicio principal Personas.

   >[!NOTE]
   >
   >If you are using S3, enter your **[!UICONTROL AWS S3 Account Server]** following this syntax:
   >
   >`<S3bucket name>.s3.amazonaws.com/<s3object path>`
   >
   >Para obtener más información sobre cómo configurar la cuenta S3, consulte este [artículo](../../platform/using/external-accounts.md#amazon-simple-storage-service--s3--external-account).

   ![](assets/aam_config_2.png)

1. Añada el **[!UICONTROL Account]** y **[!UICONTROL Password]** proporcionado por el Adobe.

Las cuentas externas ya están configuradas.

## Paso 2: Configuración de la fuente de datos {#step-2--configure-the-data-source}

La **ID de destinatario - visitante** se crea dentro de Audience Manager. Constituye una fuente de datos de serie y configurada de forma predeterminada para la ID del visitante. Los segmentos creados con Campaign forman parte de esta fuente de datos.

To configure the **[!UICONTROL Recipient - Visitor ID]** data source:

1. From the **[!UICONTROL Explorer]** node, select **[!UICONTROL Administration > Platform > AMC Data sources]**.
1. Seleccione **[!UICONTROL Recipient - Visitor ID]**.
1. Introduzca el valor **[!UICONTROL Data Source ID]** y **[!UICONTROL AAM Destination ID]** proporcionado por Adobe.

   ![](assets/aam_config_3.png)

## Paso 3: Configuración del servidor de seguimiento de campaña {#step-3--configure-campaign-tracking-server}

Para la configuración de la integración con el servicio principal Personas o Audience Manager, también es necesario configurar el servidor de seguimiento de campañas.

Debe verificar que el servidor de seguimiento de Campaign esté registrado en el dominio (CNAME). Se puede encontrar más información sobre la delegación de nombres de dominio en [este artículo](https://helpx.adobe.com/es/campaign/kb/domain-name-delegation.html).

## Paso 4: Configuración del servicio de ID de visitante {#step-4--configure-the-visitor-id-service}

En caso de que el servicio de ID de visitante no se haya configurado en las propiedades web o sitios web, consulte el siguiente [documento](https://docs.adobe.com/content/help/en/id-service/using/implementation/setup-aam-analytics.html) o el siguiente [vídeo](https://helpx.adobe.com/marketing-cloud/how-to/email-marketing.html#step-two) para aprender a configurar el servicio.

La configuración y el suministro han finalizado, la integración ya puede utilizarse para importar y exportar audiencias o segmentos.
