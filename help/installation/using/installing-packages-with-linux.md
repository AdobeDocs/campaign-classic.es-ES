---
title: Instalación de paquetes con Linux
seo-title: Instalación de paquetes con Linux
description: Instalación de paquetes con Linux
seo-description: null
page-status-flag: never-activated
uuid: d83f00b5-500b-406a-a3d6-ea5639f244f0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 04faa9f3-d160-4060-b26e-44333f2faf71
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8ad1a83d40f5a841b01aaeb17fe271b44f2480dd

---


# Instalación de paquetes con Linux{#installing-packages-with-linux}

Para una plataforma Linux de 32 bits, instale Adobe Campaign de 32 bits. Para una plataforma Linux de 64 bits, instale Adobe Campaign de 64 bits.

Para cada una de estas versiones, Adobe Campaign incluye un paquete: **nlserver**. Este paquete contiene los archivos binarios y de configuración de una versión determinada.

Los comandos de instalación le permiten:

* Copiar los archivos en **/usr/local/neolane**
* Crear una cuenta de Adobe Campaign Linux (y el grupo asociado), que se crea con **/usr/local/neolane** como directorio principal
* Creación de una secuencia de comandos automática **/etc/init.d/nlserver6** para su uso durante el inicio

Este paquete se compila con GCC 4, lo que implica dependencias con versiones específicas de las bibliotecas que no siempre están disponibles en la plataforma de instalación.

>[!NOTE]
>
>El usuario del sistema **neolane** no debe haber sido creado antes de ejecutar el comando. El usuario **neolano** se crea automáticamente durante la instalación.
>
>El directorio **principal** vinculado al usuario **neolano** también se crea automáticamente en **[!UICONTROL /usr/local/neolane]**. Asegúrese de que hay suficiente espacio en el **[!UICONTROL /usr/local]** disco (varios GB).

Puede ejecutar el comando **ping`hostname`**para asegurarse de que el servidor se pueda conectar a sí mismo.

## Distribución basada en paquetes RPM {#distribution-based-on-rpm--packages}

Para instalar Adobe Campaign en un sistema operativo RPM (RHEL, CentOS y SUSE), siga estos pasos:

1. Primero debe obtener el paquete de Adobe Campaign.

   El nombre del archivo es el siguiente, donde **XXXX** es el número de compilación de Adobe Campaign:

   * **nlserver6-v7-XXXX-0.x86_64.rpm** para v7.
   * **nlserver6-XXXX-0.x86_64.rpm** para v6.1.
   >[!CAUTION]
   >
   >Asegúrese de utilizar el nombre de archivo correcto para su versión de Adobe Campaign en los ejemplos de comandos de esta sección.

1. Para instalarlo, conéctese como **raíz** y ejecute el siguiente comando (donde **XXXX** es el número de compilación de Adobe Campaign):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   El archivo rpm tiene dependencias en paquetes que puede encontrar en distribuciones de CentOS/Red Hat. Si no desea utilizar algunas de estas dependencias (por ejemplo, si desea utilizar Oracle JDK en lugar de OpenJDK), puede que tenga que utilizar la opción &quot;nodeps&quot; de rpm:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

El comando &#39;bc&#39;, necesario para ejecutar netreport (consulte [esta sección](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) para obtener más información), no está disponible de forma predeterminada en todas las distribuciones de Linux. Para comprobar si el comando está disponible, ejecute el comando &#39;what bc&#39;. Si no es así, tiene que instalarlo.

Con CentOS, debe instalar el paquete bc.x86_64: conecte como **raíz** y ejecute el siguiente comando:

```
yum install bc.x86_64
```

**Ejemplo de una instalación en SLES 11 SP2:**

* Deshabilitar **[!UICONTROL libboost_regex]** :

   ```
   zypper remove libboost_regex1_36_0
   ```

