---
product: campaign
title: Contraseña perdida
description: Contraseña perdida
feature: Monitoring, Access Management
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
TQID: https://experienceleague.adobe.com/MaAtheK2WnozPDuEO-qPq2l9u-AOGj5aGu2TgKslgLc
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 247
ht-degree: 22%

---

# Contraseña perdida{#lost-password}

>[!NOTE]
>
>Esta página solo se aplica a los operadores que se conectan a Campaign con autenticación nativa.

Puede cambiar o recuperar una contraseña perdida.
Hay dos escenarios posibles:

* [Contraseña perdida por un operador de Adobe Campaign](#password-lost-by-campaign-operator)
* [Se ha perdido la contraseña interna](#internal-password-lost) (solo para clientes locales)

## Contraseña perdida por un operador de Campaign {#password-lost-by-campaign-operator}

Si un operador de Adobe Campaign pierde su contraseña, puede cambiarla.

>[!NOTE]
>
>Este procedimiento solo se aplica a los operadores que se conectan a Campaign con autenticación nativa. Para la autenticación de IMS de Adobe, consulte [esta documentación](https://helpx.adobe.com/ie/manage-account/using/change-or-reset-password.html){target="_blank"}.

Para restablecer una contraseña de Campaign, siga los pasos a continuación:

1. Conectarse mediante un operador con derechos de administrador.
1. Haga clic con el botón derecho en un operador.
1. Seleccione **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. Establezca la nueva contraseña del operador. Se recomienda que el operador cambie su contraseña cuando se vuelva a conectar por primera vez.

## Contraseña interna perdida {#internal-password-lost}

>[!NOTE]
>
>Esta sección solo se aplica a los clientes locales.

Si se pierde la contraseña interna, debe reinicializarla.

Para ello, siga el siguiente procedimiento:

1. Edite el archivo **/usr/local/neolane/nl6/conf/serverConf.xml**.

1. Vaya a la línea **internalPassword**.

   ```xml
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. Elimine la cadena entre comillas, en este caso: `myPassword`. Obtendrá la siguiente línea:

   ```xml
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/>
   ```

1. Guarde los cambios y cierre el archivo.

1. Detener el proceso `nlserver`.

1. Configure la nueva contraseña. Para ello, introduzca los siguientes comandos:

   ```javascript
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. Iniciar el proceso `nlserver`.

1. Ahora puede usar su nueva contraseña para conectarse al modo **Interno**.
