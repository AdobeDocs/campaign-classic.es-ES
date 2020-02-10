---
title: Funcionalidades avanzadas
seo-title: Funcionalidades avanzadas
description: Funcionalidades avanzadas
seo-description: null
page-status-flag: never-activated
uuid: 4dbf4750-0226-4f96-98d8-ec49b20374ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0c264783-2775-4ec6-8d49-cd9a45a18d60
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: af768da6ee8cc0ca2ea1f24f297239b974c113a5

---


# Funcionalidades avanzadas{#advanced-functionalities}

## Adición de una secuencia de comandos {#adding-a-script}

### Actividad de secuencia de comandos {#script-activity}

Esta actividad permite procesar datos y crear fácilmente consultas complejas que no habilitan el lenguaje SQL.

Solo se debe introducir la consulta en la ventana de secuencia de comandos.

The **[!UICONTROL Texts]** tab enables you to define text strings. They may then be used with the following syntax: **$(Identifier)**. Para obtener más información sobre el uso de textos, consulte [Adición de un encabezado y un pie de página](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>NO se recomienda el uso del código JavaScript para crear acumulados.

Para crear un historial del informe, añada la línea siguiente a la consulta JavaScript para guardar los datos archivados:

```
if( ctx.@_historyId.toString().length == 0 )
```

De lo contrario, se muestran los datos actuales.

### Secuencia de comandos externa {#external-script}

Es posible utilizar una secuencia de comandos externa que se ejecute en el servidor o del lado del cliente. Para ello:

1. Edit the report properties and click the **[!UICONTROL Scripts]**.
1. Click **[!UICONTROL Add]** and select the script to be referenced.
1. A continuación, seleccione el modo de ejecución.

   Si añade varias secuencias de comandos, utilice las flechas de la barra de herramientas para definir su secuencia de ejecución.

   ![](assets/reporting_custom_js.png)

## Llamada a otro informe {#calling-up-another-report}

### Actividad de salto {#jump-activity}

Un salto es como una transición sin una flecha: permite pasar de una actividad a otra o acceder a otro informe.
