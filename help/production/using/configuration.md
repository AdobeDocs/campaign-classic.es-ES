---
solution: Campaign Classic
product: campaign
title: Configuración
description: Configuración
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 1%

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

Debe crear la variable de entorno **TRACE_ADDR.** con el valor **localhost**: **`<listening port="" />`**.

>[!IMPORTANT]
>
>Se recomienda ejecutar algunas pruebas para asegurarse de que la plataforma funciona después de crear esta variable de entorno.

## Configuración de zonas de seguridad {#configuring-security-zones}

Cada operador debe estar vinculado a una zona para iniciar sesión en una instancia y la IP del operador debe incluirse en las direcciones o conjuntos de direcciones definidos en la zona de seguridad. La configuración de la zona técnica se realiza en el archivo de configuración del servidor de Adobe Campaign. La vinculación de un operador a una zona de seguridad debe definirse en el nodo de la consola ( **[!UICONTROL Administration > Access management > Operators]**).

>[!NOTE]
>
>Para obtener más información sobre la configuración de zonas de seguridad, consulte [esta sección](../../installation/using/configuring-campaign-server.md#defining-security-zones).
