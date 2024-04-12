---
product: campaign
title: Configuración adicional
description: Configuración
feature: Monitoring, Configuration
badge-v7-prem: label="On-Premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 6%

---

# Configuración{#configuration}



## Cambio del puerto de escucha syslogd {#changing-the-syslogd-listening-port}

De forma predeterminada, la variable **syslogd** puerto de escucha 666 (udp). Puede modificarla mediante una variable de entorno si es necesario.

Una vez configurada, todos los módulos de Adobe Campaign tienen en cuenta esta variable.

### En Linux {#in-linux}

Edite el **customer.sh** y añada la línea siguiente:

```
export TRACE_ADDR=localhost:<listening port>
```

### En Windows {#in-windows}

Debe crear la variable **TRACE_ADDR** variable de entorno con **localhost** valor: **`<listening port="" />`**.

>[!IMPORTANT]
>
>Se recomienda ejecutar algunas pruebas para asegurarse de que la plataforma funciona después de crear esta variable de entorno.

## Configuración de zonas de seguridad {#configuring-security-zones}

Cada operador debe estar vinculado a una zona para iniciar sesión en una instancia y la IP del operador debe incluirse en las direcciones o conjuntos de direcciones definidos en la zona de seguridad. La configuración de zona técnica se realiza en el archivo de configuración del servidor de Adobe Campaign. La vinculación de un operador a una zona de seguridad debe definirse en la consola ( **[!UICONTROL Administration > Access management > Operators]** node).

>[!NOTE]
>
>Para obtener más información sobre la configuración de las zonas de seguridad, consulte [esta sección](../../installation/using/security-zones.md).
