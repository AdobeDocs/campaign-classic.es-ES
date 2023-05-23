---
product: campaign
title: Configuración de SpamAssassin
description: Configuración de SpamAssassin
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 1f1004e2-dcd2-4ec5-98ec-720c205646d5
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 2%

---

# Configuración de SpamAssassin{#configuring-spamassassin}



>[!NOTE]
>
>Algunas configuraciones solo se pueden realizar mediante el Adobe para implementaciones alojadas por el Adobe. Por ejemplo, para acceder a los archivos de configuración del servidor y de la instancia. Para obtener más información sobre las distintas implementaciones, consulte la [Modelos de alojamiento](../../installation/using/hosting-models.md) o a [esta página](../../installation/using/capability-matrix.md).

## Información general {#overview}

SpamAssassin es un software diseñado para filtrar correos electrónicos no deseados. Junto con este software, Adobe Campaign puede asignar una puntuación a los correos electrónicos y determinar si es probable que un mensaje se considere no deseado antes de que se inicie la entrega. Para ello, SpamAssassin debe instalarse y configurarse en los servidores de aplicaciones de Adobe Campaign y requiere un determinado número de módulos Perl adicionales para funcionar.

La implementación y la integración de SpamAssassin, tal como se describe en este capítulo, se basan en la instalación de software predeterminada, al igual que las reglas de filtrado y puntuación, que son las proporcionadas por SpamAssassin sin ninguna alteración ni optimización. La atribución de puntuación y la calificación de mensajes se basan exclusivamente en la configuración de las opciones de SpamAssassin y en las reglas de filtrado. Los administradores de red son responsables de adaptarlos a las necesidades de su empresa.

>[!IMPORTANT]
>
>La calificación de correos electrónicos como no deseados por SpamAssassin se basa completamente en reglas de filtrado y puntuación.
>
>Por lo tanto, estas reglas deben actualizarse al menos una vez al día para que la instalación de SpamAssassin y su integración en Adobe Campaign sean completamente funcionales y garanticen la relevancia de las puntuaciones asignadas a los envíos antes de enviarlos.
>
>Esta actualización es responsabilidad del administrador del servidor que aloja SpamAssassin.

El uso de SpamAssassin en Adobe Campaign proporciona una indicación sobre el posible comportamiento de los servidores de correo que utilizan SpamAssassin cuando reciben correos electrónicos enviados por Adobe Campaign. Sin embargo, es posible que los servidores de correo de los proveedores de Internet o de los servidores de correo en línea sigan considerando los mensajes enviados por Adobe Campaign como no deseados.

La implementación de SpamAssassin y sus módulos en Perl requiere servidores de aplicaciones Adobe Campaign equipados con acceso a Internet a través de una conexión HTTP (flujo TCP/80).

## Instalación en un equipo con Windows {#installing-on-a-windows-machine}

Para instalar y configurar SpamAssassin en Windows para habilitar la integración con Adobe Campaign, siga los siguientes pasos:

1. Instalación de SpamAssassin
1. Integración de SpamAssassin en Adobe Campaign

### Instalación de SpamAssassin {#installing-spamassassin}

1. Conéctese a [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html) usando sus credenciales de usuario. Obtenga más información acerca de la distribución de software en [esta página](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=es).
1. Descargue la **Neolane Spam Assassin (instalación de Windows) (2.0)** (neolane_spamassassin.2.0.zip).
1. Copie este archivo en el servidor de Adobe Campaign y, a continuación, descomprímalo.

   >[!NOTE]
   >
   >Puede elegir descomprimir el archivo donde desee, siempre que la ruta esté formada por cualquiera de los siguientes caracteres de expresión regular: **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. La ruta de instalación no debe incluir espacios en blanco.

1. Vaya al archivo en el que ha descomprimido el archivo y haga doble clic en el **run_me.bat** para iniciar el script de instalación.

   Si aparece un Shell de Windows y continúa mostrándose durante unos segundos, espere hasta que la instalación y la actualización hayan finalizado y, a continuación, haga clic en **Entrar**.

   Si el shell de Windows no aparece o no se muestra antes de desaparecer instantáneamente, siga estos pasos y haga doble clic en el **portableShell.bat** para mostrar un Shell de Windows y comprobar que la ruta de acceso del Shell corresponde a la carpeta en la que se encuentra el **spamassassin.zip** se ha descomprimido el archivo. Si no es así, acceda a él con el complemento **cd** comando.

   Entrar **run_me.bat** luego haga clic en **Entrar** para iniciar el proceso de instalación y actualización. La operación devuelve uno de los siguientes valores para indicar el resultado de la actualización.

   * **0**: se ha realizado una actualización.
   * **1**: no hay ninguna actualización nueva disponible.
   * **2**: no hay ninguna actualización nueva disponible.
   * **3**: error de actualización durante la verificación previa.
   * **4** o más: se ha producido un error.

