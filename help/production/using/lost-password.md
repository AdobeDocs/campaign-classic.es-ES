---
product: campaign
title: Contraseña perdida
description: Contraseña perdida
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 8%

---

# Contraseña perdida{#lost-password}



Puede cambiar o recuperar una contraseña perdida.
Hay dos escenarios posibles:

* [Contraseña perdida por un operador de Adobe Campaign](#password-lost-by-campaign-operator)
* [Se ha perdido la contraseña interna](#internal-password-lost) (solo clientes locales)

## Contraseña perdida por un operador de Campaign {#password-lost-by-campaign-operator}

Si un operador de Adobe Campaign pierde su contraseña, puede cambiarla.
Para realizar esto, siga los pasos a continuación:

1. Conéctese mediante un operador con derechos de administrador.
1. Haga clic con el botón derecho en un operador.
1. Seleccione **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. Establezca la nueva contraseña del operador. Se recomienda que el operador cambie su contraseña cuando vuelva a conectarse por primera vez.

## Se ha perdido la contraseña interna {#internal-password-lost}

>[!NOTE]
>
>Esta sección solo se aplica a clientes locales.

Si se pierde la contraseña interna, debe reiniciarla.
Para ello, siga el siguiente procedimiento:

1. Edite el **/usr/local/neolane/nl6/conf/serverConf.xml** archivo.

1. Vaya a la **internalPassword** línea.

   ```
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. Elimine la cadena entre comillas, en este caso: **myPassword**

   Por lo tanto, obtiene la siguiente línea:

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

1. Ahora puede utilizar su nueva contraseña para conectarse a **Internas** en el menú contextual.
