---
title: Código SQL y código JavaScript
seo-title: Código SQL y código JavaScript
description: Código SQL y código JavaScript
seo-description: null
page-status-flag: never-activated
uuid: 20a39bbf-c6b0-4697-97b4-c07609cfb048
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 1afa75c2-7377-4d03-9105-11bcc9e3206c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# Código SQL y código JavaScript{#sql-code-and-javascript-code}

Una actividad de **SQL code** ejecuta una secuencia de comandos SQL. La secuencia de comandos es una plantilla JST.

* **[!UICONTROL Script]**

   El área central del editor contiene la secuencia de comandos que se va a ejecutar. Esta secuencia de comandos es una plantilla JST y, por lo tanto, se puede configurar según el contexto del flujo de trabajo.

* **[!UICONTROL Processing errors]**

   Consulte Errores [de procesamiento](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

Las actividades de tipo **JavaScript code** ejecutan una secuencia de comandos JavaScript en el contexto de un flujo de trabajo. Para obtener más información sobre secuencias de comandos, consulte la sección de plantillas [y secuencias de comandos de](../../workflow/using/javascript-scripts-and-templates.md) JavaScript.

* **[!UICONTROL Script]**

   El área central del editor contiene la secuencia de comandos que se va a ejecutar.

* **[!UICONTROL Processing errors]**

   Consulte Errores [de procesamiento](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

La actividad de **Advanced JavaScript code** ejecuta un script JavaScript en el contexto del flujo de trabajo. Para obtener más información sobre secuencias de comandos, consulte las plantillas [y secuencias de comandos de](../../workflow/using/javascript-scripts-and-templates.md)JavaScript.

* **[!UICONTROL First call]**

   La primera zona del editor contiene el script que se activará durante la primera llamada.

* **[!UICONTROL Next calls]**

   La segunda zona del editor contiene el script que se ejecutará durante las siguientes llamadas.

* **[!UICONTROL Transitions]**

   Puede definir varias transiciones de salida de actividad.

* **[!UICONTROL Schedule]**

   The **[!UICONTROL Schedule]** tab lets you schedule when to trigger the activity.

