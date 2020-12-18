---
solution: Campaign Classic
product: campaign
title: Administración de flujos de trabajo
description: Administración de flujos de trabajo
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 11%

---


# Administración de flujos de trabajo{#managing-workflows}

De forma predeterminada, los nuevos flujos de trabajo se basan en una plantilla de flujo de trabajo preconfigurada y basada en una tabla de destinatario (nms:destinatario). Para que se basen automáticamente en la tabla personalizada de destinatarios a la que se hace referencia en la opción **Nms_DefaultRcpSchema** (consulte [Configuración de la interfaz](../../configuration/using/configuring-the-interface.md)), debe crear una nueva plantilla de flujo de trabajo.

Cree una nueva plantilla a través del nodo **[!UICONTROL Resources > Templates > Workflow templates]**. En las propiedades de la plantilla, las dimensiones proporcionadas coinciden con la tabla de destinatarios externos.

Al basar sus nuevos flujos de trabajo en una plantilla creada recientemente, la tabla personalizada se seleccionará de forma predeterminada para las dimensiones de filtrado y objetivos globales del flujo de trabajo.

Todas las actividades utilizadas en el flujo de trabajo utilizarán la tabla personalizada sin necesidad de ninguna configuración manual adicional.

Para obtener más información sobre los flujos de trabajo, consulte [esta sección](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)

