---
product: campaign
title: Instalación de la consola del cliente
description: Obtenga información sobre cómo instalar la consola del cliente
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: 7f24c8be599d6dece41de848d64feb8079b10ff3
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 5%

---

# Instalación y actualización de la consola del cliente de Campaign{#installing-the-client-console}

![](../../assets/v7-only.svg)

La consola del cliente de Campaign es un cliente enriquecido que le permite conectarse a sus servidores de aplicaciones de Campaign.

Antes de comenzar a instalar la consola de cliente, debe:

* Compruebe la compatibilidad del sistema y las herramientas con Adobe Campaign en la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)
* Obtener la URL del servidor de Campaign
* Obtención de credenciales de usuario
* Tener instalado el tiempo de ejecución de Microsoft Edge Webview2 en el sistema (desde la versión de compilación de Campaign Classic 7.3). [Más información](#webview)

El proceso para instalar o actualizar la consola del cliente varía según la implementación de Adobe Campaign Classic.
Consulte los detalles a continuación para comprender qué es lo que se requiere para la implementación.

![](assets/do-not-localize/how-to-video.png) Descubra cómo instalar y configurar el cliente de Adobe Campaign en [video](#video)

>[!CAUTION]
>
>La consola del cliente de Campaign y el servidor de aplicaciones de Campaign deben ejecutarse **en la misma versión del producto**. El Adobe también recomienda encarecidamente utilizar la variable **misma compilación de producto**. Obtenga información sobre cómo comprobar las versiones de cliente y servidor de Campaign en [esta sección](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Instalación del tiempo de ejecución de Microsoft Edge Webview2 {#webview}

A partir de la versión de compilación de Campaign Classic 7.3, se requiere la instalación del tiempo de ejecución de Microsoft Edge Webview 2 para cualquier instalación de consola.

La vista web se instala de forma predeterminada como parte del sistema operativo Windows 11. Si aún no está presente en su sistema, el instalador de la consola de Campaign Classic le pedirá que lo descargue desde [Sitio web del desarrollador de Microsoft](http://www.adobe.com/go/acc-ms-webview2-runtime-download). Tenga en cuenta que el vínculo de descarga no funciona en el explorador Internet Explorer 11, ya que Microsoft ha dejado de ofrecer soporte técnico. Asegúrese de utilizar un explorador diferente para acceder al vínculo.

## Adobe Implementaciones alojadas {#hosted-customers}

Como cliente alojado, tiene dos opciones para instalar o actualizar sus consolas de cliente:

1. Adobe puede implementarse directamente. Una vez actualizada la consola, se pedirá a los usuarios que descarguen la última versión de la consola del cliente en una ventana emergente.

1. Puede descargar en las consolas de cliente desde [Distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html)

   **Los usuarios necesitarán acceso de administrador para completar la actualización. Si los usuarios no tienen derechos de administrador, un administrador del sistema deberá implementar en todas las consolas de cliente**

## Implementaciones híbridas y locales {#hybrid-onprem-customers}

Para que los usuarios de Adobe Campaign puedan iniciar sesión en la instancia que ha creado y configurado, deben utilizar la consola del cliente.

### Disponibilidad de la consola para los usuarios {#make-console-available}

Cuando el equipo utilizado para iniciar un servidor de aplicaciones de Adobe Campaign (nlserver web) recibe conexiones de usuario desde la consola del cliente, puede configurarlo para que el programa de configuración del cliente enriquecido de Adobe Campaign esté disponible mediante una interfaz de HTML. Siempre que hay disponible una nueva versión de la consola del cliente, se invita a los usuarios a descargarla al iniciar la consola del cliente.

Para ello, debe:

1. Seleccione el paquete que contiene el programa de instalación de la consola.

   Este archivo se denomina setup-client-7.X.XXXX.exe para v7 o setup-client-6.X.XXXX.exe para v6.1, donde X es la subversión de Adobe Campaign y XXXX es el número de compilación.

1. Copie y pegue este paquete en la carpeta de instalación de Adobe Campaign (en el servidor de marketing para instalaciones híbridas), en /datakit/nl/eng/jsp.

1. Inicie el servidor de Adobe Campaign.


### Ya no se puede hacer esta pregunta

Adobe recomienda dejar la opción **[!UICONTROL No longer ask this question]** no está seleccionado para asegurarse de que todos los usuarios reciben una alerta cuando hay una nueva versión de la consola disponible.  Si se selecciona esta opción, no se informará al usuario de las nuevas versiones disponibles.

If **[!UICONTROL No longer ask this question]**  se ha seleccionado, puede restablecer esta solicitud. Solo los administradores del sistema que estén cómodos con la edición de Windows Registry deben realizar estos cambios:

1. Abra el Editor del Registro utilizando **regedit** desde el **[!UICONTROL Start > Run]** para abrir el Navegador.

1. Busque el nodo y expórtelo.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Elimine el **confAdvisedUpgrade** y cierre el Editor del Registro.

>[!NOTE]
>
>Si está aplicando una consola actualizada a una implementación existente, los usuarios recibirán automáticamente una solicitud para actualizar su consola de cliente. Si va a implementar Campaign por primera vez, los usuarios deberán descargar la consola. Consulte a continuación los detalles sobre ambas opciones

### Actualizar la consola para una implementación existente{#update-the-client-console}

Una vez que la consola esté disponible en la carpeta del servidor de Campaign, se pedirá a los usuarios que descarguen la última versión de la consola del cliente en una ventana emergente.

**Los usuarios necesitarán acceso de administrador para completar la actualización. Si los usuarios no tienen derechos de administrador, un administrador del sistema deberá implementar en todas las consolas de cliente**


### Descargar la consola para una nueva implementación{#download-the-client-console}

Los usuarios deben descargar e instalar la consola siguiendo los pasos a continuación:

1. Abra un explorador web y descargue la consola desde la siguiente dirección:

   `https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`.

1. En la ventana de identificación, introduzca su nombre de usuario y contraseña.

   ![](assets/s_ncs_install_setup_download01.png)

   Si es necesario, utilice las credenciales de la cuenta interna definida durante la creación de la instancia.

1. Haga clic en el **[!UICONTROL Download]** en la página de instalación.
1. Descargue y guarde el archivo de configuración del cliente.
1. Ejecute el archivo descargado en un equipo en Windows: Se inicia la instalación. La ruta de instalación predeterminada de la consola del cliente es **$PROGRAMFILES$/Adobe/Cliente Adobe Campaign Classic vX**, donde &quot;X&quot; es &quot;6&quot; o &quot;7&quot;, según su versión de Adobe Campaign.

### Crear la conexión: solo usuarios nuevos{#create-the-connection}

Una vez instalada la consola del cliente, siga los pasos a continuación para crear la conexión con el servidor de aplicaciones:

1. Iniciar la consola desde Windows **[!UICONTROL Start]** en el **Adobe Campaign** grupo de programas.

1. Haga clic en el vínculo en la esquina superior derecha de los campos de credenciales para acceder a la ventana de configuración de conexión.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Haga clic en **[!UICONTROL Add > Connection]** e introduzca la etiqueta y la URL del servidor de aplicaciones de Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Especifique una conexión con el servidor de aplicaciones de Adobe Campaign a través de una URL. Utilice un DNS o un alias del equipo o su dirección IP.

   Por ejemplo, puede usar la variable [`https://<machine>.<domain>.com`](https://myserver.adobe.com) escriba URL.

1. Si Adobe IMS está configurado para su organización, marque la opción **[!UICONTROL Connect with an Adobe ID]**

1. Haga clic en **[!UICONTROL Ok]** para guardar la configuración.

Puede agregar tantas conexiones como sea necesario para conectarse a los entornos de prueba, fase y producción, por ejemplo.

>[!NOTE]
>
>El botón **[!UICONTROL Add]** permite crear **[!UICONTROL folders]** para organizar todas las conexiones. Basta con arrastrar y colocar cada conexión en una carpeta.

### Iniciar sesión en Adobe Campaign

Para iniciar sesión en una instancia existente, siga los pasos a continuación:

1. Iniciar la consola desde Windows **[!UICONTROL Start]** en el **Adobe Campaign** grupo de programas.

1. Haga clic en el vínculo en la esquina superior derecha de los campos de credenciales para acceder a la ventana de configuración de conexión.

1. Seleccione la instancia de Campaign a la que debe iniciar sesión.

1. Haga clic en **[!UICONTROL Ok]**

1. Introduzca sus credenciales de inicio de sesión de usuario y haga clic en **[!UICONTROL Log in]**

>[!NOTE]
>
>Para las versiones de compilación de campaign classic 7.3, la consola del cliente de Adobe Campaign puede solicitar credenciales de proxy dos veces durante la autenticación de proxy. Esto se debe a que Microsoft Edge Webview2 no guarda las credenciales de proxy en el almacén de caché/contraseña a diferencia de Internet Explorer.

**Temas relacionados**

* [Creación de una instancia e inicio de sesión](../../installation/using/creating-an-instance-and-logging-on.md).
* [Matriz de compatibilidad](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html)

## Tutorial en vídeo

Este vídeo muestra cómo instalar y configurar el cliente de Adobe Campaign.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

Puede encontrar disponibles más vídeos de procedimientos de Campaign Classic [aquí](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=es).
