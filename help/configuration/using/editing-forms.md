---
product: campaign
title: Edición de formularios
description: Edición de formularios
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: a6549ad4d94b93d65752df66aeec39b90e4c3ec5
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 5%

---


# Edición de formularios{#editing-forms}

![](../../assets/common.svg)

## Información general

Los especialistas en marketing y los operadores utilizan formularios de entrada para crear, modificar y previsualizar registros. Forms muestra una representación visual de la información.

Puede crear y modificar formularios de entrada:

* Puede modificar los formularios de entrada de fábrica que se envían de forma predeterminada. Los formularios de entrada de fábrica se basan en los esquemas de datos de fábrica.
* Puede crear formularios de entrada personalizados, basados en esquemas de datos definidos.

Forms son entidades de `xtk:form` tipo . Puede ver la estructura del formulario de entrada en el `xtk:form` esquema. Para ver este esquema, elija **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** del menú . Más información sobre [estructura de formulario](form-structure.md).

Para acceder a los formularios de entrada, seleccione **[!UICONTROL Administration]> [!UICONTROL Configuration] >[!UICONTROL Input forms]** del menú:

![](assets/d_ncs_integration_form_arbo.png)

Para diseñar formularios, edite el contenido XML en el editor XML:

![](assets/d_ncs_integration_form_edit.png)

[Más información](form-structure.md#formatting).

Para obtener una vista previa de un formulario, haga clic en el botón **[!UICONTROL Preview]** pestaña:

![](assets/d_ncs_integration_form_preview.png)

## Tipos de formulario

Puede crear diferentes tipos de formularios de entrada. El tipo de formulario determina cómo navegan los usuarios en el formulario:

* Pantalla de la consola

   Este es el tipo de formulario predeterminado. El formulario consta de una sola página.

   ![](assets/console_screen_form.png)

* Administración de contenido

   Utilice este tipo de formulario para la gestión de contenido. Consulte esta [caso de uso](../../delivery/using/use-case--creating-content-management.md).

   ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Asistente

   Este formulario consta de varias pantallas flotantes que se ordenan en secuencias específicas. Los usuarios navegan de una pantalla a otra. [Más información](form-structure.md#wizards).

* Iconbox

   Este formulario consta de varias páginas. Para desplazarse por el formulario, los usuarios seleccionan iconos a la izquierda del formulario.

   ![](assets/iconbox_form_preview.png)

* Portátil

   Este formulario consta de varias páginas. Para desplazarse por el formulario, los usuarios seleccionan fichas en la parte superior del formulario.

   ![](assets/notebook_form_preview.png)

* Panel vertical

   Este formulario muestra un árbol de navegación.

* Panel horizontal

   Este formulario muestra una lista de elementos.

