---
solution: Campaign Classic
product: campaign
title: Actualización a una nueva compilación
description: Conozca los pasos técnicos para actualizar a una nueva versión
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: ae4b2ba6db140cdfb9ec4a38231fcc3e54b1478c
workflow-type: tm+mt
source-wordcount: '1159'
ht-degree: 2%

---


# Actualización a una nueva compilación (local){#upgrading}

Antes de iniciar el proceso de actualización, determine y confirme a qué versión de Adobe Campaign se va a actualizar y consulte las [Notas de la versión](../../rn/using/latest-release.md) .

>[!IMPORTANT]
>
>Se recomienda realizar una copia de seguridad de la base de datos en cada instancia antes de actualizar. Para obtener más información, consulte [Copia de seguridad](../../production/using/backup.md).\
>Para realizar una actualización, asegúrese de que tiene la capacidad y los permisos para acceder a instancias y registros.

>[!NOTE]
>
>Consulte también la [guía de instalación](../../installation/using/general-architecture.md) y la [actualización de compilación](https://helpx.adobe.com/es/campaign/kb/acc-build-upgrade.html) introducción.

## Windows {#in-windows}

Para actualizar Adobe Campaign en una nueva versión al enviar una nueva compilación, se debe aplicar el siguiente procedimiento en Windows:

* [Apagar servicios](#shut-down-services),
* [Actualice la aplicación](#upgrade-the-adobe-campaign-server-application) de servidor de Adobe Campaign,
* [Sincronizar recursos](#synchronize-resources),
* [Reinicie los servicios](#restart-services).

Para saber cómo actualizar la consola del cliente, consulte [esta sección](../../installation/using/client-console-availability-for-windows.md).

### Apagar servicios {#shut-down-services}

Para reemplazar todos los archivos con la nueva versión, debe cerrar todas las instancias del servicio nlserver.

1. Apague los siguientes servicios:

   * Servicios Web (IIS):

      **iisreset /stop**

   * Servicio de Adobe Campaign: **net stop nlserver6**
   >[!IMPORTANT]
   >
   >También debe asegurarse de que el servidor de redirección (webmdl) esté detenido, de modo que el archivo **nlsrvmod.dll** utilizado por IIS pueda reemplazarse por la nueva versión.

1. Compruebe que no haya tareas activas ejecutando el comando **nlserver pdump**. Debería plantearse lo siguiente:

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   Puede usar el Administrador de tareas de Windows para asegurarse de que todos los procesos estén detenidos.

### Actualizar la aplicación de servidor de Adobe Campaign {#upgrade-the-adobe-campaign-server-application}

Para ejecutar el archivo de actualización, siga los siguientes pasos:

1. Ejecute **setup.exe**.

   Para descargar este archivo, conéctese al [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html) con sus credenciales de usuario. Obtenga más información sobre la distribución de software en [esta página](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

1. Seleccione el modo de instalación: elija **[!UICONTROL Update or repair]**
1. Haga clic en **[!UICONTROL Next]** .
1. Haga clic en **[!UICONTROL Finish]** .

   A continuación, el programa de instalación copia los nuevos archivos.

1. Una vez finalizada la operación, haga clic en **[!UICONTROL Finish]** .

### Sincronizar recursos {#synchronize-resources}

Utilice la siguiente línea de comandos:

**nlserver config -postupgrade -allinstances**

Esto le permite llevar a cabo las siguientes operaciones:

* Sincronizar recursos,
* actualizar esquemas,
* actualice la base de datos.

>[!NOTE]
>
>Esta operación debe realizarse solo una vez y solo en un servidor de aplicaciones (**nlserver web**).

A continuación, compruebe si la sincronización ha generado errores o advertencias. Para obtener más información, consulte [Resolver conflictos de actualización](#resolving-upgrade-conflicts).

### Reiniciar servicios {#restart-services}

Los servicios que se van a reiniciar son:

* Servicios Web (IIS):

   **iisreset /start**

* Servicio de Adobe Campaign: **net start nlserver6**

## Linux {#in-linux}

Para actualizar Adobe Campaign en una nueva versión cuando se entrega una nueva compilación, el procedimiento para Linux es el siguiente:

* [Obtenga paquetes](#obtain-updated-packages) actualizados,
* [Realizar una actualización](#perform-an-update),
* [Reinicie el servidor](#reboot-the-web-server) web.

[Obtenga más información sobre la disponibilidad](../../installation/using/client-console-availability-for-windows.md) de la consola de cliente.

>[!NOTE]
>
>A partir de la versión 8757, la biblioteca de terceros ya no es necesaria.

### Obtener paquetes actualizados {#obtain-updated-packages}

Comience recuperando ambos paquetes actualizados de Adobe Campaign: conéctese al [portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) con sus credenciales de usuario. Obtenga más información sobre la distribución de software en [esta página](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

El archivo es **nlserver6-v7-XXX.rpm**

### Realizar una actualización {#perform-an-update}

* Distribución basada en RPM (RedHat, SuSe)

   Para instalarlos, ejecute como raíz:

   ```
   $rpm -Uvh nlserver6-v7-XXXX.rpm
   ```

   donde XXX es la versión del archivo.

   El archivo rpm tiene dependencias en paquetes que puede encontrar en distribuciones de CentOS/Red Hat. Si no desea utilizar algunas de estas dependencias, es posible que tenga que utilizar la opción &quot;nodeps&quot; de rpm:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

* Distribución basada en DEB (Debian)

   Para instalarlos, ejecute como raíz:

   ```
   dpkg -i nlserver6-v7-XXXX-amd64_debX.deb
   ```

>[!NOTE]
>
>Los procedimientos de instalación completos se detallan en [esta sección](../../installation/using/installing-campaign-standard-packages.md). Los recursos se sincronizan automáticamente, pero debe asegurarse de que no se hayan producido errores. Para obtener más información, consulte [Resolver conflictos de actualización](#resolving-upgrade-conflicts).

### Reinicie el servidor web {#reboot-the-web-server}

Debe cerrar Apache para que la nueva biblioteca sea aplicable.

Para ello, ejecute el siguiente comando:

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* Su script puede llamarse **httpd** en lugar de **apache**.
>* DEBE ejecutar este comando hasta que obtenga la siguiente respuesta:

   >
   >   
   Esta operación es necesaria para que Apache aplique la nueva biblioteca.


A continuación, reinicie Apache:

```
/etc/init.d/apache start
```

## Resolución de conflictos de actualización {#resolving-upgrade-conflicts}

Durante la sincronización de recursos, el comando **postupgrade** permite detectar si la sincronización ha generado errores o advertencias.

### Ver el resultado de la sincronización {#view-the-synchronization-result}

Existen dos formas de ver el resultado de la sincronización:

* En la interfaz de la línea de comandos, los errores se materializan mediante una triple cadena **>>** y la sincronización se detiene automáticamente. Las advertencias se materializan mediante una cadena **>** doble y deben resolverse una vez finalizada la sincronización. Al final de la actualización posterior, se muestra un resumen en el símbolo del sistema. Puede tener este aspecto:

   ```
   2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
   2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   Si la advertencia se refiere a un conflicto de recursos, es necesario que el usuario preste atención para resolverlo.

* El archivo de registro **postupgrade_`<server version number>_<time of postupgrade>`.log** contiene el resultado de la sincronización. Está disponible de forma predeterminada en el siguiente directorio: **`<installation directory>/var/<instance/postupgrade`**. Los errores y las advertencias se indican mediante los atributos de error y advertencia.

### Resolución de conflictos {#resolving-conflicts}

Para resolver conflictos, siga el siguiente proceso:

1. En el árbol de Adobe Campaign, vaya a **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** .
1. Seleccione el conflicto que desee resolver en la lista.

Hay tres maneras de resolver un conflicto:

* **[!UICONTROL Declare as resolved]** : requiere la intervención previa del usuario.
* **[!UICONTROL Accept the new version]** : recomendado si el usuario no ha cambiado los recursos proporcionados con Adobe Campaign.
* **[!UICONTROL Keep the current version]** : significa que la actualización se rechaza.

   >[!IMPORTANT]
   >
   >Si selecciona este modo de resolución, es posible que no se beneficie de las correcciones en la nueva versión.

Si decide resolver el conflicto manualmente, proceda de la siguiente manera:

1. En la sección inferior de la ventana, busque la cadena **_conflict_** para localizar las entidades con conflictos. La entidad instalada con la nueva versión contiene el argumento **new**, la entidad que coincide con la versión anterior contiene el argumento **cus**.

   ![](assets/s_ncs_production_conflict002.png)

1. Elimine la versión que no desee conservar. Elimine la cadena **_conflict_discussion_** de la entidad que mantiene.

   ![](assets/s_ncs_production_conflict003.png)

1. Vaya al conflicto que ha resuelto. Haga clic en el icono **[!UICONTROL Actions]** y seleccione **[!UICONTROL Declare as resolved]** .
1. Guarde los cambios: el conflicto ya está resuelto.

### Prácticas recomendadas {#best-practices}

Se puede vincular un error de actualización a la configuración de la base de datos. Asegúrese de que las configuraciones realizadas por el administrador técnico y el administrador de la base de datos sean compatibles.

Por ejemplo, una base de datos Unicode no solo debe autorizar el almacenamiento de datos LATIN1, etc.

## Advertir a las consolas de cliente de la actualización disponible {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

En el equipo en el que está instalado el servidor de aplicaciones de Adobe Campaign (**nlserver web**), descargue y copie el archivo

**setup-client-6.XXXX.exe**

en **[ruta de la aplicación]**datakitnlongjsp

La próxima vez que se conecten consolas de cliente, una ventana informará a los usuarios sobre la disponibilidad de una actualización y les ofrecerá la posibilidad de descargarlas e instalarlas.

>[!NOTE]
>
>Asegúrese de que el usuario IIS_XPG tiene los derechos de lectura adecuados para este archivo de instalación y consulte la [guía de instalación](../../installation/using/general-architecture.md) para obtener más información.

### Linux {#in-linux-1}

En el equipo donde está instalado el servidor de aplicaciones de Adobe Campaign (**nlserver web**), recupere el siguiente paquete:

**setup-client-6.XXXX.exe**

y cópielo, guardando como **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

La próxima vez que se conecten consolas de cliente, una ventana informará a los usuarios sobre la disponibilidad de una actualización y les ofrecerá la posibilidad de descargarlas e instalarlas.

>[!NOTE]
>
>Asegúrese de que el usuario de Apache tiene los derechos de lectura adecuados para este archivo de instalación y consulte la [guía de instalación](../../installation/using/general-architecture.md) para obtener más información.

