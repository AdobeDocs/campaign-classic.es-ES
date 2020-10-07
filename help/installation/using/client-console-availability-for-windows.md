---
title: Disponibilidad de la consola de cliente para Windows
seo-title: Disponibilidad de la consola de cliente para Windows
description: Disponibilidad de la consola de cliente para Windows
seo-description: null
page-status-flag: never-activated
uuid: d1cbb34e-87e0-481b-a78b-3616047eb5cb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: 4fa2e8c1-33d1-4d14-941b-ca528b8ceabb
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 6%

---


# Disponibilidad de la consola de cliente para Windows{#client-console-availability-for-windows}

Para que los usuarios de Adobe Campaign puedan iniciar sesión en la instancia creada y configurada, deben utilizar la consola de cliente.

Cuando el equipo utilizado para el inicio de un servidor de aplicaciones de Adobe Campaign (**nlserver web**) recibe conexiones de usuario desde la consola del cliente, puede configurarlo para que el programa de configuración del cliente enriquecido de Adobe Campaign esté disponible mediante una interfaz HTML.

Para ello, debe:

1. Recupere el paquete que contiene el programa de instalación de la consola.

   Este archivo se llama `setup-client-7.X.XXXX.exe` para v7 o `setup-client-6.X.XXXX.exe` para v6.1, donde `X` es la subversión de Adobe Campaign y `XXXX` es el número de compilación.

1. Copie y pegue este paquete en la carpeta de instalación de Adobe Campaign, en **/datakit/nl/eng/jsp**.
1. Inicio del servidor Adobe Campaign.

Los usuarios finales pueden descargar el programa de instalación de la consola a través de un explorador Web gracias a la siguiente URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Esta página requiere un inicio de sesión y una contraseña definidos en la aplicación.

Para descargar e instalar la consola, consulte [Instalación de la consola](../../installation/using/installing-the-client-console.md)cliente.

Siempre que haya disponible una nueva versión de la consola de cliente, se le pedirá que la descargue.

>[!NOTE]
>
>En el mensaje que se muestra, Adobe recomienda dejar la opción **[!UICONTROL No longer ask this question]** sin seleccionar para asegurarse de que todos los usuarios reciban una alerta cuando haya una nueva versión de la consola disponible.\
>Si selecciona esta opción y decide no descargar la última versión, ningún otro usuario estará informado de las nuevas versiones disponibles.

Para restablecer este mensaje, siga los pasos a continuación (solo los administradores del sistema que se sientan cómodos con la edición del Registro deben realizar estos cambios):

1. Abra el Editor del Registro con el comando **regedit** del **[!UICONTROL Start > Run]** menú.
1. Busque el nodo y expórtelo.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Elimine la entrada **confAdvisedUpgrade** y cierre el Editor del Registro.

