---
solution: Campaign Classic
product: campaign
title: Configuración de SpamAssassin
description: Configuración de SpamAssassin
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 0%

---


# Configuración de SpamAssassin{#configuring-spamassassin}

>[!NOTE]
>
>Algunas configuraciones sólo pueden ser realizadas por Adobe para implementaciones alojadas en Adobe. Por ejemplo, para acceder a los archivos de configuración de instancia y servidor. Para obtener más información sobre las diferentes implementaciones, consulte la sección [Hosting models](../../installation/using/hosting-models.md) o [esta página](../../installation/using/capability-matrix.md).

## Información general {#overview}

SpamAssassin es un software diseñado para filtrar correos electrónicos no deseados. Junto con este software, Adobe Campaign puede asignar una puntuación a los correos electrónicos y determinar si es probable que un mensaje se considere indeseable antes de que se inicie el envío. Para ello, SpamAssassin debe estar instalado y configurado en los servidores de aplicaciones de Adobe Campaign y requiere un cierto número de módulos Perl adicionales para funcionar.

La implementación y la integración de SpamAssassin como se describe en este capítulo se basan en la instalación de software predeterminada, al igual que las reglas de filtrado y puntuación, que son las que proporciona SpamAssassin ninguna modificación ni optimización. La atribución de puntuación y la calificación de mensajes se basan exclusivamente en la configuración de las opciones de SpamAssassin y en las reglas de filtrado. Los administradores de red son responsables de adaptarlos a las necesidades de su compañía.

>[!IMPORTANT]
>
>La calificación de los correos electrónicos como indeseables por SpamAssassin se basa completamente en reglas de filtrado y puntuación.
>
>Por lo tanto, estas reglas deben actualizarse al menos una vez al día para que la instalación de SpamAssassin y su integración en Adobe Campaign sean completamente funcionales y para garantizar la relevancia de las puntuaciones asignadas a sus envíos antes de enviarlas.
>
>Esta actualización es responsabilidad del administrador del servidor que aloja SpamAssassin.

El uso de SpamAssassin en Adobe Campaign proporciona una indicación del posible comportamiento de los servidores de correo que utilizan SpamAssassin cuando reciben correo electrónico enviado por Adobe Campaign. Sin embargo, es posible que los servidores de correo de proveedores de Internet o servidores de correo en línea sigan considerando indeseables los mensajes enviados por Adobe Campaign.

La implementación de SpamAssassin y sus módulos en Perl requiere servidores de aplicaciones de Adobe Campaign equipados con acceso a Internet a través de una conexión HTTP (flujo TCP/80).

## Instalación en un equipo Windows {#installing-on-a-windows-machine}

Para instalar y configurar SpamAssassin en Windows para habilitar la integración con Adobe Campaign, siga los pasos siguientes:

1. Instalar SpamAssassin
1. Integrar SpamAssassin en Adobe Campaign

### Instalación de SpamAssassin {#installing-spamassassin}

