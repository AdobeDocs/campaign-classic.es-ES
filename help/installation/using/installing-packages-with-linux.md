---
product: campaign
title: Instalación de paquetes con Linux
description: Instalación de paquetes con Linux
feature: Installation, Application Settings
badge-v7-prem: label="On-Premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1199'
ht-degree: 1%

---

# Instalación de paquetes con Linux{#installing-packages-with-linux}



Para una plataforma Linux de 32 bits, instale Adobe Campaign de 32 bits. Para una plataforma Linux de 64 bits, instale Adobe Campaign de 64 bits.

Para cada una de estas versiones, Adobe Campaign viene con un paquete: **nlserver**. Este paquete contiene los binarios y los archivos de configuración de una versión determinada.

Los comandos de instalación permiten:

* Copie los archivos en **/usr/local/neolane**
* Cree una cuenta de Adobe Campaign Linux (y el grupo asociado) con **/usr/local/neolane** como directorio principal
* Creación de una secuencia de comandos automática **/etc/init.d/nlserver6** para usarlo al inicio, o crear una unidad sistémica (a partir de 20.1).

>[!NOTE]
>
>El **neolano** no se debe haber creado el usuario del sistema antes de ejecutar el comando. El **neolano** el usuario se crea automáticamente durante la instalación.
>
>El **home** directorio vinculado al **neolano** El usuario de también se crea automáticamente en **[!UICONTROL /usr/local/neolane]**. Asegúrese de que haya espacio suficiente en la **[!UICONTROL /usr/local]** disco (varios GB).

Puede ejecutar el **ping`hostname`** para asegurarse de que el servidor puede conectarse a sí mismo.

## Distribución basada en paquetes RPM {#distribution-based-on-rpm--packages}

Para instalar Adobe Campaign en un sistema operativo RPM (RHEL, CentOS y SUSE), siga los siguientes pasos:

1. Primero debe obtener el paquete de Adobe Campaign.

   El nombre del archivo es el siguiente, donde **XXXX** es el número de compilación de Adobe Campaign: **nlserver6-v7-XXXX-0.x86_64.rpm**.

   >[!CAUTION]
   >
   >Asegúrese de utilizar el nombre de archivo correcto para su versión de Adobe Campaign en los ejemplos de comandos de esta sección.

1. Para instalarlo, conéctese como **raíz** y ejecute el siguiente comando (donde **XXXX** es el número de compilación de Adobe Campaign):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   El archivo rpm depende de paquetes que se pueden encontrar en las distribuciones de CentOS/Red Hat. Si no desea utilizar algunas de estas dependencias (por ejemplo, si desea utilizar el JDK de Oracle en lugar de OpenJDK), es posible que tenga que utilizar la opción &quot;nodeps&quot; de rpm:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

El comando &#39;bc&#39; necesario para ejecutar netreport (consulte [esta sección](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) para obtener más información), no está disponible de forma predeterminada en todas las distribuciones de Linux. Para comprobar si el comando está disponible, ejecute el comando &#39;which bc&#39;. Si no es así, tiene que instalarlo.

Con CentOS, debe instalar el paquete bc.x86_64: conecte como **raíz** y ejecute el siguiente comando:

```
yum install bc.x86_64
```

## Distribución basada en APT (Debian) {#distribution-based-on-apt--debian-}

### En Debian de 64 bits {#in-debian-64-bits}

Para instalar Adobe Campaign de 64 bits en un sistema operativo Debian de 64 bits, siga los siguientes pasos:

1. Primero debe obtener el paquete de Adobe Campaign: **nlserver6-v7-XXXX-linux-2.6-amd64.deb**, donde **XXXX** es el número de compilación.

   >[!CAUTION]
   >
   >Asegúrese de utilizar el nombre de archivo correcto para su versión de Adobe Campaign en los ejemplos de comandos de esta sección.

1. Para instalarlo, conéctese como **raíz** y ejecute el siguiente comando (donde **XXXX** es el número de compilación de Adobe Campaign):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   Si faltan dependencias, ejecute el siguiente comando:

   ```
   apt-get install -f
   ```

**Detalles de Debian 8/9**

Al instalar Adobe Campaign en un sistema operativo Debian 8/9, tenga en cuenta lo siguiente:

* OpenSSL debe instalarse de antemano.
* Instale libicu52 (Debian 8) o libicu57 (Debian 9), libprotobuf9 (Debian8) y libc-ares2 con los siguientes comandos:

  ```
  aptitude install libicu52 (Debian 8) libicu57 (Debian 9)
  ```

  ```
  aptitude install libc-ares2
  ```

  ```
  aptitude install libprotobuf9 (only Debian 8)
  ```

* Instale JDK7 con el siguiente comando:

  ```
  aptitude install openjdk-7-jdk (Debian 8)
  ```

  ```
  aptitude install openjdk-7-jdk (Debian 9)
  ```

## Personalización de parámetros {#personalizing-parameters}

Algunos parámetros se pueden personalizar mediante la variable **customer.sh** archivo

