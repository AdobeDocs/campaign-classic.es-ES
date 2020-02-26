---
title: Prueba
seo-title: Prueba
description: Prueba
seo-description: null
page-status-flag: never-activated
uuid: 3522f4ac-3a72-4ff1-b3aa-1b4c283ef2bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 78c70ef4-807d-45d4-ac87-2b741c0ef5cb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b78db689958c9b240da9a0315060fe63bcb48e0a

---


# Prueba{#test}

Una actividad de tipo **Test** activa la primera transición que cumple la condición asociada a esta. If no condition is satisfied and if the **[!UICONTROL Use the default fork]** option is activated, the default transition will be activated.

Una condición es una expresión JavaScript que debe evaluarse como “verdadera” o “falsa”. To enter the expression, click the icon to the right of the name of the condition, and then select **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

Para obtener más información sobre todas las funciones adicionales de JavaScript y los métodos SOAP del servidor aplicativo accesible mediante JavaScript de flujo de trabajo, consulte la [Documentación de JSAPI](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

También puede insertar variables directamente desde este editor.

Se pueden añadir, eliminar u ordenar las condiciones desde la ventana de edición de la propiedad actividad, pero también se puede modificar desde la transición.

Si el resultado de un cálculo se reutiliza en condiciones diferentes, es posible calcularlo en el guion de inicialización de la actividad. El resultado debe almacenarse en una variable de la tarea a la que deben acceder los scripts de condición (task.vars.xxx).
