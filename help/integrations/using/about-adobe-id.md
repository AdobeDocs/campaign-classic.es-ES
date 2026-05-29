---
product: campaign
title: Utilice su Adobe ID para conectarse a Adobe Campaign
description: Obtenga más información acerca de la implementación de Adobe IMS en Adobe Campaign
feature: Configuration
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 8dad8fa9-674c-433c-af30-8c6d0aadf525
TQID: https://experienceleague.adobe.com/i9Ncu86b4PZaAY6yROb-6kUdOgjbYNV1nE0Rj-Jb-OY
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: d5ef99fa-df0c-4153-bf94-105ad0724167
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: c1579802-ddd4-4214-8a91-97b2066abe11
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 194
ht-degree: 100%

---

# Acerca de Adobe ID {#about-adobe-id}

Adobe Identity Management System (IMS) ayuda a los administradores a crear y administrar el acceso del usuario a aplicaciones y servicios. Para obtener más información sobre los distintos tipos de ID de Adobe, consulte [esta página](https://helpx.adobe.com/es/enterprise/using/identity.html).

Los usuarios de Campaign pueden conectarse a la consola de Adobe Campaign con su Adobe ID, en lugar de con la [autenticación nativa de usuario/contraseña](../../platform/using/access-management-operators.md). Esta implementación proporciona las siguientes ventajas:

* Se puede utilizar la misma ID para todas las soluciones de Experience Cloud.
* Cada conexión se mantiene cuando se utiliza Adobe Campaign con diferentes integraciones.
* Política de gestión más segura de contraseñas que el inicio de sesión o la contraseña nativos.
* Uso de cuentas de ID federadas (proveedor de ID externo).

>[!IMPORTANT]
>
> Tenga en cuenta que en Campaign v8 no se permite la conexión con un usuario/contraseña (también conocida como autenticación nativa). **Adobe recomienda realizar esta migración a partir de la versión 7.3.5 de Campaign para poder migrar sin problemas a Campaign versión 8.**
>
>Aprenda a migrar a Adobe IMS en [esta sección](../../technotes/using/ac-ims.md).
>


<!--
>[!IMPORTANT]
>
>If you are connecting to Campaign through Adobe Identity Service (IMS), you need to upgrade to the latest build to be able to connect to Campaign after **June 30, 2021**. This upgrade is mandatory for both Campaign server and client console. 
>
>Depending on your current version, you must upgrade to one of the following releases: 
>
> * [Campaign [!DNL Gold Standard] 11](../../rn/using/gold-standard.md)
> * [Campaign 21.1.4](../../rn/using/latest-release.md)
>
>[Learn more about IMS updates](../../technotes/using/ims-updates.md)
-->

## Más recursos

| Páginas útiles | Recursos adicionales |
|---|---|
| [Configuración de IMS](../../integrations/using/configuring-ims.md) | [Preguntas frecuentes sobre Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html?lang=es) |
| [Implementación de IMS](../../integrations/using/implementing-ims.md) | [Gestión de acceso](../../platform/using/access-management.md) |
| [Solución de problemas de IMS](../../integrations/using/ims-troubleshooting.md) | [Instalación de paquetes de campañas](../../installation/using/installing-campaign-standard-packages.md) |
