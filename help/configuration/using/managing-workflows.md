---
product: campaign
title: Administración de flujos de trabajo
description: Administración de flujos de trabajo
feature: Workflows, Configuration
role: Data Engineer, Developer
badge-v8: label="También se aplica a la versión 8" type="Positive" tooltip="También se aplica a Campaign v8"
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 14%

---

# Administración de flujos de trabajo{#managing-workflows}



De forma predeterminada, los nuevos flujos de trabajo se basan en una plantilla de flujo de trabajo preconfigurada y basada en una tabla de destinatarios (nms:recipient). Para que se basen automáticamente en la tabla personalizada de destinatarios a los que se hace referencia en la **Nms_DefaultRcpSchema** opción (consulte [Configuración de la interfaz](../../configuration/using/configuring-the-interface.md) ), debe crear una nueva plantilla de flujo de trabajo.

Cree una nueva plantilla a través de **[!UICONTROL Resources > Templates > Workflow templates]** nodo. En las propiedades de la plantilla, las dimensiones proporcionadas coinciden con la tabla de destinatarios externos.

Al basar los nuevos flujos de trabajo en una plantilla creada recientemente, la tabla personalizada se selecciona de forma predeterminada para las dimensiones globales de segmentación y filtrado del flujo de trabajo.

Por lo tanto, todas las actividades utilizadas en el flujo de trabajo utilizan la tabla personalizada sin necesidad de ninguna configuración manual adicional.

Para obtener más información sobre los flujos de trabajo, consulte [esta sección](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