1. Conéctese al [portal de distribución de software](https://experience.adobe.com/downloads) con sus credenciales de usuario. Obtenga más información sobre la distribución de software en [esta página](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).
1. Descargue el archivo **Neolane Spam Assassin (Instalación de Windows) (2.0)** (neolane_spamassassin.2.0.zip).
1. Copie este archivo en el servidor de Adobe Campaign y descomprímalo.

   >[!NOTE]
   >
   >Puede elegir descomprimir el archivo donde desee siempre que la ruta esté formada por cualquiera de los siguientes caracteres de expresión normal: **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. La ruta de instalación no debe incluir caracteres de espacio en blanco.

1. Vaya al archivo en el que ha descomprimido el archivo y, a continuación, haga clic en el doble del archivo **run_me.bat** para iniciar la secuencia de comandos de instalación.

   Si aparece un Shell de Windows y se sigue mostrando durante unos segundos, espere hasta que la instalación y la actualización hayan finalizado y, a continuación, haga clic en **Entrar**.

   Si el shell de Windows no aparece o no se muestra antes de que desaparezca instantáneamente, siga estos pasos y haga clic con el doble en el archivo **portableShell.bat** para mostrar un shell de Windows y compruebe que la ruta del shell corresponde a la carpeta en la que se descomprimió el archivo **spamassassin.zip**. Si este no es el caso, acceda a él mediante el comando **cd**.

   Introduzca **run_me.bat** y haga clic en **Intro** para inicio del proceso de instalación y actualización. La operación devuelve uno de los siguientes valores para indicar el resultado de la actualización.

   * **0**: se ha realizado una actualización.
   * **1**: No hay ninguna actualización nueva disponible.
   * **2**: no hay ninguna actualización nueva disponible.
   * **3**: error de actualización durante la verificación previa.
   * **4** o más: se ha producido un error.

1. Para comprobar que la instalación de SpamAssassin se ha realizado correctamente, utilice la prueba GTUBE (Generic Test for Unsolicited Bulk Email) siguiendo el siguiente procedimiento:

   1. Cree un archivo de texto y guárdelo en **C:\TestSpamMail.txt**.
   1. Inserte el siguiente contenido en el archivo:

      ```
      Subject: Test Spam Mail (GTUBE)
      Message-ID: <1010101@example.net>
      Date: MM-DD-YY
      From: Sender <sender@example.net>
      To: Recipient <recipient@example.net>
      Precedence: junk
      MIME-Version: 1.0
      Content-Type: text/plain; charset=us-ascii
      Content-Transfer-Encoding: 7bit
      
      XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
      ```

   1. Haga clic con el botón doble en el archivo **portableShell.bat** para mostrar un shell de Windows y, a continuación, inicie el siguiente comando (o bien, &quot;`<root>`&quot; designa la carpeta creada al descomprimir el archivo **spamassassin.zip**):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      El contenido de este correo electrónico de prueba desencadena una puntuación de 1000 puntos por SpamAssassin. Esto significa que se ha detectado que no es deseable y que la instalación se ha realizado correctamente y es totalmente funcional.

### Integración de SpamAssassin en Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. Edite el archivo **`[INSTALL]/conf/serverConf.xml`**. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).
1. Cambie el valor del atributo **spamCheck** elements&#39; **command** en el nodo **Web**. Para ello, ejecute el siguiente comando:

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >Todas las rutas deben ser absolutas.

   Detenga y inicio el servicio **[!UICONTROL Adobe Campaign]**.

1. Para comprobar la integración de SpamAssassin en Adobe Campaign, utilice una prueba GTBUE (Prueba genérica para correo electrónico masivo no solicitado):

   Haga clic con el doble en el archivo **portable.bat**. Esto activa la visualización de un shell de Windows. A continuación, ejecute el siguiente comando:

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   El contenido de este correo electrónico de prueba desencadena 1000 puntos asignados por SpamAssassin. Esto significa que se ha detectado que no es deseable y que la integración en Adobe Campaign ha tenido éxito y es totalmente funcional.

1. Actualización de reglas de puntuación y filtrado de SpamAssassin

   Para una actualización inicial de las reglas de filtrado y puntuación, inicio **portableShell.bat** y ejecute el siguiente comando:

   ```
   sa-update --no-gpg
   ```

   Para ejecutar una actualización automática de las reglas de filtrado y puntuación, utilice este mismo comando en una tarea del sistema programada:

   ```
   sa-update --no-gpg
   ```

## Instalación en un equipo Linux {#installing-on-a-linux-machine}

### Pasos de instalación en Debian {#installation-steps-in-debian}

* Si es necesario, instale Perl y SpamAssassin con el siguiente comando:

   ```
   apt-get install spamassassin libxml-writer-perl
   ```

* En el archivo **serverConf.xml** (disponible en `/usr/local/[INSTALL]/nl6/conf/`), cambie la línea **spamCheck** de la siguiente manera:

   ```
   <spamCheck command="perl
   /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
   ```

### Pasos de instalación en RHEL/CentOS {#installation-steps-in-rhel-centos}

Si es necesario, instale Perl y recupere los paquetes usando CPAN:

```
cpan Digest::SHA1
cpan HTML::Parser
cpan Net::DNS
cpan Mail::SPF 
cpan XML::LibXML
cpan XML::Writer
cpan Mail::SpamAssassin
```

### Actualizando reglas de filtro {#updating-filter-rules}

Las reglas de filtro se pueden actualizar automáticamente mediante la herramienta **sa-update**. Consulte el sitio web oficial de SpamAssassin [http://spamassassin.apache.org/](http://spamassassin.apache.org/) para obtener más información.

En Debian, las actualizaciones se realizan automáticamente todos los días.

Si este no es el caso (por ejemplo, cuando Debian se instala manualmente), cree un script para automatizar las actualizaciones de reglas.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

Inserte esta secuencia de comandos en **crontab** mediante el siguiente comando:

```
crontab-e
```

### Optimización del rendimiento {#performance-optimization}

Para mejorar el rendimiento en Linux, edite el archivo **/etc/spamassassin/local.cf** y agregue la línea siguiente al final del archivo:

```
dns_available no
```

