---
title: Creación de una instancia e inicio de sesión
seo-title: Creación de una instancia e inicio de sesión
description: Creación de una instancia e inicio de sesión
seo-description: null
page-status-flag: never-activated
uuid: cb1620b3-f6e8-41dc-9142-ac0da65b6f8d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: c7395094-c635-45ab-8455-a050f7d16b64
translation-type: tm+mt
source-git-commit: 6d6f63fb6ac99c3a9e58a8670bc9bc59e6cfd420
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 4%

---


# Creación de una instancia e inicio de sesión{#creating-an-instance-and-logging-on}

Para crear una nueva instancia y una base de datos de Adobe Campaign, aplique el siguiente proceso:

1. Cree la conexión.
1. Inicie sesión para crear la instancia relacionada.
1. Cree y configure la base de datos.

>[!NOTE]
>
>Sólo el identificador **interno** puede realizar estas operaciones. For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

Cuando se inicia la consola de Adobe Campaign, se accede a una página de inicio de sesión.

Para crear una nueva instancia, siga los pasos a continuación:

1. Haga clic en el vínculo en la esquina superior derecha de los campos de credenciales para acceder a la ventana de configuración de conexión. Este vínculo puede ser **[!UICONTROL New...]** o un nombre de instancia existente.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Haga clic en **[!UICONTROL Add > Connection]** y escriba la etiqueta y la dirección URL del servidor de aplicaciones de Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Especifique una conexión con el servidor de aplicaciones de Adobe Campaign mediante una URL. Use un DNS o un alias del equipo o su dirección IP.

   Por ejemplo, puede utilizar el [`https://<machine>.<domain>.com`](https://myserver.adobe.com) tipo URL.

   >[!CAUTION]
   >
   >Para la dirección URL de conexión, utilice únicamente los caracteres siguientes: `[a-z]`, `[A-Z]`, `[0-9]` y guiones (-) o paradas completas.

1. Haga clic **[!UICONTROL Ok]** para confirmar la configuración: ahora puede comenzar con el proceso de creación de instancias.
1. En la **[!UICONTROL Connection settings]** ventana, introduzca el inicio de sesión **interno** y su contraseña para conectarse al servidor de aplicaciones de Adobe Campaign. Una vez conectado, se accede al asistente para la creación de instancias para declarar una nueva instancia
1. En el **[!UICONTROL Name]** campo, introduzca el nombre **de la** instancia. Dado que este nombre se utiliza para generar un archivo de configuración **config-`<instance>`.xml** y se utiliza en los parámetros de la línea de comandos para identificar la instancia, asegúrese de elegir un nombre corto sin caracteres especiales. Por ejemplo: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   El nombre de la instancia agregada al nombre de dominio no debe exceder los 40 caracteres. Esto le permite restringir el tamaño de los encabezados &quot;Message-ID&quot; y evita que los mensajes se consideren spam, especialmente por herramientas como SpamAssassin.

1. En los **[!UICONTROL DNS masks]** campos, introduzca la **lista de las máscaras** DNS a las que debe adjuntarse la instancia. El servidor de Adobe Campaign utiliza el nombre de host que aparece en las solicitudes HTTP para determinar la instancia a la que se debe llegar.

   El nombre de host se encuentra entre la cadena **https://** y el primer carácter **/** de barra diagonal de la dirección del servidor.

   Puede definir una lista de valores separados por comas.

   El ? y * los caracteres pueden utilizarse como comodines para reemplazar uno o varios caracteres (DNS, puerto, etc.). Por ejemplo, el valor **demo*** funcionará con &quot;https://demo&quot; como con &quot;https://demo:8080&quot; e incluso con &quot;https://demo2&quot;.

   Los nombres utilizados deben definirse en el DNS. También puede informar la correspondencia entre un nombre DNS y una dirección IP en el archivo **c:/windows/system32/drivers/etc/hosts** en Windows y en el archivo **/etc/hosts** en Linux. Por lo tanto, debe modificar la configuración de conexión para utilizar este nombre DNS a fin de conectarse a la instancia elegida.

   El servidor debe identificarse con este nombre, especialmente para cargar imágenes en correos electrónicos.

   Además, el servidor debe ser capaz de conectarse a sí mismo con este nombre y, si es posible, con una dirección de loopback - 127.0.0.1 -, especialmente para permitir que los informes se exporten en formato PDF.

1. En la **[!UICONTROL Language]** lista desplegable, seleccione el idioma **de la** instancia: Inglés (EE.UU.), inglés (Reino Unido), francés o japonés.

   En [esta sección](../../platform/using/adobe-campaign-workspace.md#date-and-time)se describen las diferencias entre el inglés de EE.UU. y el inglés del Reino Unido.

   >[!CAUTION]
   >
   >El idioma de la instancia no se puede modificar después de este paso. Las instancias de Adobe Campaign no son multilingües: no se puede cambiar la interfaz de un idioma a otro.

1. Haga clic en **[!UICONTROL Ok]** para confirmar la declaración de instancia. Cierre la sesión y vuelva a iniciarla para declarar la base de datos.

   >[!NOTE]
   >
   >La instancia se puede crear desde la línea de comandos. For more on this, refer to [Command lines](../../installation/using/command-lines.md).

