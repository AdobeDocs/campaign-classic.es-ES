---
title: Edición
seo-title: Edición
description: Edición
seo-description: null
page-status-flag: never-activated
uuid: df9298fc-5f62-4afb-8118-ca7e3987e81f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
discoiquuid: 820be231-af76-44ce-8f4d-cd5eae1eb169
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 3%

---


# Edición{#edition}

Se puede acceder a la pantalla para crear y configurar los documentos de configuración de la jerarquía de navegación a través del **[!UICONTROL Administration > Configuration > Navigation hierarchies]** nodo:

![](assets/d_ncs_integration_navigation_arbo.png)

La configuración de la jerarquía de navegación se divide en varios documentos XML. Se basa en un principio similar a la extensión del esquema: todos los documentos se combinan para generar un solo documento que contiene toda la configuración. Este documento no se puede editar y se muestra mediante la ficha &quot;Previsualización&quot;.

El campo de edición proporciona el contenido del documento XML:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>El control de edición &quot;Nombre&quot; permite introducir la clave de documento que consta del nombre y la Área de nombres. The &quot;name&quot; and &quot;namespace&quot; attributes of the **`<navtree>`** element are automatically updated in the XML edit field of the schema.

La previsualización genera automáticamente el documento combinado que contiene la configuración completa:

![](assets/d_ncs_integration_navigation_preview.png)

