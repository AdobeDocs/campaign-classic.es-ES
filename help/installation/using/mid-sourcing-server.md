---
product: campaign
title: Instalación de un servidor intermediario en Campaign
description: Esta sección detalla la instalación y configuración de un servidor de mid-sourcing en Campaign
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 3e55d7f5-2858-4390-bba9-8fb5be0c3d98
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 1%

---

# Servidor intermediario{#mid-sourcing-server}

Esta sección detalla la instalación y configuración de un servidor intermediario, así como la implementación de una instancia que permite a terceros enviar mensajes en modo **mid-sourcing**.

La arquitectura &quot;intermediaria&quot; se presenta en [Implementación intermediaria](../../installation/using/mid-sourcing-deployment.md).

La instalación de un servidor intermediario sigue el mismo proceso que la instalación de un servidor de forma normal (consulte la configuración estándar). Es una instancia independiente con su propia base de datos que puede utilizarse para ejecutar envíos. En pocas palabras, contiene una configuración adicional para permitir que las instancias remotas ejecuten las entregas a través de ella en modo de intermediario.

>[!CAUTION]
>
>Una vez configurado el servidor intermediario y que los [flujos de trabajo de sincronización](../../workflow/using/about-technical-workflows.md) se hayan ejecutado por primera vez, asegúrese de no actualizar el nombre interno de las cuentas externas intermediarias.

## Pasos para instalar y configurar una instancia {#steps-for-installing-and-configuring-an-instance}

### Requisitos previos para instalar y configurar una instancia {#prerequisites-for-installing-and-configuring-an-instance}

* JDK en el servidor de aplicaciones.
* Acceso a un servidor de base de datos en el servidor de aplicaciones.
* Cortafuegos configurado para abrir puertos HTTP (80) o HTTPS (443) en el servidor intermediario.

El siguiente procedimiento detalla una configuración utilizando un solo servidor intermediario. También es posible utilizar varios servidores. Del mismo modo, también es posible enviar ciertos mensajes (como notificaciones de flujo de trabajo, por ejemplo) desde una configuración interna.

### Instalación y configuración del servidor de aplicaciones para la implementación intermediaria {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

