---
solution: Campaign Classic
product: campaign
title: Disponibilidad de la consola de cliente para Windows
description: Disponibilidad de la consola de cliente para Windows
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: 1b02c3870ddc01705f01ea992e734cf0810e003a
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 4%

---


# Disponibilidad de la consola de cliente para Windows{#client-console-availability-for-windows}

Para que los usuarios de Adobe Campaign puedan iniciar sesión en la instancia que ha creado y configurado, deben utilizar la consola del cliente.

## Disponibilidad de la consola del cliente

Cuando el equipo utilizado para iniciar un servidor de aplicaciones de Adobe Campaign (**nlserver web**) recibe conexiones de usuario desde la consola del cliente, puede configurarlo para que el programa de configuración del cliente enriquecido de Adobe Campaign esté disponible mediante una interfaz HTML. Siempre que hay disponible una nueva versión de la consola del cliente, se invita a los usuarios a descargarla al iniciar la consola del cliente.

Para ello, debe:

1. Seleccione el paquete que contiene el programa de instalación de la consola.

   Este archivo se denomina `setup-client-7.X.XXXX.exe` para v7 o `setup-client-6.X.XXXX.exe` para v6.1, donde `X` es la subversión de Adobe Campaign y `XXXX` es el número de compilación.

1. Copie y pegue este paquete en la carpeta de instalación de Adobe Campaign (en el servidor de marketing para instalaciones híbridas), en **/datakit/nl/eng/jsp**.
1. Inicie el servidor de Adobe Campaign.

Los usuarios de Campaign pueden descargar el programa de instalación de la consola a través de un explorador web gracias a la siguiente URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Esta página requiere un inicio de sesión y una contraseña definidos en la aplicación.

Aprenda a instalar la consola [en esta sección](../../installation/using/installing-the-client-console.md).

## Proponer a los usuarios finales que actualicen su consola de cliente

Una vez que la consola está disponible en la carpeta del servidor de Campaign, se invita a los usuarios a descargar la última versión de la consola del cliente en una ventana de solicitud dedicada. Adobe recomienda dejar la opción **[!UICONTROL No longer ask this question]** sin seleccionar para asegurarse de que todos los usuarios reciban alertas cuando haya una nueva versión de la consola disponible.

Si selecciona esta opción y decide no descargar la última versión, ningún otro usuario estará informado de las nuevas versiones disponibles.

Si se seleccionó la opción , puede restablecer esta solicitud. Solo los administradores del sistema que estén cómodos con la edición de Windows Registry deben realizar estos cambios:

1. Abra el Editor del Registro utilizando el comando **regedit** del menú **[!UICONTROL Start > Run]**.
1. Busque el nodo y expórtelo.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Elimine la entrada **confAdvisedUpgrade** y cierre el Editor del Registro.

