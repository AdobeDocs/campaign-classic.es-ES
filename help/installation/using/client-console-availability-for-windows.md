---
product: campaign
title: Disponibilidad de la consola de cliente para Windows
description: Disponibilidad de la consola de cliente para Windows
feature: Installation, Upgrade
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
TQID: 'https://experienceleague.adobe.com/9FqLCew1PO-oxl2hBlK1-4L3SG7tVp28x8GUAPkK6gI'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: eff19c99-440a-4318-b319-444edc4d8d8f
    internal-label: Upgrade
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 9%
---
# Disponibilidad de la consola de cliente para Windows{#client-console-availability-for-windows}



Para que los usuarios de Adobe Campaign puedan iniciar sesión en la instancia que ha creado y configurado, deben utilizar la consola de cliente.

## Hacer que la consola de cliente esté disponible

Cuando el equipo utilizado para iniciar un servidor de aplicaciones de Adobe Campaign (**nlserver web**) reciba conexiones de usuario desde la consola del cliente, puede configurarlo para que el programa de instalación del cliente enriquecido de Adobe Campaign esté disponible a través de una interfaz de HTML. Siempre que haya una nueva versión de la consola del cliente disponible, se invita a los usuarios a descargarla al iniciar la consola del cliente.

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

Aprenda a instalar la consola [en esta sección](../../installation/using/installing-the-client-console.md).

## Proponer a los usuarios finales que actualicen su consola de cliente

Una vez que la consola esté disponible en la carpeta del servidor de Campaign, se invita a los usuarios a descargar la última versión de la consola del cliente en una ventana de solicitud dedicada. Adobe recomienda dejar la opción **[!UICONTROL No longer ask this question]** sin seleccionar para asegurarse de que se avisa a todos los usuarios cuando hay una nueva versión de la consola disponible.

Si selecciona esta opción y decide no descargar la versión más reciente, no se informará a ningún otro usuario de las nuevas versiones disponibles.

Si la opción se seleccionó, puede restablecer este mensaje. Solo los administradores de sistema que se sientan cómodos con la edición del Registro de Windows deben realizar estos cambios:

1. Abra el Editor del Registro con el comando **regedit** del menú **[!UICONTROL Start > Run]**.
1. Busque el nodo y expándalo.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Elimine la entrada **confAdvisedUpgrade** y cierre el Editor del Registro.
