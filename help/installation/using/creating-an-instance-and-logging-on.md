---
product: campaign
title: Creación de una instancia e inicio de sesión
description: Creación de una instancia e inicio de sesión
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 1%

---

# Creación de una instancia e inicio de sesión{#creating-an-instance-and-logging-on}



Para crear una nueva instancia y una base de datos de Adobe Campaign, siga el siguiente proceso:

1. Cree la conexión.
1. Inicie sesión para crear los instancia relacionados.
1. Crear y configure la base de datos.

>[!NOTE]
>
>Solo el **identificador interno** puede realizar estas operaciones. Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#internal-identifier).

Cuando se inicia la consola Adobe Campaign, se accede a un inicio de sesión Página.

Para crear una nueva instancia, seguir los pasos siguientes:

1. Haga clic en la vincular situada en la esquina superior derecha de los campos de credenciales para acceder a la ventana de configuración de conexión. Este vínculo puede ser **[!UICONTROL New...]** o un nombre de instancia existente.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Clic **[!UICONTROL Add > Connection]** e introduzca la etiqueta y la dirección URL del servidor de aplicaciones de Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Especifique una conexión con el servidor de aplicaciones de Adobe Campaign mediante una dirección URL. Utilice un DNS o un alias del equipo, o su dirección IP.

   Por ejemplo, puede utilizar la variable `https://<machine>.<domain>.com` escriba la dirección URL.

   >[!CAUTION]
   >
   >Para el URL de conexión, utilice únicamente los siguientes caracteres: `[a-z]`, `[A-Z]`, `[0-9]` y guiones (-) o puntos.

1. Haga clic **[!UICONTROL Ok]** para confirmar la configuración: ahora puede comenzar con el proceso de creación de instancia.
1. En la **[!UICONTROL Connection settings]** ventana, introduzca el **inicio de sesión interno** y su contraseña para conectarse al servidor Adobe Campaign aplicación. Una vez conectado, accede al asistente de creación de instancia para declarar un nuevo instancia
1. En el **[!UICONTROL Name]** campo, introduzca el nombre del **instancia**. Como este nombre se utiliza para generar un archivo **de configuración config-`<instance>`.xml** y se utiliza en los parámetros de línea de comandos para identificar el instancia, asegúrese de elegir un nombre corto sin caracteres especiales. Por ejemplo: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   El nombre del instancia agregado al nombre de dominio no debe exceder los 40 caracteres. Esto le permite restringir el tamaño de los encabezados &quot;Enviar mensaje-ID&quot; y evita que los mensajes sean considerados como spam, particularmente por herramientas como SpamAssassin.

1. En los **[!UICONTROL DNS masks]** campos, introduzca el lista de máscaras DNS a las **** que debe adjuntarse la instancia. El servidor de Adobe Campaign utiliza el nombre de host que aparece en las solicitudes HTTP para determinar a qué instancia acceder.

   El nombre de host se encuentra entre la cadena **https://** y el primer carácter de barra diagonal **/** de la dirección del servidor.

   Puede definir una lista de valores separados por comas.

   ¿El? y &#42; los caracteres se pueden utilizar como comodines para reemplazar uno o varios caracteres (DNS, puerto, etc.). Por instancia, el valor de la **demostración&#42;** funcionará con &quot;https://demo&quot; como lo hará con &quot;https://demo:8080&quot; y igualado con &quot;https://demo2&quot;.

   Los nombres utilizados deben definirse en su DNS. También puede informar la correspondencia entre un nombre DNS y una dirección IP en el **archivo c:/windows/system32/drivers/etc/hosts** en Windows y en el **archivo /etc/hosts** en Linux. Por lo tanto, debe modificar la configuración de conexión para usar este nombre DNS con el fin de conectarse a su instancia elegido.

   El servidor debe identificarse con este nombre, especialmente para cargar imágenes en correos electrónicos.

   Además, el servidor debe poder conectarse a sí mismo con este nombre y, si es posible, mediante una dirección de bucle invertido - 127.0.0.1 -, particularmente para permitir que los informes se exporten en PDF formato.

1. En la **[!UICONTROL Language]** lista desplegable, seleccione el **idioma** instancia: Inglés (EE.UU.), Inglés (Reino Unido), Francés o Japonés.

   Las diferencias entre inglés de EE. UU. e inglés de Reino Unido se describen en [esta sección](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >No se puede modificar el idioma de la instancia después de este paso. Las instancias de Adobe Campaign no son multilingües: no puede cambiar la interfaz de un idioma a otro.

1. Clic **[!UICONTROL Ok]** para confirmar la declaración de la instancia. Cierre la sesión y vuelva a iniciarla para declarar la base de datos.

   >[!NOTE]
   >
   >La instancia se puede crear desde la línea de comandos. Para obtener más información, consulte [Comando líneas](../../installation/using/command-lines.md).
