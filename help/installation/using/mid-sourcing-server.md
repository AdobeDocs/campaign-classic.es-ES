---
title: Instalación de un servidor de fuentes intermedias en Adobe Campaign Classic
description: Esta sección detalla la instalación y configuración de un servidor de fuentes intermedias en Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 9b891a64-d75e-44d2-8de2-17334e1b8dca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 34ee3d99-4ffb-4279-b994-5ab7abc7cf06
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 25ae29490f8b4c58dad499669f5bccff43de8b7a

---


# Servidor de fuentes intermedias{#mid-sourcing-server}

Esta sección detalla la instalación y configuración de un servidor de fuentes intermedias, así como la implementación de una instancia que permite a terceros enviar mensajes en modo de **intermediación** .

La arquitectura de &quot;fuentes intermedias&quot; se presenta en la implementación [de fuentes](../../installation/using/mid-sourcing-deployment.md)intermedias.

La instalación de un servidor de fuentes intermedias sigue el mismo proceso que la instalación de un servidor de la forma normal (consulte la configuración estándar). Es una instancia independiente con su propia base de datos que puede utilizarse para ejecutar entregas. En pocas palabras, contiene una configuración adicional para permitir que las instancias remotas ejecuten entregas a través de ella en modo de abastecimiento intermedio.

## Pasos para instalar y configurar una instancia {#steps-for-installing-and-configuring-an-instance}

### Requisitos previos para instalar y configurar una instancia {#prerequisites-for-installing-and-configuring-an-instance}

* JDK en el servidor de aplicaciones.
* Acceso a un servidor de bases de datos en el servidor de aplicaciones.
* Servidor de seguridad configurado para abrir puertos HTTP (80) o HTTPS (443) en el servidor de fuentes intermedias.

El siguiente procedimiento detalla una configuración mediante un único servidor de abastecimiento intermedio. También es posible utilizar varios servidores. Del mismo modo, también es posible enviar determinados mensajes (como notificaciones de flujo de trabajo, por ejemplo) desde una configuración interna.

### Instalación y configuración del servidor de aplicaciones para la implementación de fuentes intermedias {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

