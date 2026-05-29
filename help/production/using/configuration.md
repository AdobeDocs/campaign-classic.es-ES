---
product: campaign
title: Configuración adicional
description: Configuración
feature: Monitoring, Configuration
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
TQID: https://experienceleague.adobe.com/gzcQquM9q71NIOt8mScgRpLtwffxvopslrrpLxxIang
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2: id: efa38731-2723-4334-8d8b-a778af834835id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 194
ht-degree: 17%

---

# Configuración{#configuration}



## Cambio del puerto de escucha syslogd {#changing-the-syslogd-listening-port}

De manera predeterminada, el puerto de escucha **syslogd** es 666 (udp). Puede modificarla mediante una variable de entorno si es necesario.

Una vez configurada, todos los módulos de Adobe Campaign tienen en cuenta esta variable.

### En Linux {#in-linux}

Edite el archivo **customer.sh** y agregue la línea siguiente:

```sql
export TRACE_ADDR=localhost:<listening port>
```

### En Windows {#in-windows}

Debe crear la variable de entorno **TRACE_ADDR** con el valor **localhost**: **`<listening port="" />`**.

>[!IMPORTANT]
>
>Se recomienda ejecutar algunas pruebas para asegurarse de que la plataforma funciona después de crear esta variable de entorno.

## Configuración de zonas de seguridad {#configuring-security-zones}

Cada operador debe estar vinculado a una zona para iniciar sesión en una instancia y la IP del operador debe incluirse en las direcciones o conjuntos de direcciones definidos en la zona de seguridad. La configuración de zona técnica se realiza en el archivo de configuración del servidor de Adobe Campaign. La vinculación de un operador a una zona de seguridad debe definirse en la consola (nodo **[!UICONTROL Administration > Access management > Operators]**).

>[!NOTE]
>
>Para obtener más información sobre la configuración de zonas de seguridad, consulte [esta sección](../../installation/using/security-zones.md).