El procedimiento de instalación es idéntico al de la instancia independiente. Consulte [Instalación y configuración (un solo equipo)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Sin embargo, debe aplicar lo siguiente:

* En el paso **5**, debe deshabilitar los módulos **mta** (envío) y **inMail** (correos rechazados). Sin embargo, el módulo **wfserver** (flujo de trabajo) debe permanecer activado.

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

   Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#enabling-processes).

* Los pasos **6**, **9** y **10** no son necesarios.
* Durante los pasos **12** y **13**, debe indicar el puerto 8080 en la dirección URL de conexión (ya que la consola se comunica con Tomcat directamente, no a través del servidor web). La dirección URL se convierte en [http://console.campaign.net:8080](http://console.campaign.net). Durante el paso **13**, seleccione el paquete **[!UICONTROL Issue towards Mid-sourcing]**, así como los que desea instalar.

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >El enrutamiento predeterminado de los envíos técnicos se reemplaza automáticamente con el enrutamiento de correo electrónico a través de intermediarios.

### Instalación y configuración del servidor intermediario {#installing-and-configuring-the-mid-sourcing-server}

Desde la consola del cliente, busque el **Email routing using mid-sourcing** mid-sourcing account (en la carpeta **/Administration/External accounts/**). Rellene las configuraciones **URL del servidor**, **cuenta**, **contraseña** y **URL de página espejo** con la información proporcionada por el proveedor de servidor que aloja el servidor de mid-sourcing. Pruebe la conexión.

>[!NOTE]
>
>La opción **mid-sourcingEmitter** crea dos flujos de trabajo **Mid-sourcing**. Se trata de un proceso que se ejecuta de forma predeterminada cada 1 hora y 20 minutos y que recopila información de entrega en el servidor intermediario.

## Implementación de un servidor intermediario {#deploying-a-mid-sourcing-server}

1. Instalación del servidor de aplicaciones:

   >[!CAUTION]
   >
   >Si instala el servidor de mid-sourcing y desea instalar módulos adicionales de Adobe Campaign, recomendamos utilizar el módulo Delivery y no el módulo Campaign.

   Siga el mismo procedimiento que para la implementación estándar, seleccionando solo la opción **[!UICONTROL Mid-sourcing platform]** .

   ![](assets/s_ncs_install_midsourcing01.png)

1. Configuración para recibir en modo intermediario

   Establezca la contraseña de la cuenta de envío: En la carpeta **/Mid-sourcing/Access Management/Operators/**, la instancia remota utiliza el operador **mid** para los envíos en modo intermediario. Debe establecer una contraseña para este operador y proporcionarla al administrador de la instancia de envío.

   La opción **Mid-sourcing platform** crea las carpetas predeterminadas para almacenar los envíos enviados y el operador predeterminado que realiza los envíos.

## Multiplexación del servidor de mid-sourcing {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>La multiplexación solo es compatible con entornos locales.

Es posible que varias instancias de envío compartan una instancia de mid-sourcing. Cada una de estas instancias debe estar asociada a un operador en la base de datos intermediaria. Para crear una segunda cuenta en el servidor de mid-sourcing:

1. Cree una carpeta en el nodo **[!UICONTROL Mid-sourcing > Deliveries]** que se asociará con la cuenta de mid-sourcing predeterminada (por ejemplo: prod).
1. Cree una carpeta en el nodo **[!UICONTROL Mid-sourcing > Deliveries]** con el mismo nombre que la cuenta (por ejemplo: accept_test).

   ![](assets/mid_recette_account.png)

1. En **[!UICONTROL Mid-sourcing > Access Management > Operators]**, cree una nueva cuenta.

   ![](assets/mid_recette_user_create.png)

1. En la pestaña **[!UICONTROL Access rights]**, otorgue a este operador los derechos del grupo **Mid-sourcing deliveries**. Este derecho de acceso está disponible en **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**.

   ![](assets/mid_recette_user_rights.png)

1. Seleccione la opción **[!UICONTROL Restrict to data in the sub-folders of]** y seleccione la carpeta de envíos para restringir este operador a la carpeta de envíos intermediarios.

   ![](assets/mid_recette_user_restrictions.png)

1. Reinicie el módulo web con el siguiente comando: **nlserver reinicie web**.

Debe cambiar la configuración del servidor intermediario en el archivo serverConf.xml. La línea siguiente debe agregarse a la sección &quot;Administración de afinidades con direcciones IP&quot;, en la línea existente:

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

El atributo &#39;@name&#39; debe respetar las siguientes reglas:

**&#39;marketing_account_operator_name&#39;.&#39;afinity_name&#39;.&#39;affinity_group&#39;**

&#39;marketing_account_operator_name&#39; se refiere al nombre interno de la cuenta de mid-sourcing declarada en la instancia de mid-sourcing.

&#39;affinity_name&#39; se refiere al nombre arbitrario que se le dio a la afinidad. Este nombre debe ser único. Los caracteres autorizados son `[a-z]``[A-Z]``[0-9]`. El objetivo es declarar un grupo de direcciones IP públicas.

&#39;affinity_group&#39; hace referencia a la subafinidad declarada en la asignación de destino utilizada en cada una de las entregas. La última parte que incluye el se ignora si no hay subafinidad. Los caracteres autorizados son `[a-z]``[A-Z]``[0-9]`.

Debe detener y luego reiniciar el servidor para que se tenga en cuenta la modificación.

## Configuración del seguimiento en un servidor intermediario {#configuring-tracking-on-a-mid-sourcing-server}

**Configuración del servidor intermediario**

1. Vaya a &quot;operadores&quot; y seleccione el operador **[!UICONTROL mid]**.
1. En la pestaña **[!UICONTROL Frontal servers]**, introduzca los parámetros de conexión del servidor de seguimiento.

   Para crear una instancia de seguimiento, introduzca la URL del servidor de seguimiento, la contraseña de la cuenta interna del servidor de seguimiento y el nombre de la instancia, su contraseña y las máscaras DNS asociadas a ella.

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. Cuando haya introducido los parámetros de conexión, haga clic en **[!UICONTROL Confirm the configuration]**.
1. Si es necesario, especifique la ubicación en la que se deben almacenar las imágenes incluidas en los envíos. Para ello, seleccione uno de los modos de publicación de la lista desplegable.

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   Si elige la opción **[!UICONTROL Tracking server(s)]** , las imágenes se copiarán en el servidor intermediario.

**Configuración de la plataforma del cliente**

1. Vaya a la cuenta de enrutamiento intermediario externa.
1. En la pestaña **[!UICONTROL Mid-Sourcing]**, especifique los parámetros de conexión del servidor de mid-sourcing.

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. Confirme la configuración haciendo clic en **[!UICONTROL Test the connection]**.
1. Declare la instancia de seguimiento a la que se hace referencia en el servidor intermediario:

   Haga clic en el enlace **[!UICONTROL Use this platform as a proxy to access the tracking servers]**,

   Especifique el nombre de la instancia de seguimiento y, a continuación, confirme la conexión con el servidor de seguimiento.

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

Si varios servidores intermediarios van a administrar el envío de mensajes, seleccione la opción **[!UICONTROL Routing with alternating mid-sourcing accounts]** y especifique los diferentes servidores.

![](assets/s_ncs_install_midsourcing_tracking04.png)
