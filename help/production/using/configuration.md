---
title: Configuración
seo-title: Configuración
description: Configuración
seo-description: null
page-status-flag: never-activated
uuid: 4316d4b2-0964-4e25-9e4f-f2378f044c85
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 12f13b8d-afc3-4b55-a31b-080d31f84fc9
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 2%

---


# Configuración{#configuration}

## Cambio del puerto de escucha syslogd {#changing-the-syslogd-listening-port}

De forma predeterminada, el puerto de escucha **syslogd** es 666 (udp). Puede modificarla mediante una variable de entorno si es necesario.

Una vez configurada, todos los módulos de Adobe Campaign toman en cuenta esta variable.

### En Linux {#in-linux}

Edite el archivo **customer.sh** y agregue la línea siguiente:

```
export TRACE_ADDR=localhost:<listening port>
```

### En Windows {#in-windows}

Debe crear la variable de entorno **TRACE_ADDR.** con el valor **localhost** : **`<listening port="" />`**.

>[!CAUTION]
>
>Se recomienda ejecutar algunas pruebas para asegurarse de que la plataforma funciona después de crear esta variable de entorno.

## Configuración de zonas de seguridad {#configuring-security-zones}

Cada operador debe estar vinculado a una zona para iniciar sesión en una instancia y la IP del operador debe incluirse en las direcciones o conjuntos de direcciones definidos en la zona de seguridad. La configuración de la zona técnica se realiza en el archivo de configuración del servidor de Adobe Campaign. La vinculación de un operador a una zona de seguridad debe definirse en la consola ( **[!UICONTROL Administration > Access management > Operators]** nodo).

>[!NOTE]
>
>For more on configuring security zones, refer to [this section](../../installation/using/configuring-campaign-server.md#defining-security-zones).

