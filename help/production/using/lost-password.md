---
product: campaign
title: Contraseña perdida
description: Contraseña perdida
feature: Monitoring, Access Management
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
badge-v7-prem: label="On-Premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 15%

---

# Contraseña perdida{#lost-password}



Puede cambiar o recuperar una contraseña perdida.
Hay dos escenarios posibles:

* [Contraseña perdida por un operador de Adobe Campaign](#password-lost-by-campaign-operator)
* [Contraseña interna perdida](#internal-password-lost) (solo clientes on-premise)

## Contraseña perdida por un operador de Campaign {#password-lost-by-campaign-operator}

Si un operador de Adobe Campaign pierde su contraseña, puede cambiarla.
Para realizar esto, siga los pasos a continuación:

1. Conectarse mediante un operador con derechos de administrador.
1. Haga clic con el botón derecho en un operador.
1. Seleccionar **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. Establezca la nueva contraseña del operador. Se recomienda que el operador cambie su contraseña cuando se vuelva a conectar por primera vez.

## Contraseña interna perdida {#internal-password-lost}

>[!NOTE]
>
>Esta sección solo se aplica a los clientes locales.

Si se pierde la contraseña interna, debe reinicializarla.
Para ello, siga el siguiente procedimiento:

1. Edite el **/usr/local/neolane/nl6/conf/serverConf.xml** archivo.

1. Vaya a la **internalPassword** línea.

   ```
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. Elimine la cadena entre comillas, en este caso: **myPassword**

   Por lo tanto, se obtiene la siguiente línea:

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

1. Ahora puede usar su nueva contraseña para conectarse en **Interno** modo.
