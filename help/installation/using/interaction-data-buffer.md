---
product: campaign
title: 'Interacción: búfer de datos'
description: 'Interacción: búfer de datos'
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 7250b885-0606-466a-bfc2-6dd3cc5a012d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 14%

---

# Interacción: búfer de datos{#interaction-data-buffer}



Se puede configurar una zona de búfer de datos para aumentar el rendimiento de interacción entrante desincronizando los cálculos de propuesta de oferta. Esta configuración se debe llevar a cabo en el archivo de configuración propio de la instancia (config-Instance.xml).

En Adobe Campaign, una **zona de búfer de datos** se ha introducido en el módulo de interacción. Esto le permite **aumentar rendimiento** de interacción entrante desincronizando los cálculos de stock y oferta.

Solo afecta a la interacción entrante, ya sea mediante una llamada (con o sin datos de llamada) o mediante una actualización de estado (updateStatus).

Para evitar una cola al escribir propuestas relacionadas con un destinatario, un nuevo proceso w genera un **zona de búfer de datos** que permite que las propuestas se **escrito asincrónicamente**. Esta zona de búfer de datos se lee y se vacía periódicamente. El periodo predeterminado es de aproximadamente un segundo. Por lo tanto, la escritura de propuestas se agrupa.

>[!NOTE]
>
>Este parámetro es esencial si se utiliza interacción con una arquitectura distribuida.

Zona de búfer de datos **configuración** se puede realizar en el archivo de configuración de la instancia (config-Instance.xml).

>[!CAUTION]
>
>Algunas configuraciones solo se pueden realizar mediante el Adobe para implementaciones alojadas por el Adobe. Por ejemplo, para acceder a los archivos de configuración del servidor y de la instancia. Para obtener más información sobre las distintas implementaciones, consulte la [Modelos de alojamiento](../../installation/using/hosting-models.md) o a [esta página](../../installation/using/capability-matrix.md).
>
>Cualquier cambio realizado en la configuración requiere el reinicio del servidor web (Apache:IIS) y de los procesos de Adobe Campaign.\
>Después de configurar la zona de búfer de datos, asegúrese de que haya disponible una configuración de hardware adaptada. (cantidad de memoria presente).


Después de configurar la zona de búfer de datos, asegúrese de que haya disponible una configuración de hardware adaptada. (cantidad de memoria presente).

La definición de un daemon de escritura (proceso denominado: interaction) es la siguiente:

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

Si utiliza interacción entrante, el atributo @autostart debe ser &quot;true&quot; para iniciar automáticamente el proceso cuando se inicie el servidor de Adobe Campaign.

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
