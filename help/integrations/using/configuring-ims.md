---
product: campaign
title: Configuración de IMS
description: Descubra más información sobre cómo conectar con un ID de Adobe
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 02eebe83de49ee97e573b0c47ca1fddb2195b991
workflow-type: ht
source-wordcount: '345'
ht-degree: 100%

---

# Configuración de IMS{#configuring-ims}

![](../../assets/common.svg)

>[!IMPORTANT]
>
>La implementación IMS de Adobe está estrictamente reservada para los administradores técnicos de Adobe. Póngase en contacto con su ejecutivo de Adobe para iniciar el proceso de implementación.

## Requisitos previos {#prerequisites}

Para utilizar la integración con IMS:

* Debe tener un nombre e ID de organización de Adobe Experience Cloud. Para encontrar su ID de organización, consulte [esta página](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=es){_blank}.
* Debe añadir usuarios en Experience Cloud. Para obtener más información, consulte [esta página](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=es){_blank}.

>[!NOTE]
>
>Asegúrese de que los usuarios estén vinculados a los grupos de Adobe Experience Cloud que se sincronizan con Adobe Campaign. [Más información](#configuring-the-external-account).

## Actualización de la consola {#updating-the-console}

Para utilizar esta funcionalidad, es imprescindible instalar la versión más reciente de la consola.

## Instalación del paquete {#installing-the-package}

Debe instalar el paquete integrado **[!UICONTROL Integration with the Adobe Experience Cloud]**. La instalación de un paquete de integración se realiza de la misma forma que la de un paquete estándar, la cual se detalla en [esta página](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Configuración de la cuenta externa {#configuring-the-external-account}

Configure la cuenta externa de **Adobe Experience Cloud** en **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Esta configuración está reservada para el administrador técnico.

![](assets/ims_5.png)

Introduzca la siguiente información:

* La información de conexión para el servidor IMS utilizado (ID y secreto). El servicio de asistencia de Adobe proporciona esta información. Para obtener más información, consulte las [preguntas frecuentes de los administradores de Adobe Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html?lang=es).

   La dirección **[!UICONTROL Callback server]** debe especificarse en **https**. Este campo corresponde a la dirección URL de acceso de la instancia de Adobe Campaign.

* ID de organización: para encontrar su ID de organización, consulte [esta página](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=es){_blank}.
* Máscara de asociación: este campo permite definir la sintaxis que permite sincronizar los nombres de configuración en Enterprise Dashboard con los grupos de Adobe Campaign. Si se utiliza la sintaxis “Campaign - tenant_id - (.&#42;)”, el grupo de seguridad creado en Adobe Campaign se vincula al nombre de la configuración “Campaign - tenant_id - internal_name” en Enterprise Dashboard.

   >[!CAUTION]
   >
   >La máscara de asociación es esencial para que la conexión mediante Adobe ID funcione correctamente.

* La información de conexión de Adobe Experience Cloud, especialmente el nombre del inquilino de Adobe Experience Cloud.
