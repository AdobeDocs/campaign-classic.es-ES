---
solution: Campaign Classic
product: campaign
title: Configuración de IMS
description: Descubra más información sobre cómo conectar con un ID de Adobe
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
translation-type: tm+mt
source-git-commit: db595e59f4725ba5d125e688e7bfc6d1c1a03d9f
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 100%

---


# Configuración de IMS{#configuring-ims}

>[!IMPORTANT]
>
>La implementación IMS de Adobe está estrictamente reservada para los administradores técnicos de Adobe. Póngase en contacto con su ejecutivo de Adobe para iniciar el proceso de implementación.

## Requisitos previos {#prerequisites}

Para utilizar la integración con IMS:

* Debe tener una organización de Adobe Experience Cloud e ID de IMS (siempre que se conecte por primera vez a Adobe Experience Cloud).
* Debe añadir usuarios en Experience Cloud. Para obtener más información, consulte [esta página](https://docs.adobe.com/content/help/es-ES/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!NOTE]
>
>Asegúrese de que los usuarios estén vinculados a los grupos de Adobe Experience Cloud que se sincronizan con Adobe Campaign. Consulte [Configuración de la cuenta externa](#configuring-the-external-account).

## Actualización de la consola {#updating-the-console}

Para utilizar esta funcionalidad, es imprescindible instalar la versión más reciente de la consola.

## Instalación del paquete {#installing-the-package}

Debe instalar el **[!UICONTROL Integration with the Adobe Experience Cloud]** paquete. La instalación de un paquete de integración se realiza de la misma forma que la de un paquete estándar, la cual se detalla en [esta página](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Configuración de la cuenta externa {#configuring-the-external-account}

Configure la cuenta externa de **Adobe Experience Cloud** en **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Esta configuración está reservada para el administrador técnico.

![](assets/ims_5.png)

Introduzca la siguiente información:

* La información de conexión para el servidor IMS utilizado (ID y secreto). El servicio de asistencia de Adobe proporciona esta información. Para obtener más información, consulte las [preguntas frecuentes de los administradores de Adobe Experience Cloud](https://docs.adobe.com/content/help/es-ES/core-services/interface/manage-users-and-products/faq.html).

   La dirección **[!UICONTROL Callback server]** debe especificarse en **https**. Este campo corresponde a la dirección URL de acceso de la instancia de Adobe Campaign.

* ID de la organización IMS: esta información está disponible en Experience Cloud (en **[!UICONTROL Administration > Experience Cloud Details]**) y se proporciona al conectarse por primera vez a Adobe Experience Cloud.
* Máscara de asociación: este campo permite definir la sintaxis que permite sincronizar los nombres de configuración en Enterprise Dashboard con los grupos de Adobe Campaign. Si se utiliza la sintaxis “Campaign - tenant_id - (.*)”, el grupo de seguridad creado en Adobe Campaign se vincula al nombre de la configuración “Campaign - tenant_id - internal_name” en Enterprise Dashboard.

   >[!CAUTION]
   >
   >La máscara de asociación es esencial para que la conexión mediante Adobe ID funcione correctamente.

* La información de conexión de Adobe Experience Cloud, especialmente el nombre del inquilino de Adobe Experience Cloud.

