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
source-git-commit: 16e35b62cdf42c04139cc17645095a3d1f6e0fa7

---


# Código SQL y código JavaScript{#sql-code-and-javascript-code}

## Código SQL {#sql-code}

An **[!UICONTROL SQL code*]* activity executes an SQL script. La secuencia de comandos es una plantilla JST.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   El área central del editor contiene la secuencia de comandos que se va a ejecutar. Esta secuencia de comandos es una plantilla JST y, por lo tanto, se puede configurar según el contexto del flujo de trabajo.

* **[!UICONTROL Processing errors]**

   Consulte Errores [de procesamiento](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Código JavaScript y código JavaScript avanzado {#javascript-code}

**[!UICONTROL JavaScript code]** y **[!UICONTROL Advanced JavaScript code]** las actividades ejecutan una secuencia de comandos de JavaScript en el contexto de un flujo de trabajo. Para obtener más información sobre secuencias de comandos, consulte la sección de plantillas [y secuencias de comandos de](../../workflow/using/javascript-scripts-and-templates.md) JavaScript.

>[!NOTE]
>
>De forma predeterminada, la fase de ejecución de **[!UICONTROL JavaScript code]** y **[!UICONTROL Advanced JavaScript code]** las actividades no puede exceder de 1 hora. Tras este retraso, el proceso se anulará con un mensaje de error y la ejecución de la actividad fallará.
>
>Puede cambiar esta demora en el **[!UICONTROL Stop execution after]** campo disponible en las propiedades de las actividades.

* **[!UICONTROL JavaScript code]**

   ![](assets/javascript_code.png)

   * **[!UICONTROL Script]**: El área central del editor contiene la secuencia de comandos que se va a ejecutar.
   * **[!UICONTROL Processing errors]**::Consulte Errores [de procesamiento](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

* **[!UICONTROL Advanced JavaScript code]**

   ![](assets/advanced_javascript_code.png)

   * **[!UICONTROL First call]**: La primera zona del editor contiene el script que se activará durante la primera llamada.
   * **[!UICONTROL Next calls]**: La segunda zona del editor contiene el script que se ejecutará durante las siguientes llamadas.
   * **[!UICONTROL Transitions]**: Puede definir varias transiciones de salida de actividad.
   * **[!UICONTROL Schedule]**::La **[!UICONTROL Schedule]** ficha permite programar cuándo activar la actividad.
