---
solution: Campaign Classic
product: campaign
title: 'Interacción: búfer de datos'
description: 'Interacción: búfer de datos'
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 3%

---


# Interacción: búfer de datos{#interaction-data-buffer}

>[!NOTE]
>
>Algunas configuraciones sólo pueden ser realizadas por Adobe para implementaciones alojadas en Adobe. Por ejemplo, para acceder a los archivos de configuración de instancia y servidor. Para obtener más información sobre las diferentes implementaciones, consulte la sección [Hosting models](../../installation/using/hosting-models.md) o [esta página](../../installation/using/capability-matrix.md).

En Adobe Campaign, se ha introducido una **zona de búfer de datos** en el módulo Interacción. Esto le permite **aumentar el rendimiento** de la interacción de entrada desincronizando los cálculos de oferta y existencias.

Solo se refiere a la interacción de entrada, ya sea por una llamada (con o sin datos de llamada) o por una actualización de estado (updateStatus).

Para evitar una cola al escribir propuestas relacionadas con un destinatario, un nuevo proceso w genera una **zona de búfer de datos** que permite que las propuestas se **escriban asincrónicamente**. Esta zona del búfer de datos se lee y vacía periódicamente. El período predeterminado es de aproximadamente un segundo.Por lo tanto, se agrupa la redacción de propuestas.

La zona del búfer de datos **configuración** se puede realizar en el archivo de configuración de la instancia (config-Instance.xml).

>[!NOTE]
>
>Cualquier cambio realizado en la configuración requiere un reinicio del servidor web (Apache:IIS) y de los procesos de Adobe Campaign.\
>Después de configurar la zona del búfer de datos, asegúrese de que hay una configuración de hardware adaptada disponible. (cantidad de memoria presente).

Después de configurar la zona del búfer de datos, asegúrese de que hay una configuración de hardware adaptada disponible. (cantidad de memoria presente).

La definición de un demonio de escritura (proceso denominado: interacción) es la siguiente:

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

Si utiliza Interacción entrante, el atributo @autostart debe ser &quot;true&quot; para iniciar automáticamente el proceso cuando se inicie el servidor de Adobe Campaign.

Detalles del argumento:

```
 args: Start-up parameters 
 autoStart: Automatic start Default: false 
 callDataSize: Max. number of characters stored in the shared memory for call data
 Default: 0 
 initScript: ID of JavaScript to execute when starting the process 
 maxProcessMemoryAlertMb: Alert concerning the amount of RAM consumed (in Mb) by a given process Default: 1800 
 maxProcessMemoryWarningMb: Warning concerning the amount of RAM consumed (in Mb) by a given process Default: 1600 
 maxSharedEntries: Max. number of events stored in the shared memory. Default: 25000 
 nextOffersSize: Maximum number of eligible offers sorted right after propositions, to be stored for statistics Default: 0 
 processRestartTime: Time of the day when the process is automatically restartedDefault: '06:00:00' 
 runLevel: Priority at start Default: 10 
 targetKeySize: Max. number of characters stored in the shared memory for identifying individuals Default: 16 
```

