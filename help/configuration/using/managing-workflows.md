---
product: campaign
title: Administración de flujos de trabajo
description: Administración de flujos de trabajo
feature: Workflows, Configuration
role: Developer
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
TQID: 'https://experienceleague.adobe.com/dpHtLw4PYGg35t-ihmw9LGUSbjgeNloUhGXp9KPJaRU'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 11%
---
# Administración de flujos de trabajo{#managing-workflows}



De forma predeterminada, los nuevos flujos de trabajo se basan en una plantilla de flujo de trabajo preconfigurada y basada en una tabla de destinatarios (nms:recipient). Para que se basen automáticamente en la tabla personalizada de destinatarios a los que se hace referencia en la opción **Nms_DefaultRcpSchema** (consulte la sección [Configuración de la interfaz](../../configuration/using/configuring-the-interface.md) ), debe crear una nueva plantilla de flujo de trabajo.

Cree una nueva plantilla a través del nodo **[!UICONTROL Resources > Templates > Workflow templates]**. En las propiedades de la plantilla, las dimensiones proporcionadas coinciden con la tabla de destinatarios externos.

Al basar los nuevos flujos de trabajo en una plantilla creada recientemente, la tabla personalizada se selecciona de forma predeterminada para las dimensiones globales de segmentación y filtrado del flujo de trabajo.

Por lo tanto, todas las actividades utilizadas en el flujo de trabajo utilizan la tabla personalizada sin necesidad de ninguna configuración manual adicional.

Para obtener más información sobre los flujos de trabajo, consulte [esta sección](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
