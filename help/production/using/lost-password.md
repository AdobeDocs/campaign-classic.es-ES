---
title: Contraseña perdida
seo-title: Contraseña perdida
description: Contraseña perdida
seo-description: null
page-status-flag: never-activated
uuid: caac68bf-abdc-45da-9697-b689ebd37002
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: d52eeadc-19c6-4d48-995a-1c1f2ca3b5ec
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 12%

---


# Contraseña perdida{#lost-password}

Puede cambiar o recuperar una contraseña perdida.

Existen dos escenarios posibles:

* Contraseña perdida por un operador de Adobe Campaign.

   En este caso, puede cambiar la contraseña del operador en cuestión. Para ello, conecte mediante un operador con derechos de administrador, haga clic con el botón derecho en un operador, seleccione **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** y defina la nueva contraseña del operador. Recomendamos que los operadores cambien su contraseña cuando vuelvan a conectarse por primera vez.

   ![](assets/operator-passwd.png)

* **Pérdida interna** de contraseñas (solo clientes locales).

   Si se pierde la contraseña **interna** , debe reinicializarla. Para ello, siga el procedimiento siguiente:

   1. Edite el archivo **/usr/local/neolane/nl6/conf/serverConf.xml** .
   1. Vaya a la línea **internalPassword** .

      ```
      <!-- XTK authentication mode internalPassword : Password of internal account -->
       <xtk internalPassword="myPassword"/>
      ```

   1. Elimine la cadena entre comillas, en este caso: **myPassword**

      De este modo, obtiene la siguiente línea:

      ```
      !-- XTK authentication mode internalPassword : Password of internal account -->
      <xtk internalPassword=""/
      ```

   1. Guarde los cambios y cierre el archivo.
   1. Configure la nueva contraseña. Para ello, introduzca los siguientes comandos:

      ```
      nlserver config -internalpassword
      HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
      Enter current password.
      Password: (empty)
      Enter the new password.
      Password: 
      Confirmation 
      ```

   1. Ahora puede utilizar su nueva contraseña para conectarse en modo **interno** .

