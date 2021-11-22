---
product: campaign
title: Migración en Linux para Adobe Campaign v7
description: Migración en Linux para Adobe Campaign v7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 9dc0699c-0fbf-4f8e-81f7-8ca3d7e98798
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1890'
ht-degree: 1%

---

# Migración en Linux para Adobe Campaign v7{#migrating-in-linux-for-adobe-campaign-v}

![](../../assets/v7-only.svg)

## Procedimiento general {#general-procedure}

Los pasos de migración en Linux son los siguientes:

1. Detener servicios: see [Interrupción del servicio](#service-stop).
1. Guarde la base de datos: see [Haga una copia de seguridad de la base de datos y la instalación existente](#back-up-the-database-and-the-existing-installation).
1. Desinstale los paquetes de versiones anteriores de Adobe Campaign: see [Desinstalación de paquetes de versiones anteriores de Adobe Campaign](#uninstalling-adobe-campaign-previous-version-packages).
1. Migrar la plataforma: consulte [Implementación de Adobe Campaign v7](#deploying-adobe-campaign-v7).
1. Reiniciar servicio: consulte [Reinicio de servicios](#re-starting-services).

## Interrupción del servicio {#service-stop}

En primer lugar, detenga todos los procesos con acceso a la base de datos en todos los equipos correspondientes.

1. Iniciar sesión como **root**.
1. Todos los servidores que utilizan el módulo de redirección (**webmdl** ). Para Apache, ejecute el siguiente comando:

   ```
   /etc/init.d/apache2 stop
   ```

1. Inicie sesión de nuevo como **root**.
1. Detenga los servicios de la versión anterior de Adobe Campaign en todos los servidores.

   ```
   /etc/init.d/nlserver6 stop
   ```

   Si va a migrar desde la versión 5.11, ejecute el siguiente comando:

   ```
   /etc/init.d/nlserver5 stop
   ```

1. Asegúrese de que los servicios de Adobe Campaign se detengan en cada servidor.

   ```
   ps waux | grep nlserver
   ```

   La lista de procesos activos se muestra junto con su ID (PID).

1. Si uno o más procesos de Adobe Campaign siguen activos o bloqueados después de unos minutos, mátelos.

   ```
   killall nlserver
   ```

1. Si algunos procesos siguen activos después de unos minutos, puede forzarlos a cerrar con el comando :

   ```
   killall -9 nlserver
   ```

## Haga una copia de seguridad de la base de datos y la instalación existente {#back-up-the-database-and-the-existing-installation}

El procedimiento depende de la versión anterior de Adobe Campaign.

### Migración desde Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Haga una copia de seguridad de la base de datos de Adobe Campaign.
1. Iniciar sesión como **neolano** y haga una copia de seguridad de **nl5** utilizando el siguiente comando:

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >Como precaución, le recomendamos que comprima el **nl5.back** y guárdelo en una ubicación segura distinta del servidor.

1. Edite el **config-`<instance name>`.xml** (en el **nl5.back** ), para evitar que **mta**, **wfserver**, **stat** etc. de inicio automático. Por ejemplo, reemplace **autoStart** con **_autoStart** (se mantiene como **neolano**).

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

1. Haga una copia de seguridad de la base de datos de Adobe Campaign.
1. Iniciar sesión como **neolano** y haga una copia de seguridad de **nl6** utilizando el siguiente comando:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Como precaución, le recomendamos que comprima el **nl6.back** y guárdelo en una ubicación segura distinta del servidor.

1. Edite el **config-`<instance name>`.xml** (en el **nl6.back** ) para evitar que **mta**, **wfserver**, **stat**, etc. de inicio automático. Por ejemplo, reemplace **autoStart** con **_autoStart** (se mantiene como **Adobe Campaign**).

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

1. Haga una copia de seguridad de la base de datos de Adobe Campaign.
1. Iniciar sesión como **neolano** y haga una copia de seguridad de **nl6** utilizando el siguiente comando:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Como precaución, le recomendamos que comprima el **nl6.back** y guárdelo en una ubicación segura distinta del servidor.

## Desinstalación de paquetes de versiones anteriores de Adobe Campaign {#uninstalling-adobe-campaign-previous-version-packages}

El procedimiento depende de la versión anterior de Adobe Campaign.

### Desinstalación de paquetes Adobe Campaign v5 {#uninstalling-adobe-campaign-v5-packages}

1. Iniciar sesión como **root**.
1. Identifique los paquetes de Adobe Campaign instalados mediante el siguiente comando.

   * En **Debian**:

      ```
      dpkg -l | grep nl
      ```

      Se muestra la lista de paquetes instalados:

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

### Desinstalación de paquetes Adobe Campaign v6 {#uninstalling-adobe-campaign-v6-packages}

Esta sección muestra cómo desinstalar paquetes Adobe Campaign v6.02 o v6.1.

1. Iniciar sesión como **root**.
1. Identifique los paquetes de Adobe Campaign instalados mediante el siguiente comando.

   * En **Debian**:

      ```
      dpkg -l | grep nl
      ```

      Se muestra la lista de paquetes instalados:

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

La implementación de Adobe Campaign consta de dos etapas:

* Instalación de paquetes de Adobe Campaign v7: esta operación debe realizarse en cada servidor.
* La actualización posterior: este comando debe iniciarse en cada instancia.

Para implementar Adobe Campaign, siga los siguientes pasos:

1. Instale los paquetes de Adobe Campaign v7 más recientes mediante el siguiente comando:

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
   >Al migrar desde la versión 5.11, Adobe Campaign se instala en la variable **/usr/local/neolane/nl6/** de forma predeterminada.
   >
   >Una vez instalados los paquetes, se muestra el siguiente mensaje: **Falta la opción &#39;WdbcTimeZone&#39;**. Esto es normal.

1. Para que el programa de instalación de la consola del cliente esté disponible, cópielo en el directorio de instalación de Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Para obtener más información sobre cómo instalar Adobe Campaign en Linux, consulte [esta sección](../../installation/using/installing-campaign-standard-packages.md).

1. Modifique el **.bashrd** que coincida con la variable **neolano** usuario. Iniciar sesión como **neolano** y ejecute el siguiente comando:

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >Cuando inicie sesión como **neolano**, se muestra el siguiente mensaje: **nl5/env.sh : No existe dicho archivo o directorio**. Esto es normal.

   Al final del archivo, reemplace **nl5/env.sh** con **nl6/env.sh**.

1. Iniciar sesión como **root** y prepare la instancia utilizando los siguientes comandos:

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
   >Estos comandos permiten crear el sistema de archivos internos de Adobe Campaign v6: **conf** (con el **config-default.xml** y **serverConf.xml** archivos), **var** directorio.

1. Vaya a la **nl5.back** carpeta de copia de seguridad y copie (sobrescriba) los archivos de configuración y las subcarpetas de cada instancia. Iniciar sesión como **neolano** y ejecute el siguiente comando:

   >[!IMPORTANT]
   >
   >Para el primer comando siguiente, no copie el **config-default.xml** archivo.

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. En Adobe Campaign v7 **serverConf.xml** y **config-default.xml** , aplique las configuraciones específicas que tenía para Adobe Campaign v5. Para la variable **serverConf.xml** utilice el **nl5/conf/serverConf.xml.diff** archivo.

   >[!NOTE]
   >
   >Cuando genere informes de configuraciones desde Adobe Campaign v5 a Adobe Campaign v7, asegúrese de que las rutas a los directorios físicos llevan a Adobe Campaign v7 y no a Adobe Campaign v5.

1. Como la migración no es una instalación genérica, debe forzar el reinicio de la variable **trackinglogd** servicio. Para ello, abra el **nl6/conf/config-default.xml** y asegúrese de que **trackinglogd** está activado (solo en los servidores de seguimiento/redirección):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Si la variable **trackinglogd** no se ha iniciado el servicio en el servidor de seguimiento, no se reenviará ninguna información de seguimiento.

1. Vuelva a cargar la configuración de Adobe Campaign v7 con el siguiente comando:

   ```
   nlserver config -reload
   ```

1. Inicie el proceso posterior a la actualización mediante el siguiente comando (siga siendo **neolano**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >Debe especificar qué zona horaria utilizar como referencia durante la posactualización (mediante el uso de **-timezone** ). En este caso, estamos utilizando la zona horaria Europa/París **-timezone: &quot;Europa/París&quot;**.

   >[!NOTE]
   >
   >Le recomendamos encarecidamente que actualice su base a &quot;multi-huso horario&quot;. Para obtener más información sobre las opciones de zona horaria, consulte [Zonas horarias](../../migration/using/general-configurations.md#time-zones) para obtener más información.

>[!IMPORTANT]
>
>No inicie los servicios de Adobe Campaign aún: aún es necesario realizar cambios en Apache.

### Migración desde Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

La implementación de Adobe Campaign consta de dos etapas:

* Instalación de paquetes de Adobe Campaign v7: esta operación debe realizarse en cada servidor.
* La actualización posterior: este comando debe iniciarse en cada instancia.

Para implementar Adobe Campaign, siga los siguientes pasos:

1. Instale los paquetes de Adobe Campaign v7 más recientes mediante el siguiente comando:

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
   >Adobe Campaign v7 se instala en el mismo directorio de forma predeterminada que Adobe Campaign v6.02: **/usr/local/neolane/nl6/**.

1. Para que el programa de instalación de la consola del cliente esté disponible, cópielo en el directorio de instalación de Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Para obtener más información sobre cómo instalar Adobe Campaign en Linux, consulte [esta sección](../../installation/using/installing-campaign-standard-packages.md).

1. Como la migración no es una instalación genérica, debe forzar el reinicio de la variable **trackinglogd** servicio. Para ello, abra el **nl6/conf/config-default.xml** y asegúrese de que **trackinglogd** está activado (solo en los servidores de seguimiento/redirección):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Si la variable **trackinglogd** no se ha iniciado el servicio en el servidor de seguimiento, no se reenviará ninguna información de seguimiento.

1. Vaya a la **nl6.back** carpeta de copia de seguridad y copie (sobrescriba) los archivos de configuración y las subcarpetas de cada instancia. Iniciar sesión como **neolano** y ejecute el siguiente comando:

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

1. Inicie el proceso posterior a la actualización mediante el siguiente comando (siga siendo **neolano**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >El modo &quot;multi timezone&quot; solo estaba disponible en la versión 6.02 para los motores de base de datos PostgreSQL. Ahora está disponible independientemente de la versión del motor de base de datos que se esté utilizando. Le recomendamos encarecidamente que actualice su base a &quot;multi-huso horario&quot;. Para obtener más información sobre las opciones de zona horaria, consulte [Zonas horarias](../../migration/using/general-configurations.md#time-zones) para obtener más información.

### Migración desde Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-1}

La implementación de Adobe Campaign consta de dos etapas:

* Instalación de paquetes de Adobe Campaign v7: esta operación debe realizarse en cada servidor.
* La actualización posterior: este comando debe iniciarse en cada instancia.

Para implementar Adobe Campaign, siga los siguientes pasos:

1. Instale los paquetes de Adobe Campaign v7 más recientes mediante el siguiente comando:

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
   >Adobe Campaign v7 está instalado en el **/usr/local/neolane/nl6/** de forma predeterminada.

1. Para que el programa de instalación de la consola del cliente esté disponible, cópielo en el directorio de instalación de Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Para obtener más información sobre cómo instalar Adobe Campaign en Linux, consulte [esta sección](../../installation/using/installing-campaign-standard-packages.md).

1. Vaya a la **nl6.back** carpeta de copia de seguridad y copie (sobrescriba) los archivos de configuración y las subcarpetas de cada instancia. Iniciar sesión como **neolano** y ejecute el siguiente comando:

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

1. Inicie el proceso posterior a la actualización mediante el siguiente comando (siga siendo **neolano**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## Migración del servidor de redirección (Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>Esta sección solo se aplica al migrar desde Adobe Campaign v5.11.

En este momento, Apache debe detenerse. Consulte: [Interrupción del servicio](#service-stop).

1. Iniciar sesión como **root**.
1. Cambie las variables de entorno de Apache para que estén vinculadas a la variable **nl6** directorio.

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

      En el **nlsrv.load** archivo, reemplazar **nl5** con **nl6**.

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      Elimine el vínculo del **nlsrv.conf** y cree uno nuevo.

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * En **Red Hat**:

      Vaya a la **/usr/local/apache2/conf** , edite el **http.conf** archivo y reemplazar **nl5** con **nl6** en las líneas siguientes.

      En **RHEL 7/Debian 8**:

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Vaya a la **alias.conf** y reemplazar todo **nl5** con **nl6**. Para hacerlo en Debian, ejecute el siguiente comando:

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## Zonas de seguridad {#security-zones}

Si va a migrar desde la versión 6.02 o anterior, debe configurar las zonas de seguridad antes de iniciar los servicios. Para obtener más información, consulte [Seguridad](../../migration/using/general-configurations.md#security).

## Reinicio de servicios {#re-starting-services}

El procedimiento depende de la versión anterior de Adobe Campaign.

### Migración desde Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-2}

En el **config-`<instance name>`.xml** , reactive el inicio automático del **mta**, **wfserver**, **stat**, etc. servicios.

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

Inicie los servicios de Apache y Adobe Campaign en cada uno de los siguientes servidores:

1. Servidor de seguimiento y redirección.
1. Servidor intermediario.
1. Servidor de marketing.

Antes de continuar con el siguiente paso, ejecute una prueba completa de la nueva instalación, asegúrese de que no haya regresiones y de que todo funcione siguiendo todas las recomendaciones de la [Configuraciones generales](../../migration/using/general-configurations.md) para obtener más información.

### Migración desde Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

En el **config-`<instance name>`.xml** , reactive el inicio automático del **mta**, **wfserver**, **stat**, etc. servicios.

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

Inicie los servicios de Apache y Adobe Campaign en cada uno de los siguientes servidores:

1. Servidor de seguimiento y redirección.
1. Servidor intermediario.
1. Servidor de marketing.

Pruebe completamente la nueva instalación, compruebe que no se reinicia y asegúrese de que todo funciona correctamente siguiendo todas las recomendaciones de la [Configuraciones generales](../../migration/using/general-configurations.md) para obtener más información.

### Migración desde Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-2}

Inicie los servicios de Apache y Adobe Campaign en cada uno de los siguientes servidores:

1. Servidor de seguimiento y redirección.
1. Servidor intermediario.
1. Servidor de marketing.

Pruebe completamente la nueva instalación, compruebe que no se reinicia y asegúrese de que todo funciona correctamente siguiendo todas las recomendaciones de la [Configuraciones generales](../../migration/using/general-configurations.md) para obtener más información.

## Eliminación y limpieza de Adobe Campaign v5 {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>Esta sección solo se aplica al migrar desde Adobe Campaign v5.11.

Antes de eliminar y limpiar la instalación de Adobe Campaign v5, debe aplicar las siguientes recomendaciones:

* Haga que los equipos funcionales ejecuten una comprobación completa de la nueva instalación.
* Solo desinstale Adobe Campaign v5 cuando esté seguro de que no es necesario realizar ninguna reversión.

Elimine el **nl5.back** directorio. Iniciar sesión como **neolano** y ejecute el siguiente comando:

```
su - neolane
rm -rf nl5.back
```

Vuelva a iniciar el servidor.
