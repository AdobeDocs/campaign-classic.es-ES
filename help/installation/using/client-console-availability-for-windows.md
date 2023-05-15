---
product: campaign
title: Disponibilidad de la consola de cliente para Windows
description: Disponibilidad de la consola de cliente para Windows
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 4%

---

# Disponibilidad de la consola de cliente para Windows{#client-console-availability-for-windows}



Para que los usuarios de Adobe Campaign puedan iniciar sesión en la instancia que ha creado y configurado, deben utilizar la consola del cliente.

## Disponibilidad de la consola del cliente

Cuando el equipo solía iniciar un servidor de aplicaciones de Adobe Campaign (**nlserver web**) recibe conexiones de usuario desde la consola del cliente, puede configurarla para que el programa de configuración del cliente enriquecido de Adobe Campaign esté disponible a través de una interfaz de HTML. Siempre que hay disponible una nueva versión de la consola del cliente, se invita a los usuarios a descargarla al iniciar la consola del cliente.

Para ello, debe:

1. Seleccione el paquete que contiene el programa de instalación de la consola.

   Este archivo se llama `setup-client-7.X.XXXX.exe` para v7 o `setup-client-6.X.XXXX.exe` para la versión 6.1, donde `X` es la subversión de Adobe Campaign y `XXXX` es el número de compilación.

1. Copie y pegue este paquete en la carpeta de instalación de Adobe Campaign (en el servidor de marketing para instalaciones híbridas), en **/datakit/nl/eng/jsp**.
1. Inicie el servidor de Adobe Campaign.

Los usuarios de Campaign pueden descargar el programa de instalación de la consola a través de un explorador web gracias a la siguiente URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Esta página requiere un inicio de sesión y una contraseña definidos en la aplicación.

Obtenga información sobre cómo instalar la consola [en esta sección](../../installation/using/installing-the-client-console.md).

## Proponer a los usuarios finales que actualicen su consola de cliente

Una vez que la consola está disponible en la carpeta del servidor de Campaign, se invita a los usuarios a descargar la última versión de la consola del cliente en una ventana de solicitud dedicada. Adobe recomienda dejar la opción **[!UICONTROL No longer ask this question]** no está seleccionado para asegurarse de que todos los usuarios reciben una alerta cuando hay una nueva versión de la consola disponible.

Si selecciona esta opción y decide no descargar la última versión, ningún otro usuario estará informado de las nuevas versiones disponibles.

Si se seleccionó la opción , puede restablecer esta solicitud. Solo los administradores del sistema que estén cómodos con la edición de Windows Registry deben realizar estos cambios:

1. Abra el Editor del Registro utilizando **regedit** desde el **[!UICONTROL Start > Run]** para abrir el Navegador.
1. Busque el nodo y expórtelo.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Elimine el **confAdvisedUpgrade** y cierre el Editor del Registro.
