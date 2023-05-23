---
product: campaign
title: Requisitos previos para la instalación de Campaign en Windows
description: Requisitos previos para la instalación de Campaign en Windows
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: a7cf59cc-9260-4109-af4c-b2e2a9c999da
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 8%

---

# Introducción a la instalación de Campaign en Windows {#prerequisites-of-campaign-installation-in-windows}



La configuración técnica y el software necesarios para instalar Adobe Campaign se presentan en la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md).

El proceso de instalación del servidor de Adobe Campaign para uso de varias instancias se describe a continuación en [Instalación del servidor](../../installation/using/installing-the-server.md).

Los pasos principales son los siguientes:

1. Instale el servidor de aplicaciones, consulte [Ejecución del programa de instalación](../../installation/using/installing-the-server.md#executing-the-installation-program).
1. Integre con un servidor web (opcional, según los componentes implementados), consulte [Configurar el servidor web de IIS](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

Una vez completados los pasos de instalación, debe configurar las instancias, la base de datos y el servidor. Para obtener más información, consulte [Acerca de la configuración inicial](../../installation/using/about-initial-configuration.md).

>[!NOTE]
>
>Cuando Adobe Campaign se implementa en un entorno Windows, los usuarios con los derechos de acceso necesarios pueden utilizar la sintaxis UNC (Convención de nomenclatura universal.uniforme) para las rutas de acceso durante la manipulación de archivos en la red.
