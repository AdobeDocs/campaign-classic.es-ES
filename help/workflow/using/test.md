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
translation-type: ht
source-git-commit: f7ed7e59be2cfbde467b0c80d21cfbf52016a2b8
workflow-type: ht
source-wordcount: '190'
ht-degree: 100%

---


# Prueba{#test}

Una actividad de tipo **Test** activa la primera transición que cumple la condición asociada a esta. Si no se cumple ninguna condición y si la opción **[!UICONTROL Use the default fork]** está activada, se activa la transición predeterminada.

Una condición es una expresión JavaScript que debe evaluarse como “verdadera” o “falsa”. Para introducir la expresión, haga clic en el icono a la derecha del nombre de la condición y, a continuación, seleccione **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

Para obtener más información sobre todas las funciones adicionales de JavaScript y los métodos SOAP del servidor aplicativo accesible mediante JavaScript de flujo de trabajo, consulte la [Documentación de JSAPI](https://docs.adobe.com/content/help/es-ES/campaign-classic/technicalresources/api/index.html).

También puede insertar variables directamente desde este editor. Para obtener más información sobre cómo trabajar con variables, consulte [esta sección](../../workflow/using/javascript-scripts-and-templates.md#variables).

Se pueden añadir, eliminar u ordenar las condiciones desde la ventana de edición de la propiedad actividad, pero también se puede modificar desde la transición.

Si el resultado de un cálculo se reutiliza en condiciones diferentes, es posible calcularlo en el guion de inicialización de la actividad. El resultado debe almacenarse en una variable de la tarea a la que deben acceder los scripts de condición (task.vars.xxx).
