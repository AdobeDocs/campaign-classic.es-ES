---
solution: Campaign Classic
product: campaign
title: Migración en Linux para Adobe Campaign v7
description: Migración en Linux para Adobe Campaign v7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1890'
ht-degree: 1%

---


# Migración en Linux para Adobe Campaign v7{#migrating-in-linux-for-adobe-campaign-v}

## Procedimiento general {#general-procedure}

Los pasos de migración en Linux son los siguientes:

1. Detener servicios: consulte [Parada de servicio](#service-stop).
1. Guarde la base de datos: consulte [Realice una copia de seguridad de la base de datos y de la instalación existente](#back-up-the-database-and-the-existing-installation).
1. Desinstale los paquetes de versiones anteriores de Adobe Campaign: consulte [Desinstalación de paquetes de la versión anterior de Adobe Campaign](#uninstalling-adobe-campaign-previous-version-packages).
1. Migrar la plataforma: consulte [Implementación de Adobe Campaign v7](#deploying-adobe-campaign-v7).
1. Servicio de reinicio: consulte [Reinicio de servicios](#re-starting-services).

## Detención de servicio {#service-stop}

Primero, detener todos los procesos con acceso a la base de datos en todos los equipos involucrados.

1. Inicie sesión como **raíz**.
1. Todos los servidores que utilizan el módulo de redirección (**webmdl** servicio) deben detenerse. Para Apache, ejecute el siguiente comando:

   ```
   /etc/init.d/apache2 stop
   ```

1. Vuelva a iniciar sesión como **raíz**.
1. Detenga los servicios de la versión anterior de Adobe Campaign en todos los servidores.

   ```
   /etc/init.d/nlserver6 stop
   ```

   Si va a realizar la migración desde v5.11, ejecute el siguiente comando:

   ```
   /etc/init.d/nlserver5 stop
   ```

1. Asegúrese de que los servicios de Adobe Campaign se detienen en cada servidor.

   ```
   ps waux | grep nlserver
   ```

   La lista de los procesos activos se muestra junto con su ID (PID).

1. Si uno o más procesos de Adobe Campaign siguen activos o bloqueados al cabo de unos minutos, matarlos.

   ```
   killall nlserver
   ```

1. Si algunos procesos siguen activos al cabo de unos minutos, puede forzarlos a cerrar mediante el comando:

   ```
   killall -9 nlserver
   ```

## Realice una copia de seguridad de la base de datos y de la instalación existente {#back-up-the-database-and-the-existing-installation}

El procedimiento depende de la versión anterior de Adobe Campaign.

### Migración desde Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Realice una copia de seguridad de la base de datos de Adobe Campaign.
1. Inicie sesión como **neolane** y realice una copia de seguridad del directorio **nl5** utilizando el siguiente comando:

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >Como medida de precaución, le recomendamos que comprima la carpeta **nl5.back** y la guarde en una ubicación segura que no sea el servidor.

1. Edite **config-`<instance name>`.xml** (en la carpeta **nl5.back**) para evitar que **mta**, **wfserver**, **stat** etc. desde el inicio automático. Por ejemplo, reemplace **autoStart** por **_autoStart** (aún como **neolano**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### Migración desde Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Realice una copia de seguridad de la base de datos de Adobe Campaign.
1. Inicie sesión como **neolane** y realice una copia de seguridad del directorio **nl6** utilizando el siguiente comando:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Como medida de precaución, le recomendamos que comprima la carpeta **nl6.back** y la guarde en una ubicación segura que no sea el servidor.

1. Edite **config-`<instance name>`.xml** (en la carpeta **nl6.back**) para evitar que **mta**, **wfserver**, **stat**, etc. desde el inicio automático. Por ejemplo, reemplace **autoStart** por **_autoStart** (aún como **Adobe Campaign**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### Migración desde Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}

1. Realice una copia de seguridad de la base de datos de Adobe Campaign.
1. Inicie sesión como **neolane** y realice una copia de seguridad del directorio **nl6** utilizando el siguiente comando:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Como medida de precaución, le recomendamos que comprima la carpeta **nl6.back** y la guarde en una ubicación segura que no sea el servidor.

## Desinstalación de paquetes de la versión anterior de Adobe Campaign {#uninstalling-adobe-campaign-previous-version-packages}

El procedimiento depende de la versión anterior de Adobe Campaign.

### Desinstalación de paquetes de Adobe Campaign v5 {#uninstalling-adobe-campaign-v5-packages}

1. Inicie sesión como **raíz**.
1. Identifique los paquetes de Adobe Campaign instalados mediante el siguiente comando.

   * En **Debian**:

      ```
      dpkg -l | grep nl
      ```

      Se muestra la lista de los paquetes instalados:

      ```
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

   * En **Red Hat**:

      ```
      rpm -qa | grep nl
      ```

1. Desinstale los paquetes de Adobe Campaign v5.

   * En **Debian**:

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * En **Red Hat**:

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### Desinstalación de paquetes de Adobe Campaign v6 {#uninstalling-adobe-campaign-v6-packages}

Esta sección muestra cómo desinstalar los paquetes de Adobe Campaign v6.02 o v6.1.

1. Inicie sesión como **raíz**.
1. Identifique los paquetes de Adobe Campaign instalados mediante el siguiente comando.

   * En **Debian**:

      ```
      dpkg -l | grep nl
      ```

      Se muestra la lista de los paquetes instalados:

      ```
      ii  nlserver6                       XXXX                     nlserver6-XXXX
      ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
      ```

   * En **Red Hat**:

      ```
      rpm -qa | grep nl
      ```

1. Desinstale los paquetes de Adobe Campaign v6.

   * En **Debian**:

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * En **Red Hat**:

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## Implementación de Adobe Campaign v7 {#deploying-adobe-campaign-v7}

El procedimiento depende de la versión anterior de Adobe Campaign.

### Migración desde Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}

La implementación de Adobe Campaign implica dos etapas:

* Instalación de paquetes de Adobe Campaign v7: esta operación debe realizarse en cada servidor.
* La actualización posterior: este comando debe iniciarse en cada instancia.

Para implementar Adobe Campaign, siga estos pasos:

1. Instale los paquetes más recientes de Adobe Campaign v7 con el siguiente comando:

   * En **Debian**:

      ```
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

   * En **Red Hat**:

      ```
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```
   >[!IMPORTANT]
   >
   >Debe instalar los paquetes correctamente antes de continuar con el siguiente paso.

   >[!NOTE]
   >
   >Al migrar desde v5.11, Adobe Campaign se instala de forma predeterminada en el directorio **/usr/local/neolane/nl6/**.
   >
   >Una vez instalados los paquetes, se muestra el siguiente mensaje: Falta la opción **&#39;WdbcTimeZone&#39;**. Esto es normal.

1. Para que el programa de instalación de la consola de cliente esté disponible, cópielo en el directorio de instalación de Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Para obtener más información sobre cómo instalar Adobe Campaign en Linux, consulte [esta sección](../../installation/using/installing-campaign-standard-packages.md).

1. Modifique el archivo **.bashrd** que coincide con el usuario **neolane**. Inicie sesión como **neolane** y ejecute el siguiente comando:

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >Al iniciar sesión como **neolane**, se muestra el siguiente mensaje: **nl5/env.sh : No existe dicho archivo o directorio**. Esto es normal.

   Al final del archivo, reemplace **nl5/env.sh** por **nl6/env.sh**.

1. Inicie sesión como **root** y prepare la instancia con los siguientes comandos:

   ```
   /etc/init.d/nlserver6 start   
   Starting nlserver6: [  OK  ]
   ```

   ```
   /etc/init.d/nlserver6 stop
   Stopping nlserver6: [  OK  ]
   ```

   >[!NOTE]
   >
   >Estos comandos le permiten crear el sistema de archivos internos de Adobe Campaign v6: **conf** (con los archivos **config-default.xml** y **serverConf.xml**), **var**.

1. Vaya a la carpeta de copia de seguridad **nl5.back** y copie (sobrescriba) los archivos y subcarpetas de configuración de cada instancia. Inicie sesión como **neolane** y ejecute el siguiente comando:

   >[!IMPORTANT]
   >
   >Para el primer comando siguiente, no copie el archivo **config-default.xml**.

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. En los archivos Adobe Campaign v7 **serverConf.xml** y **config-default.xml**, aplique las configuraciones específicas que tenía para Adobe Campaign v5. Para el archivo **serverConf.xml**, utilice el archivo **nl5/conf/serverConf.xml.diff**.

   >[!NOTE]
   >
   >Cuando realice configuraciones de sistema de informes desde Adobe Campaign v5 a Adobe Campaign v7, asegúrese de que las rutas a los directorios físicos conducen a Adobe Campaign v7 y no a Adobe Campaign v5.

1. Dado que la migración no es una instalación genérica, debe forzar el reinicio del servicio **trackinglogd**. Para ello, abra el archivo **nl6/conf/config-default.xml** y asegúrese de que el servicio **trackinglogd** está activado (solo en los servidores de seguimiento/redirección):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Si el servicio **trackinglogd** no se inicia en el servidor de seguimiento, no se reenviará ninguna información de seguimiento.

1. Vuelva a cargar la configuración de Adobe Campaign v7 con el siguiente comando:

   ```
   nlserver config -reload
   ```

1. Inicio el proceso posterior a la actualización utilizando el siguiente comando (aún como **neolane**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >Debe especificar qué zona horaria utilizar como referencia durante la posactualización (mediante la opción **-timezone**). En este caso, utilizamos la zona horaria Europa/París **: &quot;Europa/París&quot;**.

   >[!NOTE]
   >
   >Le recomendamos encarecidamente que actualice su base a &quot;multi timezone&quot;. Para obtener más información sobre las opciones de huso horario, consulte la sección [Husos horarios](../../migration/using/general-configurations.md#time-zones).

>[!IMPORTANT]
>
>Aún no inicio los servicios de Adobe Campaign: aún es necesario realizar cambios en Apache.

### Migración desde Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

La implementación de Adobe Campaign implica dos etapas:

* Instalación de paquetes de Adobe Campaign v7: esta operación debe realizarse en cada servidor.
* La actualización posterior: este comando debe iniciarse en cada instancia.

Para implementar Adobe Campaign, siga estos pasos:

1. Instale los paquetes más recientes de Adobe Campaign v7 con el siguiente comando:

   * En **Debian**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * En **Red Hat**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >Debe instalar los paquetes correctamente antes de continuar con el siguiente paso.

   >[!NOTE]
   >
   >Adobe Campaign v7 está instalado en el mismo directorio de forma predeterminada que Adobe Campaign v6.02: **/usr/local/neolane/nl6/**.

1. Para que el programa de instalación de la consola de cliente esté disponible, cópielo en el directorio de instalación de Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Para obtener más información sobre cómo instalar Adobe Campaign en Linux, consulte [esta sección](../../installation/using/installing-campaign-standard-packages.md).

1. Dado que la migración no es una instalación genérica, debe forzar el reinicio del servicio **trackinglogd**. Para ello, abra el archivo **nl6/conf/config-default.xml** y asegúrese de que el servicio **trackinglogd** está activado (solo en los servidores de seguimiento/redirección):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Si el servicio **trackinglogd** no se inicia en el servidor de seguimiento, no se reenviará ninguna información de seguimiento.

1. Vaya a la carpeta de copia de seguridad **nl6.back** y copie (sobrescriba) los archivos y subcarpetas de configuración de cada instancia. Inicie sesión como **neolane** y ejecute el siguiente comando:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Vuelva a cargar la configuración de Adobe Campaign v7 con el siguiente comando:

   ```
   nlserver config -reload
   ```

1. Inicio el proceso posterior a la actualización utilizando el siguiente comando (aún como **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >El modo &quot;multizona horaria&quot; solo estaba disponible en v6.02 para los motores de base de datos PostgreSQL. Ahora está disponible sin importar la versión del motor de base de datos que se esté utilizando. Le recomendamos encarecidamente que actualice su base a &quot;multi timezone&quot;. Para obtener más información sobre las opciones de huso horario, consulte la sección [Husos horarios](../../migration/using/general-configurations.md#time-zones).

### Migración desde Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-1}

La implementación de Adobe Campaign implica dos etapas:

* Instalación de paquetes de Adobe Campaign v7: esta operación debe realizarse en cada servidor.
* La actualización posterior: este comando debe iniciarse en cada instancia.

Para implementar Adobe Campaign, siga estos pasos:

1. Instale los paquetes más recientes de Adobe Campaign v7 con el siguiente comando:

   * En **Debian**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * En **Red Hat**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >Debe instalar los paquetes correctamente antes de continuar con el siguiente paso.

   >[!NOTE]
   >
   >Adobe Campaign v7 se instala de forma predeterminada en el directorio **/usr/local/neolane/nl6/**.

1. Para que el programa de instalación de la consola de cliente esté disponible, cópielo en el directorio de instalación de Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Para obtener más información sobre cómo instalar Adobe Campaign en Linux, consulte [esta sección](../../installation/using/installing-campaign-standard-packages.md).

1. Vaya a la carpeta de copia de seguridad **nl6.back** y copie (sobrescriba) los archivos y subcarpetas de configuración de cada instancia. Inicie sesión como **neolane** y ejecute el siguiente comando:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Vuelva a cargar la configuración de Adobe Campaign v7 con el siguiente comando:

   ```
   nlserver config -reload
   ```

1. Inicio el proceso posterior a la actualización utilizando el siguiente comando (aún como **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## Migración del servidor de redirección (Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>Esta sección solo se aplica al migrar desde Adobe Campaign v5.11.

En este momento, Apache necesita ser detenido. Consulte: [Detención de servicio](#service-stop).

1. Inicie sesión como **raíz**.
1. Cambie las variables de entorno Apache para que se vinculen al directorio **nl6**.

   * En **Debian**:

      ```
      vi /etc/apache2/envvars
      ```

   * En **Red Hat**:

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. A continuación, ejecute los siguientes comandos:

   * En **Debian**:

      En el archivo **nlsrv.load**, reemplace **nl5** por **nl6**.

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      Elimine el vínculo del archivo **nlsrv.conf** y cree uno nuevo.

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * En **Red Hat**:

      Vaya al directorio **/usr/local/apache2/conf**, edite el archivo **http.conf** y reemplace **nl5** por **nl6** en las siguientes líneas.

      En **RHEL 7/Debian 8**:

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Vaya al archivo **alias.conf** y reemplace todo **nl5** por **nl6**. Para hacerlo en Debian, ejecute el siguiente comando:

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## Zonas de seguridad {#security-zones}

Si va a realizar la migración desde la versión 6.02 o anterior, debe configurar las zonas de seguridad antes de iniciar los servicios. Para obtener más información, consulte [Seguridad](../../migration/using/general-configurations.md#security).

## Reinicio de servicios {#re-starting-services}

El procedimiento depende de la versión anterior de Adobe Campaign.

### Migración desde Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-2}

En los archivos **config-`<instance name>`.xml**, reactive el inicio automático de **mta**, **wfserver**, **stat**, etc. servicios.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="localhost"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Servicios de inicio Apache y Adobe Campaign en cada uno de los siguientes servidores:

1. Servidor de seguimiento y redirección.
1. Servidor intermediario.
1. Servidor de marketing.

Antes de continuar con el paso siguiente, ejecute una prueba completa de la nueva instalación, asegúrese de que no haya regresiones y de que todo funcione siguiendo todas las recomendaciones de la sección [Configuraciones generales](../../migration/using/general-configurations.md).

### Migración desde Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

En los archivos **config-`<instance name>`.xml**, reactive el inicio automático de **mta**, **wfserver**, **stat**, etc. servicios.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="myStatServer"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Servicios de inicio Apache y Adobe Campaign en cada uno de los siguientes servidores:

1. Servidor de seguimiento y redirección.
1. Servidor intermediario.
1. Servidor de marketing.

Pruebe completamente la nueva instalación, verifique que no retroceda y asegúrese de que todo funciona correctamente siguiendo todas las recomendaciones de la sección [Configuraciones generales](../../migration/using/general-configurations.md).

### Migración desde Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-2}

Servicios de inicio Apache y Adobe Campaign en cada uno de los siguientes servidores:

1. Servidor de seguimiento y redirección.
1. Servidor intermediario.
1. Servidor de marketing.

Pruebe completamente la nueva instalación, verifique que no retroceda y asegúrese de que todo funciona correctamente siguiendo todas las recomendaciones de la sección [Configuraciones generales](../../migration/using/general-configurations.md).

## Eliminación y limpieza de Adobe Campaign v5 {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>Esta sección solo se aplica al migrar desde Adobe Campaign v5.11.

Antes de eliminar y limpiar la instalación de Adobe Campaign v5, debe aplicar las siguientes recomendaciones:

* Consiga que los equipos funcionales realicen una comprobación completa de la nueva instalación.
* Solo debe desinstalar Adobe Campaign v5 cuando esté seguro de que no es necesario realizar ninguna reversión.

Elimine el directorio **nl5.back**. Inicie sesión como **neolane** y ejecute el siguiente comando:

```
su - neolane
rm -rf nl5.back
```

Vuelva a poner en inicio el servidor.
