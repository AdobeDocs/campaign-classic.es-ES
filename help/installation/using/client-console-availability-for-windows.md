---
product: campaign
title: Disponibilidad de la consola de cliente para Windows
description: Disponibilidad de la consola de cliente para Windows
feature: Installation, Upgrade
badge-v7-prem: label="Solo local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 6%

---

# Disponibilidad de la consola de cliente para Windows{#client-console-availability-for-windows}



Para que los usuarios de Adobe Campaign puedan iniciar sesión en la instancia que ha creado y configurado, deben utilizar la consola de cliente.

## Hacer que la consola de cliente esté disponible

Cuando el equipo utilizado para iniciar un servidor de aplicaciones de Adobe Campaign (**nlserver web**) recibe conexiones de usuario desde la consola del cliente, puede configurarlas para que el programa de instalación del cliente enriquecido de Adobe Campaign esté disponible a través de una interfaz de HTML. Siempre que haya una nueva versión de la consola del cliente disponible, se invita a los usuarios a descargarla al iniciar la consola del cliente.

Para ello, debe:

1. Seleccione el paquete que contiene el programa de instalación de la consola.

   Este archivo se llama `setup-client-7.X.XXXX.exe`, donde `X` es la subversión de Adobe Campaign y `XXXX` es el número de compilación.

1. Copie y pegue este paquete en la carpeta de instalación de Adobe Campaign (en el servidor de marketing para instalaciones híbridas), en **/datakit/nl/eng/jsp**.
1. Inicie el servidor de Adobe Campaign.

Los usuarios de Campaign pueden descargar el programa de instalación de la consola a través de un explorador web gracias a la siguiente URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Esta página requiere un inicio de sesión y una contraseña definidos en la aplicación.

Obtenga información sobre cómo instalar la consola [en esta sección](../../installation/using/installing-the-client-console.md).

## Proponer a los usuarios finales que actualicen su consola de cliente

Una vez que la consola esté disponible en la carpeta del servidor de Campaign, se invita a los usuarios a descargar la última versión de la consola del cliente en una ventana de solicitud dedicada. El Adobe recomienda dejar la opción **[!UICONTROL No longer ask this question]** deseleccionada para asegurarse de que todos los usuarios reciben una alerta cuando hay una nueva versión de la consola disponible.

Si selecciona esta opción y decide no descargar la versión más reciente, no se informará a ningún otro usuario de las nuevas versiones disponibles.

Si la opción se seleccionó, puede restablecer este mensaje. Solo los administradores de sistema que se sientan cómodos con la edición del Registro de Windows deben realizar estos cambios:

1. Abra el Editor del Registro con la variable **regedit** desde el **[!UICONTROL Start > Run]** menú.
1. Busque el nodo y expándalo.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Elimine el **confAdvisedUpgrade** y cierre el Editor del Registro.
