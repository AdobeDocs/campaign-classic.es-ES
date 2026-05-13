---
product: campaign
title: Editar árbol de navegación del explorador de Campaign
description: Editar árbol de navegación del explorador de Campaign
feature: Application Settings
role: Developer
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
TQID: https://experienceleague.adobe.com/k8LhZvPSYchAxnQew5eknkDbxHDznzPefl032auuYLc
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 131
ht-degree: 0%

---

# Editar árbol de navegación del explorador de Campaign{#edition}

Se puede acceder a la pantalla para crear y configurar los documentos de configuración de la jerarquía de navegación a través del nodo **[!UICONTROL Administration > Configuration > Navigation hierarchies]**:

![](assets/d_ncs_integration_navigation_arbo.png)

La configuración de la jerarquía de navegación se divide en varios documentos XML. Funciona sobre un principio similar a la extensión de esquema: todos los documentos se combinan para generar un solo documento que contenga toda la configuración. Este documento no se puede editar y se muestra en la pestaña &quot;Preview&quot;.

El campo de edición proporciona el contenido del documento XML:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>El control de edición &quot;Nombre&quot; permite introducir la clave del documento, que consta del nombre y el área de nombres. Los atributos &quot;name&quot; y &quot;namespace&quot; del elemento **`<navtree>`** se actualizan automáticamente en el campo de edición XML del esquema.

La vista previa genera automáticamente el documento combinado que contiene la configuración completa:

![](assets/d_ncs_integration_navigation_preview.png)