El procedimiento de instalación es idéntico al de la instancia independiente. Consulte [Instalación y configuración (un solo equipo)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Sin embargo, debe aplicar lo siguiente:

* En el paso **5**, debe deshabilitar los módulos **mta** (envío) y **inMail** (mensajes de correo devuelto). Sin embargo, el módulo **wfserver** (flujo de trabajo) debe permanecer activado.

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="false"/>  
       <wfserver autoStart="true"/>  
       <inMail autoStart="false"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

* Los pasos **6**, **9** y **10** no son necesarios.
* Durante los pasos **12** y **13**, debe indicar el puerto 8080 en la dirección URL de conexión (ya que la consola se comunica directamente con Tomcat, no a través del servidor Web). La dirección URL se convierte en [http://console.campaign.net:8080](http://console.campaign.net). Durante el paso **13**, seleccione el **[!UICONTROL Issue towards Mid-sourcing]** paquete y los que desea instalar.

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >El enrutamiento predeterminado de los envíos técnicos se reemplaza automáticamente por el enrutamiento de correo electrónico a través de Mid-sourcing.

### Instalación y configuración del servidor de fuentes intermedias {#installing-and-configuring-the-mid-sourcing-server}

Desde la consola del cliente, busque el enrutamiento de **correo electrónico mediante la cuenta de abastecimiento** intermedio (en la carpeta **/Administración/Cuentas/** externas). Rellene la **dirección URL del servidor**, la **cuenta**, la **contraseña** y la URL **de la página** de reflejo con la información proporcionada por el proveedor de servidores que aloja el servidor de fuentes intermedias. Compruebe la conexión.

>[!NOTE]
>
>La opción **mid-sourcingEmitter** crea dos flujos de trabajo de **fuentes** intermedias. Se trata de un proceso que se ejecuta de forma predeterminada cada 1 hora y 20 minutos y que recopila información de entrega en el servidor de fuentes intermedias.

## Implementación de un servidor de fuentes intermedias {#deploying-a-mid-sourcing-server}

1. Instalación del servidor de aplicaciones:

   >[!CAUTION]
   >
   >Si instala el servidor de fuentes intermedias y desea instalar módulos adicionales de Adobe Campaign, le recomendamos que utilice el módulo Entrega y no el módulo Campaña.

   Siga el mismo procedimiento que para la implementación estándar, seleccionando solo la **[!UICONTROL Mid-sourcing platform]** opción.

   ![](assets/s_ncs_install_midsourcing01.png)

1. Configuración para recibir en modo de abastecimiento intermedio

   Establezca la contraseña de la cuenta de envío: En la carpeta **/Mid-sourcing/Access Management/Operators/** , la instancia remota utiliza el operador **mid** para envíos en modo de abastecimiento intermedio. Debe establecer una contraseña para este operador y proporcionarla al administrador de la instancia de envío.

   La opción Plataforma **de** fuentes intermedias crea las carpetas predeterminadas para almacenar los envíos y el operador predeterminado que realiza los envíos.

## Multiplexación del servidor de fuentes intermedias {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>La multiplexación solo se admite en entornos locales.

Es posible que varias instancias de envío compartan una instancia de abastecimiento intermedio. Cada una de estas instancias debe asociarse con un operador en la base de datos de fuentes intermedias. Para crear una segunda cuenta en el servidor de abastecimiento intermedio:

1. Cree una carpeta en el **[!UICONTROL Mid-sourcing > Deliveries]** nodo que se asociará con la cuenta de abastecimiento medio predeterminada (por ejemplo: prod).
1. Cree una carpeta en el **[!UICONTROL Mid-sourcing > Deliveries]** nodo con el mismo nombre que la cuenta (por ejemplo: accept_test).

   ![](assets/mid_recette_account.png)

1. En **[!UICONTROL Mid-sourcing > Access Management > Operators]**, cree una cuenta nueva.

   ![](assets/mid_recette_user_create.png)

1. En la **[!UICONTROL Access rights]** ficha, otorgue a este operador los derechos del grupo de envíos **de** Mid-sourcing. Este derecho de acceso está disponible en **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**.

   ![](assets/mid_recette_user_rights.png)

1. Seleccione la **[!UICONTROL Restrict to data in the sub-folders of]** opción y seleccione la carpeta de envíos para restringir este operador a la carpeta de envíos de fuentes intermedias.

   ![](assets/mid_recette_user_restrictions.png)

1. Reinicie el módulo Web con el siguiente comando: **nlserver reinicie web**.

Debe cambiar la configuración del servidor de abastecimiento intermedio en el archivo serverConf.xml. La siguiente línea debe agregarse a la sección &quot;Administración de afinidades con direcciones IP&quot;, bajo la línea existente:

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

El atributo &#39;@name&#39; debe respetar las siguientes reglas:

**&#39;marketing_account_operator_name&#39;.&#39;affinity_name&#39;.&#39;affinity_group&#39;**

&#39;marketing_account_operator_name&#39; se refiere al nombre interno de la cuenta de abastecimiento intermedio declarada en la instancia de abastecimiento intermedio.

&#39;affinity_name&#39; se refiere al nombre arbitrario que se le da a la afinidad. Este nombre debe ser único. Los caracteres autorizados son `[a-z]``[A-Z]``[0-9]`. El objetivo es declarar un grupo de direcciones IP públicas.

&#39;affinity_group&#39; hace referencia a la subafinidad declarada en la asignación de destino utilizada en cada una de las entregas. La última parte, incluyendo el se ignora si no hay subafinidad. Los caracteres autorizados son `[a-z]``[A-Z]``[0-9]`.

Debe detener y luego reiniciar el servidor para que se tenga en cuenta la modificación.

## Configuración del seguimiento en un servidor de fuentes intermedias {#configuring-tracking-on-a-mid-sourcing-server}

**Configuración del servidor de fuentes intermedias**

1. Vaya a &#39;operadores&#39; y seleccione el operador **[!UICONTROL mid]**.
1. En la **[!UICONTROL Frontal servers]** ficha, introduzca los parámetros de conexión del servidor de seguimiento.

   Para crear una instancia de seguimiento, introduzca la dirección URL del servidor de seguimiento, la contraseña de la cuenta interna del servidor de seguimiento y el nombre de la instancia, su contraseña y las máscaras DNS asociadas a ella.

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. Cuando haya introducido los parámetros de conexión, haga clic en **[!UICONTROL Confirm the configuration]**.
1. Si es necesario, especifique la ubicación en la que se almacenarán las imágenes incluidas en los envíos. Para ello, seleccione uno de los modos de publicación de la lista desplegable.

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   Si elige la **[!UICONTROL Tracking server(s)]** opción, las imágenes se copiarán en el servidor de fuentes intermedias.

**Configuración de la plataforma del cliente**

1. Vaya a la cuenta de enrutamiento externo de mid-sourcing.
1. En la **[!UICONTROL Mid-Sourcing]** ficha, especifique los parámetros de conexión del servidor de abastecimiento intermedio.

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. Confirme la configuración haciendo clic en **[!UICONTROL Test the connection]**.
1. Declare la instancia de seguimiento a la que se hace referencia en el servidor de abastecimiento intermedio:

   Haga clic en el vínculo **[!UICONTROL Use this platform as a platform to access the tracking servers]**,

   Especifique el nombre de la instancia de seguimiento y confirme la conexión con el servidor de seguimiento.

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

Si la entrega de mensajes va a ser administrada por varios servidores de fuentes intermedias, seleccione la opción **[!UICONTROL Routing with alternating mid-sourcing accounts]** y especifique los diferentes servidores.

![](assets/s_ncs_install_midsourcing_tracking04.png)

