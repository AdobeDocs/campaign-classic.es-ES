---
product: campaign
title: Requisitos previos para la instalación de Campaign en Linux
description: Requisitos previos para Campaign instalación en Linux
feature: Installation, Instance Settings
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 1%

---

# Requisitos previos para instalar Campaign en Linux{#prerequisites-of-campaign-installation-in-linux}

## Requisitos previos de software {#software-prerequisites}

Esta sección detalla los pasos de configuración preliminares necesarios antes de instalar Adobe Campaign.

La configuración técnica y de software necesaria para instalar Adobe Campaign se detalla en la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md).

Como recordatorio, los siguientes componentes deben instalarse y configurarse correctamente:

* Apache, consulte [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md),
* Java JDK y OpenJDK, consulte [Kit de desarrollo de Java - JDK](../../installation/using/application-server.md#jdk),
* Bibliotecas, consulte [Bibliotecas](#libraries),
* Capas de acceso a bases de datos, consulte [Capas de acceso a bases de datos](#database-access-layers),
* LibreOffice, consulte [Instalación de LibreOffice para Debian](#installing-libreoffice-for-debian) e [Instalación de LibreOffice para CentOS](#installing-libreoffice-for-centos),
* Fuentes, consulte [Fuentes para estadísticas de MTA](#fonts-for-mta-statistics) y [Fuentes para instancias de japonés](#fonts-for-japanese-instances).


### Bibliotecas {#libraries}

Para instalar Adobe Campaign en Linux, asegúrese de tener la bibliotecas necesaria.

* La biblioteca C debe ser compatible con el modo TLS (almacenamiento local de subprocesos). Este modo está activo en la mayoría de los casos, excepto con algunos núcleos para los que se ha desactivado el soporte de Xen.

  Para comprobar esto, puede utilizar el **comando uname -a | grep xen** , por ejemplo.

  Si el comando no devuelve una línea vacía, significa que la configuración es correcta.

* Debe tener la versión de OpenSSL **1.0.2** o superior.

  Para las distribuciones RHEL, se requiere la versión 1.0 de OpenSSL.

* Para usar Adobe Campaign, debes tener instalada la biblioteca **libicu**.

### SELinux {#selinux}

Cuando se utiliza, el módulo SELinux debe estar configurado correctamente.

Para ello, inicie sesión como root e introduzca el siguiente comando:

```
echo 0 >/selinux/enforce
```

Además, en el archivo **/etc/sysconfig/httpd**, se agregó la línea siguiente para hacer referencia al script de configuración del entorno de Adobe Campaign:

```
. ~neolane/nl6/env.sh
```

En RHEL y CentOS, los problemas de compatibilidad con las capas de cliente de bases de datos se observaron cuando SELinux está habilitado. Para asegurarse de que Adobe Campaign puede funcionar correctamente, se recomienda desactivar SELinux.

**Aplicar el proceso siguiente:**

* Edite el archivo **/etc/selinux/config**

* Modifique la línea SELINUX de la siguiente manera:

```
SELINUX=disabled
```

### Fuentes para estadísticas de MTA {#fonts-for-mta-statistics}

Para que los informes sobre las estadísticas de MTA (nms/fra/jsp/stat.jsp) se muestren correctamente, agregue fuentes.

En Debian, añada el comando:

```
apt install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

Utilice el siguiente comando para RHEL:

```
dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
```

### Fuentes para instancias japonesas {#fonts-for-japanese-instances}

Fuentes de caracteres específicos son necesarios para las instancias de Japonés con el fin de exportar los informes a PDF formato.

En Debian, añada el comando:

```
apt install fonts-ipafont
```

Para RHEL, agregue el siguiente comando:

```
dnf install epel-release # if required
dnf install vlgothic-fonts
```

### Instalación de LibreOffice para Debian {#installing-libreoffice-for-debian}

Para Debian, se requieren las siguientes configuraciones:

1. Instale los siguientes paquetes estándar:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Instale las siguientes fuentes (opcionales pero muy recomendables para Japonés instancias):

   ```
   apt-get install fonts-ipafont
   ```

### Instalación de LibreOffice para CentOS {#installing-libreoffice-for-centos}

Las siguientes configuraciones son necesarias con CentOS:

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## Capas de acceso a la base de datos {#database-access-layers}

Las capas de acceso para el motor de base de datos que está utilizando deben estar instaladas en su servidor y ser accesibles a través del Adobe Campaign cuenta. Las versiones y los modos de instalación pueden variar según el motor de base de datos utilizado.

Las versiones piloto compatibles se detallan en la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md).

Compruebe también la sección general [Base de datos](../../installation/using/database.md).

### PostgreSQL {#postgresql}

Adobe Campaign admite todas las versiones de las bibliotecas de cliente PostgreSQL de la versión 9.6: **libpq.so.5**.

El uso de PostgreSQL con Adobe Campaign también requiere la instalación de las bibliotecas **pgcrypto** correspondientes.

### Oracle {#oracle}

Recupere la versión biblioteca para Debian de 64 bits, es decir: libclntsh.so, libclntsh.so.19.1 **,** libclntsh.so.18.1 **,** libclntsh.so.12.1 **,** libclntsh.so.11.1 **o** libclntsh.so.10.1 **.**&#x200B;**&#x200B;**

Puede obtener un paquete RPM de Linux de Oracle Technology Network.

>[!NOTE]
>
>Si ya ha instalado el cliente Oracle pero el entorno global (para instancia: /etcetera/perfil) no está configurado correctamente, puede agregar la **información que falta al script nl6/customer.sh** Para obtener más información, consulte Variables [&#128279;](../../installation/using/installing-packages-with-linux.md#environment-variables)de entorno.

**Solución de problemas y prácticas recomendadas**

Los problemas pueden aparecer después de que un cliente de Oracle o un servidor actualicen, cambien de versión o en la primera instalación de la instancia.

Si observa en la consola del cliente que hay retrasos inesperados (una o más horas) en los registros, el último procesamiento del flujo de trabajo, el siguiente procesamiento, etc., puede haber un problema entre la biblioteca del cliente de Oracle y el servidor de Oracle. Para evitar tales problemas

1. Asegúrese de usar **cliente completo**.

   Se han identificado varios problemas al utilizar la versión Oracle Instant Client. Además, es imposible cambiar el archivo Timezone en el cliente instantáneo.

1. Asegúrese de que la versión del **cliente y la versión** del servidor de **base de datos son iguales**&#x200B;**.**

   Se sabe que la combinación de versiones a pesar de la matriz de compatibilidad de Oracle y la recomendación de alinear las versiones de cliente y servidor causa problemas.

   Compruebe también el valor de ORACLE_HOME para asegurarse de que señala a la versión de cliente esperada (en caso de que haya varias versiones instaladas en el equipo).

1. Asegúrese de que el cliente y el servidor usen el mismo **archivo de zona horaria**.

## Pasos de implementación {#implementation-steps}

Las instalaciones de Adobe Campaign para Linux deben llevarse a cabo en la siguiente secuencia: instalación del servidor seguida de la configuración de la instancia.

El proceso de instalación se describe en este capítulo. Los pasos de instalación son los siguientes:

* Paso 1: Instalación del servidor de aplicaciones, consulte [Instalación de paquetes con Linux](../../installation/using/installing-packages-with-linux.md).
* Paso 2: Integración con un servidor web (opcional, según los componentes implementados).

Una vez completados los pasos de instalación, debe configurar las instancias, la base de datos y el servidor. Para obtener más información, consulte [Acerca de la configuración inicial](../../installation/using/about-initial-configuration.md).