* Instale Oracle Java o OpenJDK (para obtener más información sobre esto, consulte Kit de desarrollo de [Java - JDK](../../installation/using/application-server.md#java-development-kit---jdk)):

   ```
   ./jdk-6uxx-linux-x64-rpm.bin
   ```

* Instale OpenSSL 1.0 (para obtener más información sobre esto, consulte [Bibliotecas](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#libraries)):

   ```
   yast -i libopenssl1_0_0-1.0.0c-18.42.1.x86_64.rpm
   ```

   Debe crear alias que apunten a los archivos de la biblioteca OpenSSL:

   ```
   ln -s /lib64/libssl.so.1.0.0 /lib64/libssl.so.10
   ln -s /lib64/libcrypto.so.1.0.0 /lib64/libcrypto.so.10
   ```

* Instale libicu 4.2 (para obtener más información sobre esto, consulte [Bibliotecas](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#libraries)):

   ```
   yast -i libicu-4.2-7.3.1.x86_64.rpm
   ```

* Instale el paquete del servidor de Adobe Campaign:

   ```
   yast -i nlserver6-v7-xxx-x.x86_64.rpm
   ```

## Distribución basada en APT (Debian) {#distribution-based-on-apt--debian-}

### En Debian 32 bits {#in-debian-32-bits}

Para instalar Adobe Campaign de 32 bits en un sistema operativo Debian de 32 bits, siga los pasos siguientes:

1. Primero debe obtener los dos paquetes de Adobe Campaign.

   * **nlserver6-v7-XXXX-linux-2.6-intel.deb** para v7.
   * **nlserver6-XXXX-linux-2.6-intel.deb** para v6.1.
   **XXXX** es el número de compilación de Adobe Campaign.

   >[!CAUTION]
   >
   >Asegúrese de utilizar el nombre de archivo correcto para su versión de Adobe Campaign en los ejemplos de comandos de esta sección.

1. Para instalarlo, conéctese como **raíz** y ejecute el siguiente comando (donde **XXXX** es el número de compilación de Adobe Campaign):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-intel.deb
   ```

   Si faltan dependencias, ejecute el siguiente comando:

   ```
   apt-get install -f
   ```

### En Debian 64 bits {#in-debian-64-bits}

Para instalar Adobe Campaign de 64 bits en un sistema operativo Debian de 64 bits, siga los pasos siguientes:

1. Primero debe obtener el paquete de Adobe Campaign.

   * **nlserver6-v7-XXXX-linux-2.6-amd64.deb** para v7.
   * **nlserver6-XXXX-linux-2.6-amd64.deb** para v6.1.
   **XXXX** es el número de compilación de Adobe Campaign.

   >[!CAUTION]
   >
   >Asegúrese de utilizar el nombre de archivo correcto para su versión de Adobe Campaign en los ejemplos de comandos de esta sección.

1. Para instalarlo, conéctese como **raíz** y ejecute el siguiente comando (donde **XXXX** es el número de compilación de Adobe Campaign):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

**Especificaciones específicas de Debian 7/8**

Al instalar Adobe Campaign en un sistema operativo Debian 7, tenga en cuenta lo siguiente:

* OpenSSL debe estar instalado de antemano.
* Instale libicu48 (Debian 7), libicu52 (Debian 8) o libicu57 (Debian 9), libprotobuf9 (Debian8) y libc-ares2 con los siguientes comandos:

   ```
   aptitude install libicu48 (Debian 7) libicu52 (Debian 8) libicu57 (Debian 9)
   ```

   ```
   aptitude install libc-ares2
   ```

   ```
   aptitude install libprotobuf9 (only Debian 7/8)
   ```

* Instale JDK7 con el siguiente comando:

   ```
   aptitude install openjdk-7-jdk (Debian 7/8)
   ```

   ```
   aptitude install openjdk-7-jdk (Debian 9)
   ```

## Personalización de parámetros {#personalizing-parameters}

Algunos parámetros se pueden personalizar mediante el archivo **customer.sh** .

Si está realizando la instalación por primera vez, es posible que el archivo **customer.sh** aún no exista en el servidor. Crearla y asegurarse de que tiene derechos de ejecución. Si no es así, introduzca el siguiente comando:

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Codificación del servidor {#server-encoding}

De forma predeterminada, el servidor se inicia en un entorno iso8859-15. Sin embargo, el servidor puede iniciarse en un entorno UTF-8.

>[!CAUTION]
>
>Este cambio afecta a las interacciones con el sistema de archivos (archivos cargados mediante un flujo de trabajo o una secuencia de comandos de JavaScript) y a la codificación de archivos. Por lo tanto, recomendamos utilizar el entorno predeterminado.

Sin embargo, para crear una instancia **** japonesa, debe utilizar un entorno UTF-8.

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

y agregue la línea siguiente:

```
export neolane_LANG=fra
```

Para garantizar que los mensajes del sistema se leen correctamente, las consolas deben estar en una página de código correspondiente al idioma (ISO-8859-1 o -15 para francés).

### Variables de entorno {#environment-variables}

Las siguientes variables de entorno deben definirse correctamente.

Determinadas combinaciones requieren cambios en el entorno utilizado para ejecutar Adobe Campaign. Se puede crear y editar un archivo específico (`/usr/local/neolane/nl6/customer.sh`) para agregar modificaciones específicas al entorno de Adobe Campaign.

Si es necesario, edite el archivo **customer.sh** mediante el comando **vi customer.sh** y adapte la configuración o agregue las líneas que faltan:

* Para el cliente de Oracle:

   ```
   export ORACLE_HOME=/usr/local/instantclient_10_2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
   ```

   El contenido de la variable de entorno ORACLE_HOME coincide con el directorio de instalación de Oracle.

   El contenido de la variable TNS_ADMIN debe coincidir con la ubicación del archivo **tnsnames.ora** .

* Para LibreOffice:

   Para ejecutar Adobe Campaign en una versión existente de LibreOffice, se requieren configuraciones adicionales: debe especificar las rutas de acceso al directorio de instalación. Por ejemplo:

   * Debian

      Se proporcionan los valores predeterminados para OOO_INSTALL_DIR, OOO_BASIS_INSTALL_DIR, OOO_URE_INSTALL_DIR. Puedes ignorarlos en **customer.sh** si tu diseño de la instalación de LibreOffice es diferente:

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
      export OOO_INSTALL_DIR=/usr/lib/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib/ure/share/
      ```

   * CentOs

      Utilice los siguientes valores predeterminados:

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib64/libreoffice/ure/share/
      ```

* Para Java Development Kit (JDK):

   De forma predeterminada, la secuencia de comandos de configuración del entorno de Adobe Campaign (`~/nl6/env.sh`) busca el directorio de instalación de JDK. Dado que este comportamiento no es 100% fiable, debe especificar qué JDK debe utilizarse. Para ello, puede forzar la variable de entorno **JDK_HOME** mediante el siguiente comando:

   ```
   export JDK_HOME=/usr/java/jdk1.6.0_07
   ```

   >[!NOTE]
   >
   >Este es un ejemplo. Asegúrese de que la versión de JDK utilizada coincida con el nombre del directorio.

   Para probar la configuración de JDK, inicie sesión como usuario del sistema de Adobe Campaign con el siguiente comando:

   ```
   su - neolane
   ```

Debe reiniciar el servicio Adobe Campaign para que se tengan en cuenta los cambios.

Los comandos son los siguientes:

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

### Oracle Client en Linux {#oracle-client-in-linux}

Al utilizar Oracle con Adobe Campaign, debe configurar las capas de cliente de Oracle en Linux.

* Usar el cliente completo
* Definición TNS

   Las definiciones de TNS deben agregarse durante la fase de instalación. Para ello, utilice los siguientes comandos:

   ```
   cd /etc
   mkdir oracle
   cd oracle
   vi tnsnames.ora
   ```

* Variables de entorno

   Consulte las variables [de entorno](../../installation/using/installing-packages-with-linux.md#environment-variables).

* Configuración de Adobe Campaign

   Para finalizar la instalación del cliente de Oracle para Adobe Campaign, debe crear un vínculo simbólico para el archivo **.so** que utiliza Adobe Campaign.

   Para ello, utilice los siguientes comandos:

   ```
   cd /usr/lib/oracle/10.2.0.4/client/lib
   ln -s libclntsh.so.10.1 libclntsh.so
   ```

Si se produce un problema, asegúrese de que los paquetes enumerados en la documentación [de instalación de](http://www.oracle.com/pls/db112/portal.portal_db?selected=11) Oracle están correctamente instalados.

## Comprobaciones de instalación {#installation-checks}

Ahora puede realizar una prueba de instalación inicial con los siguientes comandos:

```
su - neolane
nlserver pdump
```

Cuando Adobe Campaign no se ha iniciado, la respuesta es:

```
no task
```

## Primera puesta en marcha del servidor {#first-start-up-of-the-server}

Una vez finalizada la prueba de instalación, introduzca el siguiente comando:

```
nlserver web
```

A continuación se muestra la siguiente información:

```
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

Estos comandos le permiten crear archivos de configuración **config-default.xml** y **serverConf.xml** . Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

Pulse **Ctrl+C** para detener el proceso y, a continuación, introduzca el siguiente comando:

```
nlserver start web
```

A continuación se muestra la siguiente información:

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Running task 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') in a new process
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Para detenerlo, introduzca:

```
nlserver stop web
```

A continuación se muestra la siguiente información:

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Contraseña del identificador interno {#password-for-the-internal-identifier}

El servidor de Adobe Campaign define un inicio de sesión técnico denominado **interno** que tiene todos los derechos en todas las instancias. Justo después de la instalación, el inicio de sesión no tiene contraseña. Es obligatorio definir uno.

Consulte la sección Identificador [interno](../../installation/using/campaign-server-configuration.md#internal-identifier).
