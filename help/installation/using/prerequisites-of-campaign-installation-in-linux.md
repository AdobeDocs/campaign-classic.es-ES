---
product: campaign
title: Requisitos previos para la instalación de Campaign en Linux
description: Requisitos previos para la instalación de Campaign en Linux
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
badge-v7-prem: label="on-premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 4%

---

# Requisitos previos para instalar Campaign en Linux{#prerequisites-of-campaign-installation-in-linux}



## Requisitos previos de software {#software-prerequisites}

En esta sección se detallan los pasos de configuración preliminares necesarios para instalar Adobe Campaign.

La configuración técnica y de software necesaria para instalar Adobe Campaign se detalla en la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md).

Como recordatorio, los siguientes componentes deben instalarse y configurarse correctamente:

* Apache, consulte [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md),
* Java JDK y OpenJDK, consulte [Kit de desarrollo de Java: JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* Bibliotecas, consulte [Bibliotecas](#libraries),
* Capas de acceso a bases de datos, consulte [Capas de acceso a base de datos](#database-access-layers),
* LibreOffice, consulte [Instalación de LibreOffice para Debian](#installing-libreoffice-for-debian) y [Instalación de LibreOffice para CentOS](#installing-libreoffice-for-centos),
* Fuentes, consulte [Fuentes para estadísticas de MTA](#fonts-for-mta-statistics) y [Fuentes para instancias japonesas](#fonts-for-japanese-instances).

>[!NOTE]
>
>Para instalar una compilación inferior o igual a 8709 en las plataformas CentOS 7 y Debian 8, el módulo apache access_compat debe estar habilitado.

### Bibliotecas {#libraries}

Para instalar Adobe Campaign en Linux, asegúrese de que dispone de las bibliotecas requeridas.

* La biblioteca C debe poder admitir el modo TLS (almacenamiento local de subprocesos). Este modo está activo en la mayoría de los casos, excepto con algunos kernels para los que se ha desactivado la compatibilidad con Xen.

  Para comprobarlo, puede utilizar el **comando uname-a | grep Xen** , por ejemplo.

  Si el comando no devuelve nada (línea vacía), significa que la configuración es correcta.

* Debe tener la versión de OpenSSL **1.0.2** o superior.

  Para las distribuciones RHEL 7/8, se requiere la versión 1.0 de OpenSSL.

* Para utilizar Adobe Campaign, debe tener **instalado libicu** biblioteca.

  Se admiten las siguientes versiones de **libicu** (32 bits o 64 bits):

   * RHEL 7/8, aclibicu50 7:
   * Debian 8: libicu52
   * Debian 9: libicu57

  Para utilizar Adobe Campaign, debe tener instalado libc-áreas biblioteca. En RHEL/CentOS, ejecute el siguiente comando:

  ```
  yum install c-ares
  ```

  En Debian:

  ```
  aptitude install libc-ares2
  ```

### SELinux {#selinux}

Cuando se utiliza, el módulo SELinux debe configurarse correctamente.

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

Para que los informes sobre las estadísticas de MTA (NMS/FRA/JSP/stat. jsp) se muestren correctamente, agregue fuentes.

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

### Fuentes para instancias de Japonés {#fonts-for-japanese-instances}

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

Las siguientes configuraciones son necesarias con la de la:

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## Capas de acceso a bases de datos {#database-access-layers}

Las capas de acceso para el motor de base de datos que utilice deben estar instaladas en el servidor y ser accesibles a través de la cuenta de Adobe Campaign. Las versiones y los modos de instalación pueden variar según el motor de base de datos utilizado.

La versión piloto admitida se detalla en la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md).

Compruebe también la información general [Base de datos](../../installation/using/database.md) sección.

### PostgreSQL {#postgresql}

Adobe Campaign es compatible con todas las versiones de la bibliotecas del cliente PostgreSQL de la versión 7,2: ( **libpq. por ejemplo, 5** , **libpq. por ejemplo: 4** , libpq. por ejemplo, **etc. 3.2** y **libpq. por ejemplo. 3.1** ).

El uso de PostgreSQL con Adobe Campaign también requiere la instalación de los bibliotecas de pgcrypto **correspondientes** .

### Oracle {#oracle}

Recupere la versión biblioteca para 64-bit Debian, por ejemplo: **libclntsh.so** , libclntsh. por ejemplo, **11.1** y **libclntsh. so. 10.1** .

Puede obtener un paquete de Linux RPM desde la red tecnológica de Oracle.

>[!NOTE]
>
>Si ya ha instalado el cliente de Oracle pero el entorno global (por ejemplo: /etc/profile) no está configurado correctamente, puede añadir la información que falta a **nl6/customer.sh** script Para obtener más información, consulte [Variables de entorno](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Solución de problemas y prácticas recomendadas**

Los problemas pueden aparecer después de que un cliente de Oracle o un servidor actualicen, cambien de versión o en la primera instalación de la instancia.

Si observa en la consola del cliente que hay retrasos inesperados (una o más horas) en los registros, el último procesamiento del flujo de trabajo, el siguiente procesamiento, etc., puede haber un problema entre la biblioteca del cliente de Oracle y el servidor de Oracle. Para evitar tales problemas

1. Asegúrese de utilizar el **cliente completo**.

   Se han identificado varios problemas al utilizar la versión de cliente instantáneo de Oracle. Además, es imposible cambiar el archivo Timezone en un cliente instantáneo.

1. Asegúrese de que la variable **versión de cliente** y el **versión del servidor de base de datos** son las **igual**.

   Se sabe que la combinación de versiones a pesar de la matriz de compatibilidad de Oracle y la recomendación de alinear las versiones de cliente y servidor causa problemas.

   Compruebe también el valor de ORACLE_HOME para asegurarse de que señala a la versión de cliente esperada (en caso de que haya varias versiones instaladas en el equipo).

1. Asegúrese de que el cliente y el servidor utilicen lo mismo **archivo de zona horaria**.

### DB2 {#db2}

La versión de biblioteca admitida es **libdb2.so** .

## Pasos de implementación {#implementation-steps}

Las instalaciones de Adobe Campaign para Linux deben llevarse a cabo en la siguiente secuencia: instalación del servidor seguida de la configuración de la instancia.

El proceso de instalación se describe en este capítulo. Los pasos de instalación son los siguientes:

* Paso 1: instalación del servidor de aplicación, consulte [ instalación de paquetes con Linux ](../../installation/using/installing-packages-with-linux.md) .
* Paso 2: integración con un servidor Web (opcional, según los componentes implementados).

Una vez completados los pasos de la instalación, debe configurar las instancias, la base de datos y el servidor. Para obtener más información, consulte [ acerca de la configuración ](../../installation/using/about-initial-configuration.md) inicial.