Si realiza la instalación por primera vez, la variable **customer.sh** es posible que el archivo aún no exista en el servidor. Créela y asegúrese de que tiene derechos de ejecución. Si no es así, introduzca el siguiente comando:

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Codificación del servidor {#server-encoding}

De forma predeterminada, el servidor se inicia en un entorno iso8859-15. Sin embargo, el servidor se puede iniciar en un entorno UTF-8.

>[!CAUTION]
>
>Este cambio afecta a las interacciones con el sistema de archivos (archivos cargados mediante un flujo de trabajo o una secuencia de comandos JavaScript) y a la codificación de archivos. Por lo tanto, se recomienda utilizar el entorno predeterminado.

Sin embargo, para crear un **Instancia de japonés**, debe utilizar un entorno UTF-8.

Para habilitar el entorno UTF-8, utilice el siguiente comando:

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### Idioma predeterminado del servidor {#default-language-for-the-server}

La instalación admite inglés y francés. El inglés se utiliza de forma predeterminada.

Para cambiar al francés, introduzca los siguientes comandos:

```
su - neolane
vi nl6/customer.sh
```

y añada la línea siguiente:

```
export neolane_LANG=fra
```

Para garantizar que los mensajes del sistema se lean correctamente, las consolas deben estar en una página de códigos correspondiente al idioma (ISO-8859-1 o -15 para francés).

### Variables de entorno {#environment-variables}

Las siguientes variables de entorno deben definirse correctamente.

Algunas combinaciones requieren cambios en el entorno utilizado para ejecutar Adobe Campaign. Un archivo específico (`/usr/local/neolane/nl6/customer.sh`) se puede crear y editar para añadir modificaciones específicas al entorno de Adobe Campaign.

Si es necesario, edite el **customer.sh** usando el archivo **vi customer.sh** y adaptar la configuración o añadir las líneas que faltan:

* Para el cliente de Oracle:

  ```
  export ORACLE_HOME=/usr/local/instantclient_10_2
  export TNS_ADMIN=/etc/oracle
  export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
  ```

  El contenido de la variable de entorno ORACLE_HOME coincide con el directorio de instalación de Oracle.

  El contenido de la variable TNS_ADMIN debe coincidir con la ubicación de la variable **tnsnames.ora** archivo.

* Para LibreOffice:

  Para ejecutar Adobe Campaign en una versión existente de LibreOffice, se requieren configuraciones adicionales: debe especificar las rutas de acceso al directorio de instalación. Por ejemplo:

   * Debian

     Se proporcionan los valores predeterminados para OOO_INSTALL_DIR y OOO_BASIS_INSTALL_DIR. Puede anularlos en **customer.sh** si el diseño de la instalación de LibreOffice es diferente:

     ```
     export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
     export OOO_INSTALL_DIR=/usr/lib/libreoffice/
     ```

   * CentOs

     Utilice los siguientes valores predeterminados:

     ```
     export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
     export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
     ```

* Para el kit de desarrollo de Java (JDK):

  De forma predeterminada, la secuencia de comandos de configuración del entorno de Adobe Campaign (`~/nl6/env.sh`) busca el directorio de instalación de JDK. Dado que este comportamiento no es 100 % fiable, debe especificar qué JDK debe utilizarse. Para ello, puede forzar al **JDK_HOME** variable de entorno mediante el siguiente comando:

  ```
  export JDK_HOME=/usr/java/jdk1.6.0_07
  ```

  >[!NOTE]
  >
  >Este es un ejemplo. Asegúrese de que la versión del JDK utilizada coincida con el nombre del directorio.

  Para probar la configuración de JDK, inicie sesión como el usuario del sistema de Adobe Campaign con el siguiente comando:

  ```
  su - neolane
  ```

Debe reiniciar el servicio Adobe Campaign para que se tengan en cuenta los cambios.

Los comandos son los siguientes:

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

A partir de la versión 20.1, se recomienda utilizar los siguientes comandos:

```
systemctl stop nlserver
systemctl start nlserver
```

### Cliente de oracle en Linux {#oracle-client-in-linux}

Cuando se utiliza el Oracle con Adobe Campaign, es necesario configurar las capas de cliente de Oracle en Linux.

* Usar el cliente completo
* Definición de TNS

  Las definiciones de TNS deben añadirse durante la fase de instalación. Para ello, utilice los siguientes comandos:

  ```
  cd /etc
  mkdir oracle
  cd oracle
  vi tnsnames.ora
  ```

* Variables de entorno

  Consulte [Variables de entorno](../../installation/using/installing-packages-with-linux.md#environment-variables).

* Configuración de Adobe Campaign

  Para finalizar la instalación del cliente de Oracle para Adobe Campaign, debe crear un vínculo simbólico para **.so** archivo utilizado por Adobe Campaign.

  Para ello, utilice los siguientes comandos:

  ```
  cd /usr/lib/oracle/10.2.0.4/client/lib
  ln -s libclntsh.so.10.1 libclntsh.so
  ```

Si tiene algún problema, asegúrese de que los paquetes que aparecen en la [documentación de instalación de oracle](https://docs.oracle.com/) están correctamente instalados.

## Comprobaciones de instalación {#installation-checks}

Ahora puede realizar una prueba de instalación inicial con los siguientes comandos:

```
su - neolane
nlserver pdump
```

Cuando Adobe Campaign no se inicia, la respuesta es:

```
no task
```

## Primer inicio del servidor {#first-start-up-of-the-server}

Una vez finalizada la prueba de instalación, introduzca el siguiente comando:

```
nlserver web
```

A continuación, se muestra la siguiente información:

```
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

Estos comandos permiten crear **config-default.xml** y **serverConf.xml** archivos de configuración. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

Prensa **Ctrl + C** para detener el proceso, introduzca el siguiente comando:

```
nlserver start web
```

A continuación, se muestra la siguiente información:

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Running task 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') in a new process
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Para detenerlo, escriba:

```
nlserver stop web
```

A continuación, se muestra la siguiente información:

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Contraseña para el identificador interno {#password-for-the-internal-identifier}

El servidor de Adobe Campaign define un inicio de sesión técnico llamado **interno** que tiene todos los derechos en todas las instancias. Justo después de la instalación, el inicio de sesión no tiene contraseña. Es obligatorio definir uno.

Obtenga más información en [esta sección](../../installation/using/configuring-campaign-server.md#internal-identifier).
