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
translation-type: ht
source-git-commit: 26ba86073e4f1569bf05a7d8aa864ca87baed3ea
workflow-type: ht
source-wordcount: '201'
ht-degree: 100%

---


# Código SQL y código JavaScript{#sql-code-and-javascript-code}

## Código SQL {#sql-code}

Una actividad de **[!UICONTROL SQL code]** ejecuta una secuencia de comandos SQL. La secuencia de comandos es una plantilla JST.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   El área central del editor contiene la secuencia de comandos que se va a ejecutar. Esta secuencia de comandos es una plantilla JST y, por lo tanto, se puede configurar según el contexto del flujo de trabajo.

* **[!UICONTROL Processing errors]**

   Consulte [Errores de procesamiento](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Código JavaScript y código JavaScript avanzado {#javascript-code}

Las actividades **[!UICONTROL JavaScript code]** y **[!UICONTROL Advanced JavaScript code]** ejecutan una secuencia de comandos JavaScript en el contexto de un flujo de trabajo. Para obtener más información sobre secuencias de comandos, consulte la sección [Secuencias de comandos de JavaScript y plantillas](../../workflow/using/javascript-scripts-and-templates.md).

>[!NOTE]
>
>De forma predeterminada, la fase de ejecución de **[!UICONTROL JavaScript code]** y **[!UICONTROL Advanced JavaScript code]** actividades no puede exceder de 1 hora. Tras esta demora, el proceso se anula con un mensaje de error y la ejecución de la actividad falla.
>
>Puede cambiar esta demora en el campo **[!UICONTROL Stop execution after]** disponible en las propiedades de las actividades.

* **[!UICONTROL JavaScript code]**

   ![](assets/javascript_code.png)

   * **[!UICONTROL Script]**: El área central del editor contiene la secuencia de comandos que se va a ejecutar.
   * **[!UICONTROL Processing errors]**: Consulte [Errores de procesamiento](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

* **[!UICONTROL Advanced JavaScript code]**

   ![](assets/advanced_javascript_code.png)

   * **[!UICONTROL First call]**: La primera zona del editor contiene el script que se activará durante la primera llamada.
   * **[!UICONTROL Next calls]**: La segunda zona del editor contiene el script que se ejecutará durante las siguientes llamadas.
   * **[!UICONTROL Transitions]**: Puede definir varias transiciones de salida de actividad.
   * **[!UICONTROL Schedule]**: La pestaña **[!UICONTROL Schedule]** permite programar el lanzamiento de la actividad.
