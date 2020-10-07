---
title: Parámetros adicionales
seo-title: Parámetros adicionales
description: Parámetros adicionales
seo-description: null
page-status-flag: never-activated
uuid: c223c84a-f8fd-43d3-9deb-b1c19d442c65
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 1b2ae224-8406-4506-b589-6e5f6631e87f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 2%

---


# Parámetros adicionales{#additional-parameters}

## Definición de parámetros {#definition-of-parameters}

La plataforma Adobe Campaign oferta dos parámetros de seguimiento web de tipo TRANSACTION como estándar:

* **importe**: representa el importe de una transacción,
* **artículo**: representa el número de artículos de una transacción.

Estos parámetros se definen en el esquema **nms:webTrackingLog** y son algunos de los indicadores que se ven en sistema de informes.

Para definir parámetros adicionales, debe extender este esquema.

**Ejemplo**:

```
<srcSchema extendedSchema="nms:webTrackingLog" label="Web Tracking"
           mappingType="sql" name="webTrackingLog" 
           namespace="cus" xtkschema="xtk:srcSchema">

  <element name="webTrackingLog">
    <attribute desc="Payment method" label="Payment method" length="10" name="mode" type="string"/>
    <attribute desc="Offer code" label="Offer code" length="5" name="code" type="string"/>
  </element>
</srcSchema>
```

Puede mostrar los valores de estos parámetros configurando la lista del registro de seguimiento (de un envío o destinatario).

## Configuración del servidor de redirección {#redirection-server-configuration}

En la configuración del servidor, puede definir el número máximo de caracteres que se deben tener en cuenta para los parámetros de seguimiento web.

>[!IMPORTANT]
>
>El aumento del número máximo de caracteres que se deben tener en cuenta puede afectar al rendimiento del seguimiento web de la plataforma.

Para ello, modifique el atributo **webTrackingParamSize** del **`<trackinglogd>`** elemento en el **archivo serverConf.xml** . Este archivo se guarda en el subdirectorio **conf** del directorio de instalación de Adobe Campaign.

**Ejemplo**:

El valor predeterminado es de 64 caracteres. Este valor permite tener en cuenta la **cantidad** y los parámetros estándar del **artículo** (&quot;amount=xxxxxxxx&amp;article=xxxxxxxx&quot;).

Teniendo en cuenta los dos parámetros (tamaño del nombre + tamaño del valor) indicados en el ejemplo de esquema de extensión anterior, puede modificar la configuración para tener en cuenta 100 caracteres (&quot;amount=xxxxxxxx&amp;article=xxxxxxxx&amp;mode=xxxxxxxxxx&amp;code=xxxx&quot;).

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

Cuando se haya modificado la configuración, deberá:

* Detenga el servidor web que aloja el módulo de redirección (Apache, IIS, etc.),
* Detenga el servidor de Adobe Campaign: **net stop nlserver6** en Windows, **/etc/init.d/nlserver6 stop** en Linux,

   >[!NOTE]
   >
   >A partir de 20.1, se recomienda utilizar el siguiente comando en su lugar (para Linux): **syctl stop nlserver**

* En Linux, elimine los segmentos de memoria compartida mediante el **comando ipcrm** ,
* Reinicie el servidor de Adobe Campaign: **net inicio nlserver6** en Windows, **/etc/init.d/nlserver6 inicio** en Linux,

   >[!NOTE]
   >
   >A partir de 20.1, se recomienda utilizar el siguiente comando en su lugar (para Linux): **servidorDeinicioDelSistema**

* Reinicie el servidor web.

**Ejemplo**: teniendo en cuenta la configuración en Linux.

```
adobe@selma:~$ systemctl stop nlserver
adobe@selma:~$ systemctl stop apache2
adobe@selma:~$ ipcs shm

------ Shared Memory Segments --------
key        shmid      owner      perms      bytes      nattch     status      
0x52020679 2097153    adobe   666        93608      8                       

------ Semaphore Arrays --------
key        semid      owner      perms      nsems     
0x52020678 4227081    adobe   666        1         

------ Message Queues --------
key        msqid      owner      perms      used-bytes   messages    

adobe@selma:~$ ipcrm shm 2097153                             
1 resource(s) deleted
adobe@selma:~$ systemctl start nlserver
adobe@selma:~$ systemctl start apache2
```

>[!NOTE]
>
>Para Linux, si aumenta el tamaño de los parámetros **webTrackingParamSize** o **maxSharedLogs** , es posible que tenga que aumentar el tamaño de la memoria compartida (SHM).