1. Para comprobar que la instalación de SpamAssassin se ha realizado correctamente, utilice la prueba GTUBE (Prueba genérica para correo electrónico masivo no solicitado) con el siguiente procedimiento:

   1. Crear un archivo de texto y guardarlo en **C:\TestSpamMail.txt**.
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

   1. Haga doble clic en **portableShell.bat** para mostrar un Shell de Windows e iniciar el siguiente comando (o &quot;`<root>`&quot; designa la carpeta creada al descomprimir el  **spamassassin.zip** file):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      El contenido de este correo electrónico de prueba déclencheur una puntuación de 1000 puntos por SpamAssassin. Esto significa que se ha detectado como no deseable y que la instalación se ha realizado correctamente y funciona por completo.

### Integración de SpamAssassin en Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. Edite el **`[INSTALL]/conf/serverConf.xml`** archivo. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).
1. Cambie el valor del **spamCheck** elements&#39; **mando** en el **Web** nodo. Para ello, ejecute el siguiente comando:

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >Todas las rutas deben ser absolutas.

   Detener e iniciar **[!UICONTROL Adobe Campaign]** servicio.

1. Para comprobar la integración de SpamAssassin en Adobe Campaign, utilice una prueba GTBUE (Prueba genérica para correo electrónico masivo no solicitado):

   Haga doble clic en **portableshell.bat** archivo. Esto déclencheur la visualización de un shell de Windows. A continuación, ejecute el siguiente comando:

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   El contenido de este correo electrónico de prueba tiene un déclencheur de 1000 puntos asignados por SpamAssassin. Esto significa que se ha detectado como no deseable y que la integración en Adobe Campaign se realizó correctamente y es completamente funcional.

1. Actualizar las reglas de filtrado y puntuación de SpamAssassin

   Para una actualización inicial de las reglas de filtrado y puntuación, comience por **portableShell.bat** y ejecute el siguiente comando:

   ```
   sa-update --no-gpg
   ```

   Para ejecutar una actualización automática de las reglas de filtrado y puntuación, utilice el mismo comando en una tarea programada del sistema:

   ```
   sa-update --no-gpg
   ```

## Instalación en un equipo Linux {#installing-on-a-linux-machine}

### Pasos de instalación en Debian {#installation-steps-in-debian}

* Si es necesario, instale Perl y SpamAssassin con el siguiente comando:

   ```
   apt-get install spamassassin libxml-writer-perl
   ```

* En el **serverConf.xml** archivo (disponible en `/usr/local/[INSTALL]/nl6/conf/`), cambie la **spamCheck** línea como sigue:

   ```
   <spamCheck command="perl
   /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
   ```

### Pasos de instalación en RHEL/CentOS {#installation-steps-in-rhel-centos}

Si es necesario, instale Perl y recupere los paquetes mediante CPAN:

```
cpan Digest::SHA1
cpan HTML::Parser
cpan Net::DNS
cpan Mail::SPF 
cpan XML::LibXML
cpan XML::Writer
cpan Mail::SpamAssassin
```

### Actualización de reglas de filtro {#updating-filter-rules}

Las reglas de filtro se pueden actualizar automáticamente mediante el **sa-update** herramienta. Consulte el sitio web oficial de SpamAssassin [https://spamassassin.apache.org/](https://spamassassin.apache.org/) para obtener más información.

En Debian, las actualizaciones se realizan automáticamente cada día.

Si este no es el caso (por ejemplo, cuando Debian se instala manualmente), cree un script para automatizar las actualizaciones de reglas.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

Insertar este script en **crontab** mediante el siguiente comando:

```
crontab-e
```

### Optimización del rendimiento {#performance-optimization}

Para mejorar el rendimiento en Linux, edite el **/etc/spamassassin/local.cf** y agregue la línea siguiente al final del archivo:

```
dns_available no
```
