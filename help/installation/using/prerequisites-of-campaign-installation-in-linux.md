---
product: campaign
title: Requisitos previos para la instalación de Campaign en Linux
description: Requisitos previos para la instalación de Campaign en Linux
feature: Installation, Instance Settings
badge-v7-prem: label="Solo local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 1%

---

# Requisitos previos para instalar Campaign en Linux{#prerequisites-of-campaign-installation-in-linux}



## Requisitos previos de software {#software-prerequisites}

Esta sección detalla los pasos de configuración preliminares necesarios antes de instalar Adobe Campaign.

La configuración técnica y de software necesaria para instalar Adobe Campaign se detalla en la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md).

Como recordatorio, los siguientes componentes deben instalarse y configurarse correctamente:

* Apache, consulte Compatibilidad [matriz](../../rn/using/compatibility-matrix.md),
* Java JDK y OpenJDK, consulte Kit de [desarrollo de Java - JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* Bibliotecas, consulte [Bibliotecas](#libraries),
* Capas de acceso a la base de datos, consulte Capas](#database-access-layers) de acceso a [la base de datos,
* LibreOffice, consulte [Instalación de LibreOffice para Debian](#installing-libreoffice-for-debian) y [Instalación de LibreOffice para CentOS](#installing-libreoffice-for-centos),
* Fuentes, consulte [Fuentes para estadísticas de MTA](#fonts-for-mta-statistics) y [Fuentes para instancias japonesas](#fonts-for-japanese-instances).

>[!NOTE]
>
>Para instalar una compilación inferior o igual a 8709 en las plataformas CentOS 7 y Debian 8, el módulo apache access_compat debe estar habilitado.

### Bibliotecas {#libraries}

Para instalar Adobe Campaign en Linux, asegúrese de tener la bibliotecas necesaria.

* La biblioteca C debe ser compatible con el modo TLS (almacenamiento local de subprocesos). Este modo está activo en la mayoría de los casos, excepto con algunos núcleos para los que se ha desactivado el soporte de Xen.

  Para comprobar esto, puede utilizar el **comando uname -a | grep xen** , por ejemplo.

  Si el comando no devuelve nada (línea vacía), significa que la configuración es correcta.

* Debe tener la versión de OpenSSL **1.0.2** o superior.

  Para las distribuciones RHEL 7/8, se requiere la versión 1.0 de OpenSSL.

* Para utilizar Adobe Campaign, debe tener el **libicu** biblioteca instalada.

  Las siguientes versiones de **libicu** son compatibles (32 o 64 bits):

   * RHEL 7/8, CentOS 7: libicu50
   * Debian 8: libicu52
   * Debian 9: libicu57

  Para utilizar Adobe Campaign, debe tener instalada la biblioteca libc-ares. En RHEL/CentOS, ejecute el siguiente comando:

  ```
  yum install c-ares
  ```

  En Debian:

  ```
  aptitude install libc-ares2
  ```

### Selinux {#selinux}

Cuando se utiliza, el módulo SELinux debe estar configurado correctamente.

Para ello, inicie sesión como root e introduzca el siguiente comando:

```
echo 0 >/selinux/enforce
```

Además de esto, en la variable **/etc/sysconfig/httpd** , se agregó la siguiente línea para hacer referencia al script de configuración del entorno de Adobe Campaign:

```
. ~neolane/nl6/env.sh
```

En RHEL y CentOS, los problemas de compatibilidad con las capas de cliente de bases de datos se observaron cuando SELinux está habilitado. Para asegurarse de que Adobe Campaign puede funcionar correctamente, se recomienda desactivar SELinux.

**Siga el siguiente proceso:**

* Editar el archivo **/etc/selinux/config**

* Modifique la línea SELINUX de la siguiente manera:

```
SELINUX=disabled
```

### Fuentes para estadísticas de MTA {#fonts-for-mta-statistics}

Para que los informes sobre las estadísticas de MTA (NMS/FRA/JSP/stat.jsp) se muestren correctamente, agregue fuentes.

En Debian, añada el comando:

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

En Redhat, utilice el siguiente comando:

* Para CentOS/RHEL 7:

  ```
  yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
  ```

* Para RHEL 8:

  ```
  dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
  ```

### Fuentes para instancias japonesas {#fonts-for-japanese-instances}

Se necesitan fuentes de caracteres específicos para las instancias japonesas a fin de exportar los informes al formato de PDF.

En Debian, añada el comando:

```
aptitude install fonts-ipafont
```

En Red Hat, agregue el comando:

* Para RHEL 7:

  ```
  yum install ipa-gothic-fonts ipa-mincho-fonts
  ```

* Para RHEL 8:

  ```
  dnf install vlgothic-fonts
  ```

### Instalación de LibreOffice para Debian {#installing-libreoffice-for-debian}

Para Debian, se requieren las siguientes configuraciones:

1. Instale los siguientes paquetes estándar:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Instale las siguientes fuentes (opcional pero muy recomendable para instancias japonesas):

   ```
   apt-get install fonts-ipafont
   ```

### Instalación de LibreOffice para CentOS {#installing-libreoffice-for-centos}

Las siguientes configuraciones son necesarias con CentOS:

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## Capas de acceso a la base de datos {#database-access-layers}

Las capas de acceso para el motor de base de datos que utilice deben estar instaladas en el servidor y ser accesibles a través de la cuenta de Adobe Campaign. Las versiones y los modos de instalación pueden variar según el motor de base de datos utilizado.

La versión piloto admitida se detalla en la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md).

Compruebe también la información general [Base de datos](../../installation/using/database.md) sección.

### PostgreSQL {#postgresql}

Adobe Campaign es compatible con todas las versiones de las bibliotecas de cliente PostgreSQL de la versión 7.2: (**libpq.so.5**, **libpq.so.4**, **libpq.so.3.2** y **libpq.so.3.1**).

El uso de PostgreSQL con Adobe Campaign también requiere la instalación del correspondiente **pgcrypto** bibliotecas.

### Oracle {#oracle}

Recupere la versión de la biblioteca para Debian de 64 bits, por ejemplo: **libclntsh.so**, **libclntsh.so.11.1** y **libclntsh.so.10.1**.

Puede obtener un paquete RPM de Linux de la Red de Tecnología de Oracle.

>[!NOTE]
>
>Si ya ha instalado el cliente de Oracle pero el entorno global (por ejemplo: /etc/profile) no está configurado correctamente, puede añadir la información que falta a **nl6/customer.sh** script Para obtener más información, consulte [Variables de entorno](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Solución de problemas y prácticas recomendadas**

Los problemas pueden aparecer después de una actualización del cliente Oracle o del servidor, cambio de versión o en la primera instalación del instancia.

Si observa en la consola del cliente que hay retrasos inesperados (una o más horas) en los registros, flujo de trabajo último procesamiento, siguiente procesamiento, etc., puede haber un problema entre el biblioteca del cliente Oracle y el servidor de Oracle. Para evitar estos problemas

1. Asegúrese de utilizar el **cliente completo**.

   Se han identificado varios problemas al utilizar la versión de cliente instantáneo de Oracle. Además, es imposible cambiar el archivo Timezone en un cliente instantáneo.

1. Asegúrese de que la variable **versión de cliente** y el **versión del servidor de base de datos** son las **igual**.

   Se sabe que la combinación de versiones a pesar de la matriz de compatibilidad de Oracle y la recomendación de alinear las versiones de cliente y servidor causa problemas.

   Compruebe también ORACLE_HOME valor para asegurarse de que apunta a la versión de cliente esperada (en caso de que haya varias versiones instaladas en el equipo).

1. Asegúrese de que el cliente y el servidor utilicen el mismo **archivo** de zona horaria.

### DB2 {#db2}

La versión biblioteca admitida es **libdb2.so**.

## Pasos de implementación {#implementation-steps}

Las instalaciones de Adobe Campaign para Linux deben llevarse a cabo en la siguiente secuencia: instalación del servidor seguida de la configuración de la instancia.

El proceso de instalación se describe en este capítulo. Los pasos de instalación son los siguientes:

* Paso 1: Instalación del servidor de aplicaciones, consulte [Instalación de paquetes con Linux](../../installation/using/installing-packages-with-linux.md).
* Paso 2: Integración con un servidor web (opcional, según los componentes implementados).

Una vez completados los pasos de instalación, debe configurar las instancias, la base de datos y el servidor. Para obtener más información, consulte [Acerca de la configuración inicial](../../installation/using/about-initial-configuration.md).
