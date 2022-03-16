---
product: campaign
title: Configuración adicional
description: Configuración
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 1%

---

# Configuración{#configuration}

![](../../assets/v7-only.svg)

## Cambio del puerto de escucha syslogd {#changing-the-syslogd-listening-port}

De forma predeterminada, la variable **syslogd** el puerto de escucha es 666 (udp). Puede modificarla con una variable de entorno si es necesario.

Una vez configurada, todos los módulos de Adobe Campaign tienen en cuenta esta variable.

### En Linux {#in-linux}

Edite el **customer.sh** y agregue la línea siguiente:

```
export TRACE_ADDR=localhost:<listening port>
```

### En Windows {#in-windows}

Debe crear la variable **TRACE_ADDR** variable de entorno con la variable **localhost** valor: **`<listening port="" />`**.

>[!IMPORTANT]
>
>Se recomienda ejecutar algunas pruebas para asegurarse de que la plataforma funcione después de crear esta variable de entorno.

## Configuración de zonas de seguridad {#configuring-security-zones}

Cada operador debe estar vinculado a una zona para iniciar sesión en una instancia y la IP del operador debe incluirse en las direcciones o conjuntos de direcciones definidos en la zona de seguridad. La configuración de la zona técnica se realiza en el archivo de configuración del servidor de Adobe Campaign. La vinculación de un operador a una zona de seguridad debe definirse en la consola ( **[!UICONTROL Administration > Access management > Operators]** nodo ).

>[!NOTE]
>
>Para obtener más información sobre la configuración de las zonas de seguridad, consulte [esta sección](../../installation/using/security-zones.md).
