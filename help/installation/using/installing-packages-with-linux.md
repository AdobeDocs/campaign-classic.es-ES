---
product: campaign
title: Instalación de paquetes con Linux
description: Instalación de paquetes con Linux
feature: Installation, Application Settings
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
source-git-commit: 934185053bea08ea1fa6f52dec1d86a5ced02c11
workflow-type: tm+mt
source-wordcount: '1110'
ht-degree: 2%

---

# Instalación de paquetes con Linux {#installing-packages-with-linux}

Adobe Campaign viene con el paquete **nlserver** que contiene los binarios y los archivos de configuración de una versión determinada.

Los comandos de instalación permiten:

* Copie los archivos en **/usr/local/neolane**
* Cree una cuenta de Adobe Campaign Linux (y el grupo asociado), que se crea con **/usr/local/neolane** como directorio principal
* Crear un script automático **/etc/init.d/nlserver6** para usarlo al inicio o crear una unidad sistémica

>[!NOTE]
>
>No se debe crear el usuario del sistema **neolane** antes de ejecutar el comando. El usuario **neolane** se crea automáticamente durante la instalación.
>
>El directorio **home** vinculado al usuario **neolane** también se crea automáticamente en **[!UICONTROL /usr/local/neolane]**. Asegúrese de que haya espacio suficiente en el disco **[!UICONTROL /usr/local]**.

Puede ejecutar el comando **ping`hostname`** para asegurarse de que el servidor se puede conectar a sí mismo.

## Distribución basada en paquetes RPM {#distribution-based-on-rpm--packages}

>[!AVAILABILITY]
>
>A partir de la versión 7.4.1, las bibliotecas XML para paquetes RPM de Linux ya no se incluyen en Campaign. Debe instalar estas bibliotecas.
> 

Para instalar Adobe Campaign en un sistema operativo RPM (RHEL, CentOS), siga estos pasos:

1. Obtenga el paquete de Adobe Campaign. El nombre del archivo es **nlserver6-v7-XXXX-0.x86_64.rpm**, donde **XXXX** es el número de compilación de Adobe Campaign.

   >[!CAUTION]
   >
   >Asegúrese de utilizar el nombre de archivo correcto para su versión de Adobe Campaign en los ejemplos de comandos de esta sección.

1. Para instalarlo, conéctese como **root** y ejecute el siguiente comando, donde **XXXX** es el número de compilación de Adobe Campaign:

   ```sql
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   El archivo rpm depende de paquetes que se pueden encontrar en las distribuciones de CentOS/Red Hat. Si no desea utilizar algunas de estas dependencias (por ejemplo, si desea utilizar el JDK de Oracle en lugar de OpenJDK), es posible que tenga que utilizar la opción &quot;nodeps&quot; de rpm:

   ```sql
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

Tenga en cuenta que la mayoría de las dependencias enumeradas son obligatorias y `nlserver` no se puede iniciar si no están instaladas (la excepción es opendk; se puede instalar otro JDK).

El comando `bc`, obligatorio para ejecutar [netreport](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts), no está disponible de forma predeterminada en todas las distribuciones de Linux. Para comprobar si el comando está disponible, ejecute el comando `which bc`. Si no es así, tiene que instalarlo.

Con CentOS, debe instalar el paquete bc.x86_64: conéctese como **root** y ejecute el siguiente comando:

```sql
yum install bc.x86_64
```


### RHEL 9 para implementaciones locales {#rhel-9-update}

Con Campaign v7.4.1, como cliente On-Premise que utiliza RHEL 9, si desea utilizar claves de DKIM/dominio, debe actualizar la configuración del sistema.

Para ello, siga estos pasos:

1. Ejecute el siguiente comando como raíz:

```sql
update-crypto-policies --set LEGACY
```

1. Reinicie el módulo MTA:

```sql
nlserver restart mta@<instance-name>
```

## Distribución basada en APT (Debian) {#distribution-based-on-apt--debian-}

Para instalar Adobe Campaign en un sistema operativo Debian de 64 bits, siga los siguientes pasos:

1. Obtenga el paquete de Adobe Campaign. El nombre del archivo es **nlserver6-v7-XXXX-linux-2.6-amd64.deb**, donde **XXXX** es el número de compilación de Adobe Campaign.

   >[!CAUTION]
   >
   >Asegúrese de utilizar el nombre de archivo correcto para su versión de Adobe Campaign en los ejemplos de comandos de esta sección.

1. Para instalarlo, conéctese como **root** y ejecute el siguiente comando, donde **XXXX** es el número de compilación de Adobe Campaign:

   ```sql
   apt install ./nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```


## Personalización de parámetros {#personalizing-parameters}

Algunos parámetros se pueden personalizar mediante el archivo **customer.sh**

Si realiza la instalación por primera vez, es posible que el archivo **customer.sh** aún no exista en el servidor.

Créela y asegúrese de que tiene derechos de ejecución. Si no es así, introduzca el siguiente comando:

