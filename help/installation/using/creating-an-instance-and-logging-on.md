---
product: campaign
title: Creación de una instancia e inicio de sesión
description: Creación de una instancia e inicio de sesión
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 0db6f107d2c161b07f42dcf7a932d319130b31e0
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 9%

---

# Creación de una instancia e inicio de sesión{#creating-an-instance-and-logging-on}



Para crear una nueva instancia y una base de datos de Adobe Campaign, siga el siguiente proceso:

1. Cree la conexión.
1. Inicie sesión para crear la instancia relacionada.
1. Crear y configurar la base de datos.

>[!NOTE]
>
>Solo el identificador **internal** puede llevar a cabo estas operaciones. Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#internal-identifier).

Cuando se inicia la consola de Adobe Campaign, se accede a una página de inicio de sesión.

Para crear una nueva instancia, siga los pasos a continuación:

1. Haga clic en el vínculo en la esquina superior derecha de los campos de credenciales para acceder a la ventana de configuración de la conexión. Este vínculo puede ser **[!UICONTROL New...]** o un nombre de instancia existente.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Haga clic en **[!UICONTROL Add > Connection]** e introduzca la etiqueta y la dirección URL del servidor de aplicaciones de Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Especifique una conexión con el servidor de aplicaciones de Adobe Campaign mediante una dirección URL. Utilice un DNS o un alias del equipo, o su dirección IP.

   Por ejemplo, puede usar la dirección URL de tipo `https://<machine>.<domain>.com`.

   >[!CAUTION]
   >
   >Para la dirección URL de conexión, use solamente los siguientes caracteres: `[a-z]`, `[A-Z]`, `[0-9]` y guiones (-) o paradas completas.

1. Haga clic en **[!UICONTROL Ok]** para confirmar la configuración: ahora puede comenzar con el proceso de creación de instancias.
1. En la ventana **[!UICONTROL Connection settings]**, introduzca el inicio de sesión **interno** y su contraseña para conectarse al servidor de aplicaciones de Adobe Campaign. Una vez conectado, acceda al asistente de creación de instancias para declarar una instancia nueva
1. En el campo **[!UICONTROL Name]**, escriba el **nombre de instancia**. Dado que este nombre se usa para generar un archivo de configuración **config-`<instance>`.xml** y se usa en los parámetros de la línea de comandos para identificar la instancia, asegúrese de elegir un nombre corto sin caracteres especiales. Por ejemplo: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   El nombre de la instancia agregada al nombre de dominio no debe superar los 40 caracteres. Esto le permite restringir el tamaño de los encabezados &quot;Message-ID&quot; y evita que los mensajes se consideren como correo no deseado, especialmente por herramientas como SpamAssassin.

1. En los campos **[!UICONTROL DNS masks]**, escriba la **lista de máscaras DNS** a las que se debe adjuntar la instancia. El servidor de Adobe Campaign utiliza el nombre de host que aparece en las solicitudes HTTP para determinar a qué instancia acceder.

   El nombre de host se encuentra entre la cadena **https://** y el primer carácter de barra diagonal **/** de la dirección del servidor.

   Puede definir una lista de valores separados por comas.

   ¿El? y &#42; caracteres se pueden usar como comodines para reemplazar uno o varios caracteres (DNS, puerto, etc.). Por ejemplo, el valor **demo&#42;** funcionará con &quot;https://demo&quot; como lo hará con &quot;https://demo:8080&quot; e incluso &quot;https://demo2&quot;.

   Los nombres utilizados deben definirse en su DNS. También puede informar la correspondencia entre un nombre DNS y una dirección IP en el archivo **c:/windows/system32/drivers/etc/hosts** en Windows y en el archivo **/etc/hosts** en Linux. Por lo tanto, debe modificar la configuración de conexión para utilizar este nombre DNS para conectarse a la instancia elegida.

   El servidor debe identificarse con este nombre, especialmente para cargar imágenes en correos electrónicos.

   Además, el servidor debe poder conectarse a sí mismo con este nombre y, si es posible, con una dirección de bucle invertido - 127.0.0.1 -, en particular para permitir que los informes se exporten en formato PDF.

1. En la lista desplegable **[!UICONTROL Language]**, seleccione **idioma de instancia**: inglés (EE.UU.), inglés (Reino Unido), francés o japonés.

   Las diferencias entre el inglés de EE. UU. y el inglés de Reino Unido se describen en la [documentación de Campaign v8 (consola)](.https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-ui).

   >[!CAUTION]
   >
   >No se puede modificar el idioma de la instancia después de este paso. Las instancias de Adobe Campaign no son multilingües: no puede cambiar la interfaz de un idioma a otro.

1. Haga clic en **[!UICONTROL Ok]** para confirmar la declaración de la instancia. Cierre la sesión y vuelva a iniciarla para declarar la base de datos.

   >[!NOTE]
   >
   >La instancia se puede crear desde la línea de comandos. Para obtener más información, consulte [Líneas de comandos](../../installation/using/command-lines.md).
