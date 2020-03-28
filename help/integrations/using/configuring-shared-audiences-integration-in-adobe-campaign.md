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
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 6ae45cbd87fc0152fc654202e03501fc8d2abd06

---


# Configuración de la integración de audiencias compartidas en Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}

Una vez enviada esta solicitud, Adobe procede a ofrecer de la integración y a ponerse en contacto para proporcionar los detalles y la información necesaria para finalizar la configuración:

1. [Paso 1: Configuración o verificación de las cuentas externas en Adobe Campaign](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [Paso 2: Configuración de la fuente de datos](#step-2--configure-the-data-source)
1. [Paso 3: Configuración del servidor de seguimiento de campaña](#step-3--configure-campaign-tracking-server)
1. [Paso 4: Configuración del servicio de ID de visitante](#step-4--configure-the-visitor-id-service)

## Paso 1: Configuración o verificación de las cuentas externas en Adobe Campaign {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

En primer lugar, se deben configurar o verificar las cuentas externas en Adobe Campaign de la siguiente manera:

1. Haga clic en el icono **[!UICONTROL Explorador]**.
1. Vaya a **[!UICONTROL Administration > Platform > External accounts]**. Las cuentas SFTP mencionadas deberían estar ya configuradas por Adobe, y se le debe haber comunicado la información necesaria.

   * **[!UICONTROL importSharedAudience]** : Cuenta SFTP específica para la importación de audiencias.
   * **[!UICONTROL exportSharedAudience]** : Cuenta SFTP específica para la exportación de audiencias.
   ![](assets/aam_config_1.png)

1. Rellene el campo **[!UICONTROL Servidor]** : Dominio **ftp-out.demdex.com** para la cuenta externa de importación y dominio **ftp-in.demdex.com** para la cuenta externa de exportación.

   Recuerde que una exportación de Campaign es una importación para Audience Manager o el servicio principal Personas.

   >[!NOTE]
   >
   >Si utiliza S3, introduzca **[!UICONTROL el servidor de cuentas AWS S3]** siguiendo esta sintaxis:\
   `<S3bucket name>.s3.amazonaws.com/<s3object path>`\
   Para obtener más información sobre cómo configurar la cuenta S3, consulte este [artículo](../../platform/using/external-accounts.md#amazon-simple-storage-service--s3--external-account).

   ![](assets/aam_config_2.png)

1. Añada la **[!UICONTROL Cuenta]** y la **[!UICONTROL Contraseña]** proporcionadas por Adobe.

Las cuentas externas ya están configuradas.

## Paso 2: Configuración de la fuente de datos {#step-2--configure-the-data-source}

La **ID de destinatario - visitante** se crea dentro de Audience Manager. Constituye una fuente de datos de serie y configurada de forma predeterminada para la ID del visitante. Los segmentos creados con Campaign forman parte de esta fuente de datos.

Para configurar la fuente de datos **[!UICONTROL Destinatario - ID de visitante]**:

1. En el nodo **[!UICONTROL Explorador]**, seleccione **[!UICONTROL Administración > Plataforma > Fuentes de datos AMC]**.
1. Seleccionar **[!UICONTROL Destinatario - ID de visitante]**.
1. Introduzca el **[!UICONTROL ID de origen de datos]** y la **[!UICONTROL ID de destino AAM]** proporcionadas por Adobe.

   ![](assets/aam_config_3.png)

## Paso 3: Configuración del servidor de seguimiento de campaña {#step-3--configure-campaign-tracking-server}

Para la configuración de la integración con el servicio principal Personas o Audience Manager, también es necesario configurar el servidor de seguimiento de campañas.

Debe verificar que el servidor de seguimiento de Campaign esté registrado en el dominio (CNAME). Se puede encontrar más información sobre la delegación de nombres de dominio en [este artículo](https://helpx.adobe.com/es/campaign/kb/domain-name-delegation.html).

## Paso 4: Configuración del servicio de ID de visitante {#step-4--configure-the-visitor-id-service}

En caso de que el servicio de ID de visitante no se haya configurado en las propiedades web o sitios web, consulte el siguiente [documento](https://marketing.adobe.com/resources/help/es_ES/mcvid/mcvid-setup-aam-analytics.html) o el siguiente [vídeo](https://helpx.adobe.com/marketing-cloud/how-to/email-marketing.html#step-two) para aprender a configurar el servicio.

La configuración y el suministro han finalizado, la integración ya puede utilizarse para importar y exportar audiencias o segmentos.
