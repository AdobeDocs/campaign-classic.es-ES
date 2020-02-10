---
title: Administración de derechos
seo-title: Administración de derechos
description: Administración de derechos
seo-description: null
page-status-flag: never-activated
uuid: 07039fec-c957-4548-acc7-22dc7827a54b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: f78603e9-f6ff-4ebe-941b-b3fbd1924b71
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Administración de derechos{#managing-rights}

Si no son administradores, los operadores de Adobe Campaign necesitan derechos de acceso para crear, ejecutar o modificar los flujos de trabajo.

En términos generales, los operadores que intervienen en los flujos de trabajo necesitan acceder a los archivos que contienen los datos utilizados durante las diversas actividades (destinatarios, lista de destinatarios, suscripciones, envíos, etc.) y, probablemente, a sus subarchivos.

También se deben asignar a los derechos con un nombre que coincida con las acciones realizadas por los flujos de trabajo a los que afectan (importación de destinatarios, acceso a archivos, fusión, ejecución de secuencias de comandos SQL, etc.).

Para gestionar operadores y permisos, consulte esta [sección](../../platform/using/access-management.md).

## Grupos de operadores {#operator-groups}

Los siguientes grupos de operadores están asociados al flujo de trabajo:

* The **[!UICONTROL Workflow execution]** group lets you control the execution and approval of targeting workflows: the WORKFLOW named right is mapped to this group&#39;s operators. Es necesario para todas las acciones relacionadas con los flujos de trabajo, además de los derechos de acceso a los archivos de datos. By default, the **[!UICONTROL Workflow execution]** group has read-only access to standard targeting workflow files and workflow templates. Los operadores de este grupo también tienen acceso de lectura y escritura al archivo de aprobaciones pendientes.
* The **[!UICONTROL Workflow supervisors]** group lets operators manage workflow approvals.
* El **[!UICONTROL Operation Managers]** grupo al que se accede a los flujos de trabajo de las campañas.

## Derechos asignados {#named-rights}

Solo el derecho denominado “WORKFLOW” es específico de los flujos de trabajo: permite crear, iniciar y detener flujos de trabajo. Se necesitan derechos de lectura en el archivo de flujo de trabajo para que el derecho llamado sea aplicable. For targeting workflows, the reading right on the **[!UICONTROL Profiles and Targets]** file is necessary.

## Cuenta de ejecución del flujo de trabajo {#workflow-execution-account}

Puede configurar la cuenta de ejecución para usarla al nivel de plantilla de flujo de trabajo. La cuenta de ejecución permite asignar autorizaciones directamente al flujo de trabajo, independientemente de si el operador de Adobe Campaign inicia la ejecución. De forma predeterminada, cada flujo de trabajo se ejecuta con los derechos del operador que lo inicia.

Para asignar una cuenta de ejecución a un flujo de trabajo, vaya a la lista de plantillas de flujo de trabajo y haga clic con el botón derecho en la plantilla vinculada al flujo de trabajo. Elija **[!UICONTROL Action > Change execution account...]** y luego seleccione la cuenta que desee utilizar.
