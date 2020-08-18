---
title: Actualización
seo-title: Actualización
description: Actualización
seo-description: null
page-status-flag: never-activated
uuid: f24552d4-6bdf-411c-a1f2-b8f339c311f4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: f8e3633d-7232-44a5-842b-1a70c4f2bca2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5598682078a8fd3c8d9ecdca083f3a310c48f5f0
workflow-type: tm+mt
source-wordcount: '1120'
ht-degree: 1%

---


# Actualización{#upgrading}

Antes de iniciar el proceso de actualización, determine y confirme a qué versión de Adobe Campaign se va a actualizar y consulte las [Notas](../../rn/using/latest-release.md) de la versión.

>[!CAUTION]
>
>Se recomienda encarecidamente realizar una copia de seguridad de la base de datos en cada instancia antes de la actualización. Para obtener más información, consulte [Copia de seguridad](../../production/using/backup.md).\
>Para realizar una actualización, asegúrese de que tiene la capacidad y los permisos para acceder a instancias y registros.

>[!NOTE]
>
>Consulte también la guía [de](../../installation/using/general-architecture.md) instalación y la introducción de la actualización [de la](https://helpx.adobe.com/es/campaign/kb/acc-build-upgrade.html) compilación.

## En Windows {#in-windows}

Para actualizar Adobe Campaign en una nueva versión al enviar una nueva compilación, se debe aplicar el siguiente procedimiento en Windows:

* [Cerrar servicios](#shut-down-services),
* [Actualice la aplicación](#upgrade-the-adobe-campaign-server-application)de servidor de Adobe Campaign,
* [Sincronizar recursos](#synchronize-resources),
* [Reinicie los servicios](#restart-services).

Para saber cómo actualizar la consola de cliente, consulte [esta sección](../../installation/using/client-console-availability-for-windows.md).

### Cerrar servicios {#shut-down-services}

Para reemplazar todos los archivos con la nueva versión, debe cerrar todas las instancias del servicio nlserver.

1. Cierre los siguientes servicios:

   * Servicios Web (IIS):

      **iisreset /stop**

   * Servicio Adobe Campaign: **net stop nlserver6**
   >[!CAUTION]
   >
   >También debe asegurarse de que el servidor de redirección (webmdl) está detenido, para que el archivo **nlsrvmod.dll** que utiliza IIS pueda reemplazarse por la nueva versión.

1. Compruebe que no hay tareas activas ejecutando el comando **nlserver pdump** . Debe presentarse lo siguiente:

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   Puede utilizar el Administrador de Tareas de Windows para asegurarse de que se detienen todos los procesos.

### Actualización de la aplicación de servidor Adobe Campaign {#upgrade-the-adobe-campaign-server-application}

Para ejecutar el archivo de actualización, siga los pasos siguientes:

1. Ejecute **setup.exe**.

   Para descargar este archivo, vaya a la página de asistencia técnica de Adobe Campaign ( [https://support.neolane.net/](https://support.neolane.net/)) a través del vínculo **Centro** de descargas.

1. Seleccione el modo de instalación: elegir **[!UICONTROL Update or repair]**
1. Haga clic **[!UICONTROL Next]** .
1. Haga clic **[!UICONTROL Finish]** .

   A continuación, el programa de instalación copia los nuevos archivos.

1. Una vez finalizada la operación, haga clic en **[!UICONTROL Finish]** .

### Sincronizar recursos {#synchronize-resources}

Utilice la siguiente línea de comandos:

**nlserver config -postupgrade -allinstance**

Esto le permitirá realizar las siguientes operaciones:

* Sincronizar recursos,
* esquemas de actualización,
* actualice la base de datos.

>[!NOTE]
>
>Esta operación debe realizarse una sola vez y solo en un servidor de aplicaciones (**servidor web**).

A continuación, compruebe si la sincronización ha generado errores o advertencias. Para obtener más información sobre esto, consulte [Resolución de conflictos](#resolving-upgrade-conflicts)de actualización.

### Reiniciar servicios {#restart-services}

Los servicios que se reiniciarán son:

* Servicios Web (IIS):

   **iisreset /inicio**

* Servicio Adobe Campaign: **net inicio nlserver6**

## En Linux {#in-linux}

Para actualizar Adobe Campaign en una nueva versión cuando se entrega una nueva compilación, el procedimiento para Linux es el siguiente:

* [Obtener paquetes](#obtain-updated-packages)actualizados,
* [Realizar una actualización](#perform-an-update),
* [Reinicie el servidor](#reboot-the-web-server)web.

Para saber cómo actualizar la consola de cliente, consulte [esta sección](../../installation/using/client-console-availability-for-linux.md).

>[!NOTE]
>
>A partir de la compilación 8757, la biblioteca de terceros ya no es necesaria.

### Obtener paquetes actualizados {#obtain-updated-packages}

Inicio recuperando los dos paquetes actualizados de Adobe Campaign: vaya a la página de asistencia técnica de Adobe Campaign ( [https://support.neolane.net/](https://support.neolane.net/)) a través del vínculo **Centro** de descargas.

El archivo es **nlserver6-v7-XXX.rpm**

### Realizar una actualización {#perform-an-update}

* Distribución basada en RPM (RedHat, SuSe)

   Para instalarlos, ejecute como root:

   ```
   $rpm -Uvh nlserver6-v7-XXXX.rpm
   ```

   donde XXX es la versión del archivo.

   El archivo rpm tiene dependencias en paquetes que puede encontrar en distribuciones de CentOS/Red Hat. Si no desea utilizar algunas de estas dependencias, puede que tenga que utilizar la opción &quot;nodeps&quot; de rpm:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

* Distribución basada en DEB (Debian)

   Para instalarlos, ejecute como root:

   ```
   dpkg -i nlserver6-v7-XXXX-amd64_debX.deb
   ```

>[!NOTE]
>
>Los procedimientos de instalación completos se detallan en [esta sección](../../installation/using/installing-campaign-standard-packages.md). Los recursos se sincronizan automáticamente, pero es necesario asegurarse de que no se produzca ningún error. Para obtener más información sobre esto, consulte [Resolución de conflictos](#resolving-upgrade-conflicts)de actualización.

### Reinicie el servidor Web {#reboot-the-web-server}

Debe cerrar Apache para que la nueva biblioteca sea aplicable.

Para ello, ejecute el siguiente comando:

```
/etc/init.d/apache stop
```

>[!CAUTION]
>
>* Es posible que la secuencia de comandos se llame **httpd** en lugar de **apache**.
>* DEBE ejecutar este comando hasta que obtenga la siguiente respuesta:
   >Esta operación es necesaria para que Apache aplique la nueva biblioteca.

>



A continuación, reinicie Apache:

```
/etc/init.d/apache start
```

## Resolución de conflictos de actualización {#resolving-upgrade-conflicts}

Durante la sincronización de recursos, el comando **postupgrade** permite detectar si la sincronización ha generado errores o advertencias.

### Vista del resultado de sincronización {#view-the-synchronization-result}

Existen dos formas de ver el resultado de la sincronización:

* En la interfaz de la línea de comandos, los errores se materializan con un triple elemento **>>>** y la sincronización se detiene automáticamente. Las advertencias son materializadas por un doble chevron **>>** y deben resolverse una vez finalizada la sincronización. Al final de la posactualización, se muestra un resumen en el símbolo del sistema. Puede tener este aspecto:

   ```
   2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
   2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   Si la advertencia se refiere a un conflicto de recursos, se requiere la atención del usuario para resolverlo.

* El archivo de registro **postupgrade_`<server version number>_<time of postupgrade>`.log** contiene el resultado de la sincronización. Está disponible de forma predeterminada en el siguiente directorio: **`<installation directory>/var/<instance/postupgrade`**. Los errores y las advertencias se indican mediante los atributos de error y advertencia.

### Resolución de conflictos {#resolving-conflicts}

Para resolver conflictos, aplique el siguiente proceso:

1. En el árbol de Adobe Campaign, vaya a **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** .
1. Seleccione el conflicto que desee resolver en la lista.

Existen tres maneras de resolver un conflicto:

* **[!UICONTROL Declare as resolved]** :: requiere la intervención previa del usuario.
* **[!UICONTROL Accept the new version]** :: recomendado si el usuario no ha cambiado los recursos proporcionados con Adobe Campaign.
* **[!UICONTROL Keep the current version]** :: significa que se rechaza la actualización.

   >[!CAUTION]
   >
   >Si selecciona este modo de resolución, es posible que no se beneficie de las correcciones en la nueva versión.

Si ha elegido resolver el conflicto manualmente, siga este procedimiento:

1. En la sección inferior de la ventana, busque la cadena de **_conflicto_** para localizar las entidades con conflictos. La entidad instalada con la nueva versión contiene el **nuevo** argumento; la entidad que coincide con la versión anterior contiene el argumento **cus** .

   ![](assets/s_ncs_production_conflict002.png)

1. Elimine la versión que no desee conservar. Elimine la cadena **_Conflict_argumento_** de la entidad que mantiene.

   ![](assets/s_ncs_production_conflict003.png)

1. Vaya al conflicto que ha resuelto. Click the **[!UICONTROL Actions]** icon and select **[!UICONTROL Declare as resolved]** .
1. Guarde los cambios: el conflicto ya está resuelto.

### Prácticas recomendadas {#best-practices}

Se puede vincular un error de actualización a la configuración de la base de datos. Asegúrese de que las configuraciones realizadas por el administrador técnico y el administrador de la base de datos sean compatibles.

Por ejemplo, una base de datos Unicode no sólo debe autorizar el almacenamiento de datos LATIN1, etc.

## Avisar a las consolas de cliente de la actualización disponible {#warn-the-client-consoles-of-the-available-update}

### En Windows {#in-windows-1}

En el equipo en el que está instalado el servidor de aplicaciones (**nlserver web**) de Adobe Campaign, descargue y copie el archivo

**setup-client-6.XXXX.exe**

en **[path de la aplicación]**datakitnlongjsp

La próxima vez que se conecten las consolas de cliente, una ventana informará a los usuarios sobre la disponibilidad de una actualización y les oferta la posibilidad de descargarlas e instalarlas.

>[!NOTE]
>
>Asegúrese de que el usuario de IIS_XPG tiene los derechos de lectura adecuados para este archivo de instalación y consulte la guía [de](../../installation/using/general-architecture.md) instalación para obtener más información.

### En Linux {#in-linux-1}

En el equipo en el que está instalado el servidor de aplicaciones de Adobe Campaign (**servidor Web**), recupere el siguiente paquete:

**setup-client-6.XXXX.exe**

y cópiela, guardando como **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

La próxima vez que se conecten las consolas de cliente, una ventana informará a los usuarios sobre la disponibilidad de una actualización y les oferta la posibilidad de descargarlas e instalarlas.

>[!NOTE]
>
>Asegúrese de que el usuario de Apache tiene los derechos de lectura correspondientes para este archivo de instalación y consulte la guía [de](../../installation/using/general-architecture.md) instalación para obtener más información.

