---
product: campaign
title: Edición
description: Edición
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 1%

---

# Editar árbol de navegación del explorador de Campaign{#edition}

Se puede acceder a la pantalla para crear y configurar los documentos de configuración de la jerarquía de navegación a través del nodo **[!UICONTROL Administration > Configuration > Navigation hierarchies]**:

![](assets/d_ncs_integration_navigation_arbo.png)

La configuración de la jerarquía de navegación se divide en varios documentos XML. Funciona con un principio similar a la extensión de esquema: todos los documentos se combinan para generar un solo documento que contenga toda la configuración. Este documento no se puede editar y se muestra a través de la pestaña &quot;Preview&quot;.

El campo de edición proporciona el contenido del documento XML:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>El control de edición &quot;Nombre&quot; permite introducir la clave del documento que consta del nombre y el área de nombres. Los atributos &quot;name&quot; y &quot;namespace&quot; del elemento **`<navtree>`** se actualizan automáticamente en el campo de edición XML del esquema.

La vista previa genera automáticamente el documento combinado que contiene la configuración completa:

![](assets/d_ncs_integration_navigation_preview.png)
