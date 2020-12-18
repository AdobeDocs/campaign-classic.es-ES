---
solution: Campaign Classic
product: campaign
title: Edición
description: Edición
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 2%

---


# Edición{#edition}

Se puede acceder a la pantalla para crear y configurar los documentos de configuración de la jerarquía de navegación a través del nodo **[!UICONTROL Administration > Configuration > Navigation hierarchies]**:

![](assets/d_ncs_integration_navigation_arbo.png)

La configuración de la jerarquía de navegación se divide en varios documentos XML. Se basa en un principio similar a la extensión del esquema: todos los documentos se combinan para generar un solo documento que contiene toda la configuración. Este documento no se puede editar y se muestra mediante la ficha &quot;Previsualización&quot;.

El campo de edición proporciona el contenido del documento XML:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>El control de edición &quot;Nombre&quot; permite introducir la clave de documento que consta del nombre y la Área de nombres. Los atributos &quot;name&quot; y &quot;Área de nombres&quot; del elemento **`<navtree>`** se actualizan automáticamente en el campo de edición XML del esquema.

La previsualización genera automáticamente el documento combinado que contiene la configuración completa:

![](assets/d_ncs_integration_navigation_preview.png)

