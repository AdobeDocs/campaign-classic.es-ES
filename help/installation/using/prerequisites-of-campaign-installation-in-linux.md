---
solution: Campaign Classic
product: campaign
title: Requisitos previos para la instalación de Campaign en Linux
description: Requisitos previos para la instalación de Campaign en Linux
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 2%

---


# Requisitos previos para la instalación de Campaign en Linux{#prerequisites-of-campaign-installation-in-linux}

## Requisitos previos de software {#software-prerequisites}

En esta sección se detallan los pasos de configuración preliminares necesarios antes de instalar Adobe Campaign.

La configuración técnica y de software necesaria para instalar Adobe Campaign se detalla en la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md).

Como recordatorio, es necesario instalar y configurar correctamente los siguientes componentes:

* Apache, consulte [Tabla de compatibilidad](../../rn/using/compatibility-matrix.md),
* Java JDK y OpenJDK, consulte [Java Development Kit - JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* Bibliotecas, consulte [Bibliotecas](#libraries),
* Capas de acceso a la base de datos, consulte [Capas de acceso a la base de datos](#database-access-layers),
* LibreOffice, consulte [Instalación de LibreOffice para Debian](#installing-libreoffice-for-debian) y [Instalación de LibreOffice para CentOS](#installing-libreoffice-for-centos),
* Fuentes, consulte [Fuentes para estadísticas de MTA](#fonts-for-mta-statistics) y [Fuentes para instancias japonesas](#fonts-for-japanese-instances).

>[!NOTE]
>
>Para instalar una compilación inferior o igual a 8709 en las plataformas CentOS 7 y Debian 8, el módulo apache access_compat debe estar habilitado.

### Bibliotecas {#libraries}

Para instalar Adobe Campaign en Linux, asegúrese de tener las bibliotecas necesarias.

* La biblioteca C debe poder admitir el modo TLS (Almacenamiento local de subprocesos). Este modo está activo en la mayoría de los casos excepto con algunos núcleos para los que se ha deshabilitado la compatibilidad con Xen.

   Para comprobar esto, puede utilizar el **nombre -a | grep xen**, por ejemplo.

   Si el comando no devuelve nada (línea vacía), significa que la configuración es correcta.

* Debe tener **versión 0.9.8** o **1.0** de OpenSSL.

   Para distribuciones RHEL 7, se requiere la versión 1.0 de OpenSSL.

* Para utilizar Adobe Campaign, debe tener instalada la biblioteca **libicu**.

   Se admiten las siguientes versiones de **libicu** (32 bits o 64 bits):

   * RHEL 7, CentOS 7: libicu50
   * Debian 8: libicu52
   * Debian 9: libicu57

   Para usar Adobe Campaign, necesita tener instalada la biblioteca libc-ares. En RHEL/CentOS, ejecute el siguiente comando:

   ```
   yum install c-ares
   ```

   Sobre Debian:

   ```
   aptitude install libc-ares2
   ```

### SELinux {#selinux}

Cuando se utiliza, el módulo SELinux debe configurarse correctamente.

Para ello, inicie sesión como raíz e introduzca el siguiente comando:

```
echo 0 >/selinux/enforce
```

Además de esto, en el archivo **/etc/sysconfig/httpd** se agregó la línea siguiente para hacer referencia al script de configuración de Adobe Campaign entorno:

```
. ~neolane/nl6/env.sh
```

En RHEL y CentOS, se observaron problemas de compatibilidad con los niveles de cliente de las bases de datos cuando SELinux está habilitado. Para estar seguro de que Adobe Campaign puede funcionar correctamente, recomendamos desactivar SELinux.

**Aplique el siguiente proceso:**

* Editar el archivo **/etc/selinux/config**

* Modifique la línea SELINUX de la siguiente manera:

```
SELINUX=disabled
```

### Fuentes para estadísticas de MTA {#fonts-for-mta-statistics}

Para que los informes sobre estadísticas de MTA (nms/fra/jsp/stat.jsp) se muestren correctamente, agregue fuentes.

En Debian, agregue el comando:

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

En Redhat, utilice el siguiente comando:

```
yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
```

### Fuentes para instancias de japonés {#fonts-for-japanese-instances}

Las fuentes de caracteres específicos son necesarias para las instancias japonesas a fin de exportar los informes al formato PDF.

En Debian, agregue el comando:

```
aptitude install fonts-ipafont
```

En Red Hat, agregue el comando:

```
yum install ipa-gothic-fonts ipa-mincho-fonts
```

### Instalación de LibreOffice para Debian {#installing-libreoffice-for-debian}

Para Debian, se requieren las siguientes configuraciones:

1. Instale los siguientes paquetes estándar:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Instale las siguientes fuentes (opcional pero muy recomendable para las instancias de japonés):

   ```
   apt-get install fonts-ipafont
   ```

### Instalación de LibreOffice para CentOS {#installing-libreoffice-for-centos}

Las siguientes configuraciones son necesarias con CentOS:

1. Instale los siguientes paquetes estándar:

   ```
   yum install libreoffice-headless libreoffice-writer libreoffice-calc
   ```

1. Instale las fuentes siguientes (opcional pero muy recomendable para las instancias de japonés):

   ```
   yum install ipa-gothic-fonts ipa-mincho-fonts
   ```

## Capas de acceso a base de datos {#database-access-layers}

Las capas de acceso para el motor de base de datos que está utilizando deben estar instaladas en el servidor y ser accesibles a través de la cuenta de Adobe Campaign. Las versiones y los modos de instalación pueden variar en función del motor de base de datos utilizado.

La versión piloto admitida se detalla en la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md).

Consulte también la sección general [Base de datos](../../installation/using/database.md).

### PostgreSQL {#postgresql}

Adobe Campaign admite todas las versiones de las bibliotecas cliente PostgreSQL de la versión 7.2: (**libpq.so.5**, **libpq.so.4**, **libpq.so.3.2** y **libpq.so.3.1**).

El uso de PostgreSQL con Adobe Campaign también requiere la instalación de las bibliotecas **pgcrypto** correspondientes.

### Oracle {#oracle}

Recupere la versión de la biblioteca para Debian de 64 bits, es decir: **libclntsh.so**, **libclntsh.so.11.1** y **libclntsh.so.10.1**.

Puede obtener un paquete RPM de Linux de la red de tecnología Oracle.

>[!NOTE]
>
>Si ya ha instalado el cliente de Oracle pero el entorno global (por ejemplo: /etc/perfil) no está configurado correctamente, puede agregar la información que falta a la **nl6/customer.sh** secuencia de comandos Para obtener más información sobre esto, consulte [Variables de Entorno](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Solución de problemas y prácticas recomendadas**

Los problemas pueden aparecer después de una actualización de un cliente de Oracle o de un servidor, un cambio de versión o en la primera instalación de la instancia.

Si observa en la consola del cliente que hay retrasos inesperados (una o más horas) en los registros, en el último procesamiento del flujo de trabajo, en el siguiente procesamiento, etc., es posible que haya un problema entre la biblioteca del cliente Oracle y el servidor Oracle. Para evitar esos problemas

1. Asegúrese de utilizar el **cliente completo**.

   Se han identificado varios problemas al usar la versión de Oracle Instant Client. Además, es imposible cambiar el archivo de zona horaria en el cliente instantáneo.

1. Asegúrese de que la **versión del cliente** y la **versión del servidor de la base de datos** son **iguales**.

   Se sabe que la mezcla de versiones a pesar de la matriz de compatibilidad de Oracle y la recomendación de alinear versiones de cliente y servidor causa problemas.

   Compruebe también el valor de ORACLE_HOME para asegurarse de que apunta a la versión del cliente esperada (en caso de que se instalen varias versiones en el equipo).

1. Asegúrese de que el cliente y el servidor utilicen el mismo **archivo de zona horaria**.

### DB2 {#db2}

La versión de biblioteca admitida es **libdb2.so**.

## Pasos de implementación {#implementation-steps}

Las instalaciones de Adobe Campaign para Linux deben realizarse en la siguiente secuencia: instalación del servidor seguida de la configuración de la instancia.

El proceso de instalación se describe en este capítulo. Los pasos de instalación son los siguientes:

* Paso 1: Instalación del servidor de aplicaciones, consulte [Instalación de paquetes con Linux](../../installation/using/installing-packages-with-linux.md).
* Paso 2: Integración con un servidor web (opcional, según los componentes implementados).

Una vez completados los pasos de instalación, debe configurar las instancias, la base de datos y el servidor. Para obtener más información sobre esto, consulte [Acerca de la configuración inicial](../../installation/using/about-initial-configuration.md).
