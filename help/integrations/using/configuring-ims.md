---
title: Configuración de IMS
seo-title: Configuración de IMS
description: Configuración de IMS
seo-description: null
page-status-flag: never-activated
uuid: b659d29f-2a27-4a7b-b5ca-f44c3271dd4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: 279d0548-c876-4d5f-a195-48618bd5e9d1
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Configuración de IMS{#configuring-ims}

## Requisitos previos {#prerequisites}

Para utilizar la integración con IMS:

* Debe tener una organización de Adobe Marketing Cloud e ID de IMS (siempre que se conecte por primera vez a Adobe Marketing Cloud).
* Debe añadir usuarios en Marketing Cloud. Para obtener más información, consulte esta página: [https://marketing.adobe.com/resources/help/es_ES/mcloud/admin_getting_started.html](https://marketing.adobe.com/resources/help/es_ES/mcloud/admin_getting_started.html).

>[!NOTE]
>
>Asegúrese de que los usuarios estén vinculados a los grupos de Adobe Marketing Cloud que se sincronizan con Adobe Campaign. Consulte [Configuración de la cuenta externa](#configuring-the-external-account).

## Actualización de la consola {#updating-the-console}

Para utilizar esta funcionalidad, es imprescindible instalar la versión más reciente de la consola.

## Instalación del paquete {#installing-the-package}

Se debe instalar el paquete **[!UICONTROL Integration with the Adobe Experience Cloud]**. La instalación de un paquete de integración se realiza de la misma forma que la de un paquete estándar, la cual se detalla en [esta página](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Configuración de la cuenta externa {#configuring-the-external-account}

Configure la cuenta externa de **Adobe Experience Cloud** en **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Esta configuración está reservada para el administrador técnico.

![](assets/ims_5.png)

Introduzca la siguiente información:

* La información de conexión para el servidor IMS utilizado (ID y secreto). El servicio de asistencia de Adobe proporciona esta información. Para obtener más información, consulte las [preguntas frecuentes de los administradores de Adobe Experience Cloud](https://marketing.adobe.com/resources/help/es_ES/mcloud/faq.html).

   La dirección **[!UICONTROL Callback server]** debe especificarse en **https**. Este campo corresponde a la dirección URL de acceso de la instancia de Adobe Campaign.

* ID de la organización IMS: esta información está disponible en Experience Cloud (en **[!UICONTROL Administration > Experience Cloud Details]**) y se proporciona al conectarse por primera vez a Adobe Experience Cloud.
* Máscara de asociación: este campo permite definir la sintaxis que permite sincronizar los nombres de configuración en Enterprise Dashboard con los grupos de Adobe Campaign. Si se utiliza la sintaxis “Campaign - tenant_id - (.*)”, el grupo de seguridad creado en Adobe Campaign se vincula al nombre de la configuración “Campaign - tenant_id - internal_name” en Enterprise Dashboard.

   >[!CAUTION]
   >
   >La máscara de asociación es esencial para que la conexión mediante Adobe ID funcione correctamente.

* La información de conexión de Adobe Experience Cloud, especialmente el nombre del inquilino de Adobe Experience Cloud.

