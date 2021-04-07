---
solution: Campaign Classic
product: campaign
title: Administración de permisos de flujo de trabajo
description: Obtenga información sobre cómo administrar los permisos de flujo de trabajo
audience: workflow
content-type: reference
topic-tags: advanced-management
translation-type: ht
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: ht
source-wordcount: '321'
ht-degree: 100%

---


# Administración de permisos de flujo de trabajo{#managing-rights}

Si no son administradores, los operadores de Adobe Campaign necesitan derechos de acceso para crear, ejecutar o modificar los flujos de trabajo.

En términos generales, los operadores que intervienen en los flujos de trabajo necesitan acceder a los archivos que contienen los datos utilizados durante las diversas actividades (destinatarios, lista de destinatarios, suscripciones, envíos, etc.) y, probablemente, a sus subarchivos.

También se deben asignar a los derechos con un nombre que coincida con las acciones realizadas por los flujos de trabajo a los que afectan (importación de destinatarios, acceso a archivos, fusión, ejecución de secuencias de comandos SQL, etc.).

Para gestionar operadores y permisos, consulte esta [sección](../../platform/using/access-management.md).

## Grupos de operadores {#operator-groups-wf}

Los siguientes grupos de operadores están asociados al flujo de trabajo:

* El grupo **[!UICONTROL Workflow execution]** permite controlar la ejecución y la aprobación de los flujos de trabajo de objetivo: el derecho denominado “WORKFLOW” se asigna a los operadores de este grupo. Es necesario para todas las acciones relacionadas con los flujos de trabajo, además de los derechos de acceso a los archivos de datos. De forma predeterminada, el grupo **[!UICONTROL Workflow execution]** tiene acceso de solo lectura a los archivos de flujo de trabajo de objetivo estándar y a las plantillas de flujo de trabajo. Los operadores de este grupo también tienen acceso de lectura y escritura al archivo de aprobaciones pendientes.
* El grupo **[!UICONTROL Workflow supervisors]** permite que los operadores administren las aprobaciones de flujo de trabajo.
* El grupo **[!UICONTROL Operation Managers]** permite el acceso a los flujos de trabajo de campaña.

## Derechos asignados {#named-rights}

Solo el derecho denominado “WORKFLOW” es específico de los flujos de trabajo: permite crear, iniciar y detener flujos de trabajo. Se necesitan derechos de lectura en el archivo de flujo de trabajo para que el derecho llamado sea aplicable. Para flujos de trabajo de objetivo, es necesario tener derechos de lectura sobre el archivo **[!UICONTROL Profiles and Targets]**.

## Cuenta de ejecución del flujo de trabajo {#workflow-execution-account}

Puede configurar la cuenta de ejecución para usarla al nivel de plantilla de flujo de trabajo. La cuenta de ejecución permite asignar autorizaciones directamente al flujo de trabajo, independientemente de si el operador de Adobe Campaign inicia la ejecución. De forma predeterminada, cada flujo de trabajo se ejecuta con los derechos del operador que lo inicia.

Para asignar una cuenta de ejecución a un flujo de trabajo, vaya a la lista de plantillas de flujo de trabajo y haga clic con el botón derecho en la plantilla vinculada al flujo de trabajo. Elija **[!UICONTROL Action > Change execution account...]** y después seleccione la cuenta que desee utilizar.
