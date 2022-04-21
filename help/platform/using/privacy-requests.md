---
product: campaign
title: Administrar solicitudes de privacidad
description: Obtenga información sobre las solicitudes de privacidad
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: c7688c2a-f0a7-4c51-a4cf-bf96fe8bf9b6
source-git-commit: a8044037e889f59d4288a0746001e84d319f6bcf
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 98%

---

# Acerca de las solicitudes de privacidad {#privacy-requests}

![](../../assets/v7-only.svg)

Para una presentación general sobre la Gestión de la privacidad, consulte esta [sección](privacy-management.md).

Esta información se aplica al RGPD, la CCPA, la PDPA y la LGPD. Para obtener más información sobre estas normativas, consulte [esta sección](privacy-management.md#privacy-management-regulations).

>[!NOTE]
>
>La opción de exclusión de la Venta de información personal, que es específica de la CCPA, se explica en esta [sección](#sale-of-personal-information-ccpa).

<!--Installation procedures described in this document are applicable starting Campaign Classic 18.4 (build 8931+). If you are running on a previous version, refer to this [technote](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html).-->

Para ayudarle a facilitar su preparación para la privacidad, Adobe Campaign le permite gestionar solicitudes de acceso y eliminación. El **derecho de acceso** y el **derecho a ser olvidado** (solicitud de supresión) se describen en [esta sección](privacy-management.md#right-access-forgotten).

Adobe Campaign ofrece a los controladores de datos dos posibilidades para realizar solicitudes de Acceso y Eliminación de privacidad:

* A través de **la interfaz de Adobe Campaign**: por cada solicitud de privacidad, el controlador de datos crea una nueva solicitud de privacidad en Adobe Campaign. Consulte [esta sección](privacy-requests-ui.md).
* A través de la **API**: Adobe Campaign proporciona una API que permite el procesamiento automático de solicitudes de privacidad mediante SOAP. Consulte [esta sección](privacy-requests-api.md).

>[!NOTE]
>
>Para obtener más información sobre los datos personales y las distintas entidades que administran los datos (controlador de datos, procesador de datos y sujeto de datos), consulte [Datos personales y personas](privacy-and-recommendations.md#personal-data).

## Requisitos previos {#prerequesites}

Adobe Campaign oferta las herramientas de los controladores de datos para crear y procesar solicitudes de privacidad de datos almacenados en Adobe Campaign. Sin embargo, es responsabilidad del controlador de datos administrar la relación con el sujeto de datos (correo electrónico, atención al cliente o un portal web).

Por ello, es responsabilidad del controlador de datos confirmar la identidad del sujeto de datos que realiza la solicitud y confirmar que la información devuelta al solicitante sea sobre el sujeto de datos.

## Instalación del paquete de privacidad {#install-privacy-package}

Para utilizar esta funcionalidad, debe instalar el **[!UICONTROL Privacy Data Protection Regulation]** paquete mediante el menú **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** > **[!UICONTROL Adobe Campaign Package]**. Para obtener más información sobre cómo instalar paquetes, consulte la [documentación detallada](../../installation/using/installing-campaign-standard-packages.md).

Dos carpetas nuevas, específicas de Privacidad, en **[!UICONTROL Administration]** > **[!UICONTROL Platform]**:

* **[!UICONTROL Privacy Requests]**: aquí es donde creará sus solicitudes de privacidad y rastreará su evolución.
* **[!UICONTROL Namespaces]**: aquí es donde definirá el campo que se utilizará para identificar el sujeto de datos en la base de datos de Adobe Campaign.

![](assets/privacy-folders.png)

En **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**, se ejecutan tres flujos de trabajo técnicos cada día para procesar las solicitudes de privacidad.

![](assets/privacy-workflows.png)

* **[!UICONTROL Collect privacy requests]**: este flujo de trabajo genera los datos del destinatario almacenados en Adobe Campaign y lo hace disponibles para su descarga en la pantalla de la solicitud de privacidad.
* **[!UICONTROL Delete privacy requests data]**: este flujo de trabajo elimina los datos del destinatario almacenados en Adobe Campaign.
* **[!UICONTROL Privacy request cleanup]**: este flujo de trabajo borra los archivos de solicitud de acceso anteriores a 90 días.

En **[!UICONTROL Administration]** > **[!UICONTROL Access Management]** > **[!UICONTROL Named rights]**, se ha añadido el **[!UICONTROL Privacy Data Right]** asignado. Se requiere este derecho asignado para que los controladores de datos puedan utilizar las herramientas de privacidad. Esto les permite crear nuevas solicitudes, rastrear su evolución, utilizar la API, etc.

![](assets/privacy-right.png)

## Áreas de nombres {#namesspaces}

Antes de crear solicitudes de privacidad, debe definir el área de nombres que utilizará. Esta es la clave que se utiliza para identificar el sujeto de datos en la base de datos de Adobe Campaign.

Hay tres áreas de nombres predeterminadas disponibles: correo electrónico, teléfono y teléfono móvil. Si necesita un área de nombres diferente (por ejemplo, un campo personalizado de destinatario), puede crear una nueva desde **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**.

>[!NOTE]
>
>Para obtener un rendimiento óptimo, se recomienda utilizar áreas de nombres predeterminadas.
