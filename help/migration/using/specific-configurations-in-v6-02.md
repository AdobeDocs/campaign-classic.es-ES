---
solution: Campaign Classic
product: campaign
title: Configuraciones específicas en la versión 6.02
description: Configuraciones específicas en la versión 6.02
audience: migration
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 3%

---


# Configuraciones específicas en la versión 6.02{#specific-configurations-in-v6-02}

En la siguiente sección se detalla la configuración adicional necesaria para migrar desde la versión 6.02. También debe configurar las opciones detalladas en la sección [Configuraciones generales](../../migration/using/general-configurations.md).

## Aplicaciones web {#web-applications}

Si va a realizar la migración desde la versión 6.02, es posible que aparezcan registros de errores relacionados con las aplicaciones web de tipo información general. Ejemplos de mensajes de error:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

Estas aplicaciones web usaban SQLData y no son compatibles con v7, debido a la mayor seguridad. Estos errores provocarán un error en la migración.

Si no ha utilizado estas aplicaciones web, ejecute el siguiente script de limpieza y vuelva a ejecutar el postupgrade:

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

Si ha modificado estas aplicaciones web y desea seguir usándolas en v7, debe activar la opción **allowSQLInjection** en las diferentes zonas de seguridad y volver a inicio la posactualización. Consulte la sección [SQLData](../../migration/using/general-configurations.md#sqldata) para obtener más información sobre esto.

## Facilidad de uso: Página de inicio y navegación {#user-friendliness--home-page-and-navigation}

>[!IMPORTANT]
>
>Si desea seguir utilizando aplicaciones web de tipo general v6.02, debe activar la opción **allowSQLInjection** en las diferentes zonas de seguridad antes de la posactualización. Consulte [Aplicaciones web](#web-applications).

Tras una migración desde la versión 6.02, la página de inicio de Adobe Campaign v6.02 ya no se muestra, pero sigue siendo accesible y compatible con Adobe Campaign v7.

Para continuar usando la página principal v6.02, debe instalar un paquete de &quot;compatibilidad&quot; después de la migración.

Para ello, importe el paquete de compatibilidad:

Haga clic en **[!UICONTROL Tools > Advanced > Import package]** y elija el paquete **campaignMigration.xml** en **`\nl\datakit\nms\[Your language]\package\optional`**.

Para permitir el acceso a las interfaces de tipo de Aplicación web v6.02, la opción de configuración del servidor **sessionTokenOnly** debe activarse en el archivo **serverConf.xml**:

```
sessionTokenOnly="true"
```

Esta opción altera los niveles de seguridad para garantizar la compatibilidad de la interfaz.

Una vez instalado el paquete, la página de inicio de Adobe Campaign v7 se sustituye por la antigua página de inicio v6.02, que se completa con las configuraciones generales de v7 (titular de página de inicio azul).

![](assets/dashboards.png)

Todos los vínculos de esta página principal llevan a pantallas v7 excepto las listas (**[!UICONTROL operation list]**, **[!UICONTROL delivery tracking in operations]**, etc.) que se vinculan a la descripción general de la versión 6.02 (aplicaciones web).

![](assets/dashboards2.png)

Si desea agregar otra información general configurada en v6.02, debe agregarla a la página de inicio desde el panel. (**[!UICONTROL Administration > Access management > Dashboard]**).

>[!NOTE]
>
>Recuerde desconectar y volver a conectar la consola para registrar las modificaciones.

## Centro de mensajes {#message-center}

Después de una migración de instancia de control a Message Center, debe volver a publicar las Plantillas de mensaje transaccional para que funcionen.

En v7, los nombres de Plantillas de mensaje transaccional en instancias de ejecución han cambiado. Actualmente llevan el prefijo el nombre del operador que corresponde a la instancia de control en la que se crean, por ejemplo **control1_template1_rt** (donde **control1** es el nombre del operador). Si tiene un volumen significativo de plantillas, le recomendamos que elimine las plantillas antiguas de las instancias de control.
