---
solution: Campaign Classic
product: campaign
title: Contraseña perdida
description: Contraseña perdida
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: f24642223a2ec9f3d8e78e2f7e71a55bf14b80c7
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 9%

---


# Contraseña perdida{#lost-password}

Puede cambiar o recuperar una contraseña perdida.
Existen dos escenarios posibles:

**Contraseña perdida por un operador de Adobe Campaign**

En este caso, puede cambiar la contraseña del operador en cuestión.
Para realizar esto, siga los pasos a continuación:

1. Conéctese mediante un operador con derechos de administrador.
1. Haga clic con el botón derecho en un operador.
1. Seleccione **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. Establezca la nueva contraseña del operador. Se recomienda que los operadores cambien su contraseña la primera vez que se vuelvan a conectar.

**Pérdida interna de contraseña (solo clientes locales)**

Si se pierde la contraseña interna, debe reinicializarla.
Para ello, siga el procedimiento siguiente:

1. Edite el archivo **/usr/local/neolane/nl6/conf/serverConf.xml**.

1. Vaya a la línea **internalPassword**.

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

1. Ahora puede utilizar su nueva contraseña para conectarse en modo **Interno**.
