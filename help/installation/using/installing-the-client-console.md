---
product: campaign
title: Instalación de la consola de cliente
description: Obtenga información sobre cómo instalar la consola de cliente
feature: Installation, Upgrade
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 2%

---

# Instalación y actualización de la consola del cliente de Campaign{#installing-the-client-console}

La consola del cliente de Campaign es un cliente enriquecido que le permite conectarse a sus servidores de aplicaciones de Campaign.

Antes de empezar a instalar la consola de cliente, debe hacer lo siguiente:

* Compruebe la compatibilidad del sistema y las herramientas con Adobe Campaign en la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)
* Obtener la URL del servidor de Campaign
* Obtener sus credenciales de usuario
* Instale el tiempo de ejecución de Microsoft Edge Webview2 en el sistema (desde la versión de compilación de Campaign Classic 7.3). [Más información](#webview)

El proceso de instalación o actualización de la consola del cliente difiere según la implementación de Adobe Campaign Classic.
Consulte los detalles siguientes para comprender qué se necesita para la implementación.

![](assets/do-not-localize/how-to-video.png) Descubra cómo instalar y configurar el cliente de Adobe Campaign en [vídeo](#video)

>[!CAUTION]
>
>* La consola del cliente de Campaign y el servidor de aplicaciones de Campaign deben ejecutar **en la misma versión de producto**. El Adobe también recomienda encarecidamente usar la **misma compilación de producto**. Aprenda a comprobar las versiones de cliente y servidor de Campaign en [esta sección](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).
>
>* El acceso a la carpeta de instalación en la que está instalada la consola debe limitarse únicamente al usuario deseado, lo que garantiza que los permisos de escritura estén restringidos en consecuencia.



## Instalación en tiempo de ejecución de Microsoft Edge Webview2 {#webview}

A partir de la versión de compilación del Campaign Classic 7.3, se requiere la instalación del tiempo de ejecución de Microsoft Edge Webview 2 para cualquier instalación de la consola.

Web View se instala de forma predeterminada como parte del sistema operativo Windows 11. Si no está presente en el sistema, el instalador de la consola de Campaign Classic le pedirá que lo descargue del [sitio web para desarrolladores de Microsoft](http://www.adobe.com/go/acc-ms-webview2-runtime-download_es). Tenga en cuenta que el vínculo de descarga no funciona en el navegador Internet Explorer 11, ya que Microsoft ha dejado de admitir. Asegúrese de utilizar un explorador diferente para acceder al vínculo.

## Adobe Implementaciones alojadas {#hosted-customers}

Como cliente alojado, tiene dos opciones para instalar o actualizar la consola o las consolas de cliente:

1. El Adobe puede implementarse directamente. Una vez actualizada la consola, se solicitará a los usuarios que descarguen la versión más reciente de la consola del cliente en una ventana emergente.

1. Puede descargar en sus consolas de cliente desde [Distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html)

   **Los usuarios necesitarán acceso de administrador para completar la actualización. Si los usuarios no tienen derechos de administrador, un administrador del sistema deberá implementar en todas las consolas de cliente**

## Implementaciones híbridas y locales {#hybrid-onprem-customers}

Para que los usuarios de Adobe Campaign puedan iniciar sesión en la instancia que ha creado y configurado, deben utilizar la consola de cliente.

### Disponibilidad de la consola para los usuarios {#make-console-available}

Cuando el equipo utilizado para iniciar un servidor de aplicaciones de Adobe Campaign (nlserver web) recibe conexiones de usuario desde la consola del cliente, puede configurarlo para que el programa de instalación del cliente enriquecido de Adobe Campaign esté disponible a través de una interfaz de HTML. Siempre que haya una nueva versión de la consola del cliente disponible, se invita a los usuarios a descargarla al iniciar la consola del cliente.

Para ello, debe:

1. Seleccione el paquete que contiene el programa de instalación de la consola.

   Este archivo se denomina setup-client-7.X.XXXX.exe, donde X es la subversión de Adobe Campaign y XXXX es el número de compilación.

1. Copie y pegue este paquete en la carpeta de instalación de Adobe Campaign (en el servidor de marketing para instalaciones híbridas), en /datakit/nl/eng/jsp.

1. Inicie el servidor de Adobe Campaign.


### Ya no se puede hacer esta pregunta

El Adobe recomienda dejar la opción **[!UICONTROL No longer ask this question]** sin seleccionar para asegurarse de que se avisa a todos los usuarios cuando hay una nueva versión de la consola disponible.  Si se selecciona esta opción, no se informará al usuario de las nuevas versiones disponibles.

Si se ha seleccionado **[!UICONTROL No longer ask this question]**, puede restablecer este mensaje. Solo los administradores de sistema que se sientan cómodos con la edición del Registro de Windows deben realizar estos cambios:

1. Abra el Editor del Registro con el comando **regedit** del menú **[!UICONTROL Start > Run]**.

1. Busque el nodo y expándalo.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Elimine la entrada **confAdvisedUpgrade** y cierre el Editor del Registro.

>[!NOTE]
>
>Si está aplicando una consola actualizada a una implementación existente, los usuarios recibirán automáticamente una solicitud para actualizar su consola de cliente. Si va a implementar Campaign por primera vez, los usuarios deberán descargar la consola. Consulte a continuación para obtener más información sobre ambas opciones

### Actualizar la consola para la implementación existente{#update-the-client-console}

Una vez que la consola esté disponible en la carpeta del servidor de Campaign, se solicitará a los usuarios que descarguen la versión más reciente de la consola del cliente en una ventana emergente.

**Los usuarios necesitarán acceso de administrador para completar la actualización. Si los usuarios no tienen derechos de administrador, un administrador del sistema deberá implementar en todas las consolas de cliente**


### Descargar la consola para la nueva implementación{#download-the-client-console}

Los usuarios ahora deben descargar e instalar la consola siguiendo los pasos a continuación:

1. Abra un explorador web y descargue la consola desde la siguiente dirección:

   `https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`.

1. En la ventana de identificación, introduzca su nombre de usuario y contraseña.

   ![](assets/s_ncs_install_setup_download01.png)

   Si es necesario, utilice las credenciales de la cuenta interna definida durante la creación de la instancia.

1. Haga clic en el vínculo **[!UICONTROL Download]** de la página de instalación.
1. Descargue y guarde el archivo de configuración de cliente.
1. Ejecutar el archivo descargado en un equipo en Windows: Se inicia la instalación. La ruta de instalación predeterminada de la consola del cliente es **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, donde &quot;X&quot; es &quot;6&quot; o &quot;7&quot;, según la versión de Adobe Campaign.

### Creación de la conexión: solo usuarios nuevos{#create-the-connection}

Una vez instalada la consola del cliente, siga los pasos a continuación para crear la conexión con el servidor de aplicaciones:

1. Inicie la consola desde el menú de Windows **[!UICONTROL Start]**, en el grupo de programas **Adobe Campaign**.

1. Haga clic en el vínculo en la esquina superior derecha de los campos de credenciales para acceder a la ventana de configuración de la conexión.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Haga clic en **[!UICONTROL Add > Connection]** e introduzca la etiqueta y la dirección URL del servidor de aplicaciones de Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Especifique una conexión con el servidor de aplicaciones de Adobe Campaign mediante una dirección URL. Utilice un DNS o un alias del equipo, o su dirección IP.

   Por ejemplo, puede usar la dirección URL de tipo `https://<machine>.<domain>.com`.

1. Si Adobe IMS está configurado para su organización, marque la opción **[!UICONTROL Connect with an Adobe ID]**

1. Haga clic en **[!UICONTROL Ok]** para guardar la configuración.

Puede añadir tantas conexiones como sea necesario para conectarse a los entornos de prueba, fase y producción, por ejemplo.

>[!NOTE]
>
>El botón **[!UICONTROL Add]** le permite crear **[!UICONTROL folders]** para organizar todas las conexiones. Basta con arrastrar y colocar cada conexión en una carpeta.

### Iniciar sesión en Adobe Campaign

Para iniciar sesión en una instancia existente, siga los pasos a continuación:

1. Inicie la consola desde el menú de Windows **[!UICONTROL Start]**, en el grupo de programas **Adobe Campaign**.

1. Haga clic en el vínculo en la esquina superior derecha de los campos de credenciales para acceder a la ventana de configuración de la conexión.

1. Seleccione la instancia de Campaign en la que debe iniciar sesión.

1. Haga clic **[!UICONTROL Ok]**

1. Escriba sus credenciales de inicio de sesión de usuario y haga clic en **[!UICONTROL Log in]**

>[!NOTE]
>
>Para las versiones de compilación de campaign classic 7.3, la consola del cliente de Adobe Campaign puede solicitar credenciales de proxy dos veces durante la autenticación de proxy. Esto se debe a que Microsoft Edge Webview2 no guarda las credenciales de proxy en el almacén de caché/contraseña a diferencia de Internet Explorer.

**Temas relacionados**

* [Creando una instancia e iniciando sesión](../../installation/using/creating-an-instance-and-logging-on.md).
* [Matriz de compatibilidad](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html)

## Tutorial en vídeo

Este vídeo muestra cómo instalar y configurar el cliente de Adobe Campaign.

>[!VIDEO](https://video.tv.adobe.com/v/38273?quality=12&captions=spa)

Puede encontrar disponibles más vídeos de procedimientos de Campaign Classic [aquí](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=es).
