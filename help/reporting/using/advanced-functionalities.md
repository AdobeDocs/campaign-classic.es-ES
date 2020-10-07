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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 100%

---


# Funcionalidades avanzadas{#advanced-functionalities}

## Adición de una secuencia de comandos {#adding-a-script}

### Actividad de secuencia de comandos {#script-activity}

Esta actividad permite procesar datos y crear fácilmente consultas complejas que no habilitan el lenguaje SQL.

Solo se debe introducir la consulta en la ventana de secuencia de comandos.

La pestaña **[!UICONTROL Texts]** permite definir cadenas de texto. Pueden utilizarse con la siguiente sintaxis: **$(Identifier)**. Para obtener más información sobre el uso de textos, consulte [Adición de un encabezado y un pie de página](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

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

1. Edite las propiedades del informe y haga clic en **[!UICONTROL Scripts]**.
1. Haga clic en **[!UICONTROL Add]** y seleccione la secuencia de comandos a la que desea hacer referencia.
1. A continuación, seleccione el modo de ejecución.

   Si añade varias secuencias de comandos, utilice las flechas de la barra de herramientas para definir su secuencia de ejecución.

   ![](assets/reporting_custom_js.png)

## Llamada a otro informe {#calling-up-another-report}

### Actividad de salto {#jump-activity}

Un salto es como una transición sin una flecha: permite pasar de una actividad a otra o acceder a otro informe.