```sql
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Codificación del servidor {#server-encoding}

De forma predeterminada, el servidor se inicia en un entorno iso8859-15. Sin embargo, el servidor se puede iniciar en un entorno UTF-8.

>[!CAUTION]
>
>Este cambio afecta a las interacciones con el sistema de archivos (archivos cargados mediante un flujo de trabajo o una secuencia de comandos de JavaScript) y a la codificación de los archivos. Por lo tanto, se recomienda utilizar el entorno predeterminado.

Para crear una **instancia japonesa**, debe usar un entorno UTF-8.

Para habilitar el entorno UTF-8, utilice el siguiente comando:

```sql
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### Variables de entorno {#environment-variables}

Las siguientes variables de entorno deben definirse correctamente.

Algunas combinaciones requieren cambios en el entorno utilizado para ejecutar Adobe Campaign. Se puede crear y editar un archivo específico (`/usr/local/neolane/nl6/customer.sh`) para agregar modificaciones específicas al entorno de Adobe Campaign.

Si es necesario, edite el archivo **customer.sh** con el comando **vi customer.sh** y adapte la configuración o agregue las líneas que faltan:

* Para el cliente de Oracle:

  ```sql
  export ORACLE_HOME=/usr/local/instantclient_10_2
  export TNS_ADMIN=/etc/oracle
  export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
  ```

  El contenido de la variable de entorno ORACLE_HOME coincide con el directorio de instalación de Oracle.

  El contenido de la variable TNS_ADMIN debe coincidir con la ubicación del archivo **tnsnames.ora**.

* Para LibreOffice:

  Para ejecutar Adobe Campaign en una versión existente de LibreOffice, se requieren configuraciones adicionales: debe especificar las rutas de acceso al directorio de instalación. Por ejemplo:

   * Debian

     Se proporcionan los valores predeterminados para OOO_INSTALL_DIR y OOO_BASIS_INSTALL_DIR. Puede anularlos en **customer.sh** si el diseño de la instalación de LibreOffice es diferente:

     ```sql
     export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
     export OOO_INSTALL_DIR=/usr/lib/libreoffice/
     ```

   * CentOs

     Utilice los siguientes valores predeterminados:

     ```sql
     export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
     export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
     ```

* Para el kit de desarrollo de Java (JDK):

  De forma predeterminada, el script de configuración del entorno de Adobe Campaign (`~/nl6/env.sh`) busca el directorio de instalación de JDK. Sin embargo, se recomienda especificar qué JDK se debe utilizar. Para ello, puede forzar la variable de entorno **JDK_HOME** mediante el siguiente comando:

  ```sql
  export JDK_HOME=/usr/java/jdkX.Y.Z
  ```

  >[!NOTE]
  >
  >Asegúrese de que la versión del JDK utilizada coincida con el nombre del directorio.

  Para probar la configuración de JDK, inicie sesión como el usuario del sistema de Adobe Campaign con el siguiente comando:

  ```sql
  su - neolane
  ```

Debe reiniciar el servicio Adobe Campaign para que se tengan en cuenta los cambios.

Los comandos son los siguientes:

```sql
systemctl stop nlserver
systemctl start nlserver
```

### Cliente de oracle en Linux {#oracle-client-in-linux}

Cuando se utiliza el Oracle con Adobe Campaign, es necesario configurar las capas de cliente de Oracle en Linux.

* Usar el cliente completo
* Definición de TNS

  Las definiciones de TNS deben añadirse durante la fase de instalación. Para ello, utilice los siguientes comandos:

  ```sql
  cd /etc
  mkdir oracle
  cd oracle
  vi tnsnames.ora
  ```

* Variables de entorno

  Consulte [Variables de entorno](#environment-variables).

* Configuración de Adobe Campaign

  Para finalizar la instalación del cliente de Oracle para Adobe Campaign, debe crear un vínculo simbólico para el archivo **.so** utilizado por Adobe Campaign.

  Para ello, utilice los siguientes comandos:

  ```sql
  cd /usr/lib/oracle/10.2.0.4/client/lib
  ln -s libclntsh.so.10.1 libclntsh.so
  ```

En caso de problemas, asegúrese de que los paquetes enumerados en la documentación de instalación de Oracle estén instalados correctamente.

## Comprobaciones de instalación {#installation-checks}

Ahora puede realizar una prueba de instalación inicial con los siguientes comandos:

```sql
su - neolane
nlserver pdump
```

Cuando Adobe Campaign no se inicia, la respuesta es:

```sql
no task
```

## Primer inicio del servidor {#first-start-up-of-the-server}

Una vez finalizada la prueba de instalación, introduzca el siguiente comando:

```sql
nlserver web
```

A continuación, se muestra la siguiente información:

```sql
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

Estos comandos le permiten crear **config-default.xml** y **serverConf.xml** archivos de configuración. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

Presione **Ctrl+C** para detener el proceso y luego ingrese el siguiente comando:

```sql
nlserver start web
```

A continuación, se muestra la siguiente información:

```sql
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Running task 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') in a new process
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Para detenerlo, escriba:

```sql
nlserver stop web
```

A continuación, se muestra la siguiente información:

```sql
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Contraseña para el identificador interno {#password-for-the-internal-identifier}

El servidor de Adobe Campaign define un inicio de sesión técnico denominado **internal** con todos los derechos en todas las instancias. Justo después de la instalación, el inicio de sesión no tiene contraseña. Es obligatorio definir uno.

Obtenga más información en [esta sección](../../installation/using/configuring-campaign-server.md#internal-identifier).
