---
title: Migración de usuarios técnicos a la consola de Adobe Developer
description: Obtenga información sobre cómo migrar los operadores técnicos de Campaign a la cuenta técnica en la consola de Adobe Developer
feature: Technote
role: Admin
source-git-commit: 68d1f5ae0089a0c447acf67c28c27f4e1069a218
workflow-type: tm+mt
source-wordcount: '1646'
ht-degree: 0%

---

# Migración de los operadores técnicos de Campaign a la consola de Adobe Developer {#migrate-tech-users-to-ims}

Como parte del esfuerzo por reforzar la seguridad y el proceso de autenticación, a partir de la versión 7.3.5 de Campaign Classic, se está mejorando el proceso de autenticación en Campaign Classic. Los operadores técnicos deben utilizar ahora el [Adobe Identity Management System (IMS)](https://helpx.adobe.com/es/enterprise/using/identity.html){target="_blank"} to connect to Campaign. Learn more about the new server to server authentication process in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}. **Adobe recomienda realizar esta migración en Campaign v7.3.5 para poder migrar sin problemas a Campaign v8.**

Un operador técnico es un perfil de usuario de Campaign que se ha creado explícitamente para la integración de API. Este artículo detalla los pasos necesarios para migrar un operador técnico a una cuenta técnica a través de la consola de Adobe Developer.


## ¿Se ha visto afectado?{#ims-impacts}

Si realiza llamadas de API desde un sistema externo a Campaign a la instancia de Campaign Marketing o a la instancia de Real-Time Message Center, Adobe recomienda migrar los operadores técnicos a cuentas técnicas a través de la consola de Adobe Developer, como se detalla a continuación.

Este cambio es aplicable a partir de la versión 7.3.5 de Campaign Classic y es **obligatorio** para pasar a Adobe Campaign v8.

## Proceso de migración {#ims-migration-procedure}

Siga los siguientes pasos para crear cuentas técnicas en la consola de Adobe Developer y, a continuación, utilice las cuentas recién creadas para poder cambiar los métodos de autenticación de todos los sistemas externos que realizan llamadas de API en Adobe Campaign.

A continuación se ofrece una descripción general de los pasos:

* Creación de un proyecto dentro de la consola de Adobe Developer
* Asignar las API adecuadas al proyecto recién creado
* Concesión de los perfiles de producto de Campaign necesarios al proyecto
* Actualizar las API para utilizar las credenciales de la cuenta técnica recién creada
* Eliminación de los operadores técnicos heredados de la instancia de Campaign

### Requisitos previos para la migración{#ims-migration-prerequisites}

<!--To be able to create the technical accounts which replace the technical operators, the prerequisite that the proper Campaign Product Profiles exist within the Admin Console for all Campaign instances need to be validated. You can learn more about Product Profiles within the Adobe Console in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.-->

* Clientes de Campaign alojados y Managed Services

  Para las llamadas API a las instancias del Centro de mensajes, se debería haber creado un perfil de producto durante la actualización a Campaign v7.3.5 o durante el aprovisionamiento de la instancia. Este perfil de productos se denomina:

  `campaign - <your campaign instance> - messagecenter`

  Si ya ha estado utilizando la autenticación basada en IMS para el acceso de los usuarios a Campaign, los perfiles de producto necesarios para las llamadas de API ya deben existir dentro del Admin Console. Si utiliza un grupo de operadores personalizado en Campaign para las llamadas de API a la instancia de Marketing, debe crear ese perfil de producto dentro del Admin Console.

  Para otros casos, debe ponerse en contacto con el administrador de transición de Adobe (para usuarios de Managed Services) o con el servicio de atención al cliente de Adobe (para otros usuarios alojados), de modo que los equipos técnicos de Adobe puedan migrar los grupos de operadores existentes y los derechos asignados a los perfiles de producto dentro del Admin Console.

* Clientes on-Premise e híbridos de Campaign

  Para las llamadas de API a las instancias del Centro de mensajes, debe crear un perfil de producto denominado:

  `campaign - <your campaign instance> - messagecenter`

  Si ya ha estado utilizando la autenticación basada en IMS para el acceso de los usuarios a Campaign, los perfiles de producto necesarios para las llamadas de API ya deben existir dentro del Admin Console. Si utiliza un grupo de operadores personalizado en Campaign para las llamadas de API a la instancia de Marketing, debe crear ese perfil de producto dentro del Admin Console.

  Puede obtener más información sobre los Perfiles de producto en la Consola de Adobe en [Documentación de la consola Adobe Developer](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}


### Paso 1: Creación del proyecto de Campaign en la consola de Adobe Developer {#ims-migration-step-1}

Las integraciones se crean como parte de un **Proyecto** en la consola de Adobe Developer. Más información sobre los Proyectos en [Documentación de la consola Adobe Developer](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.

Puede utilizar cualquier proyecto creado anteriormente por usted o puede crear un nuevo proyecto. Los pasos para crear un proyecto se detallan en la [Documentación de la consola Adobe Developer](https://developer.adobe.com/developer-console/docs/guides/getting-started/){target="_blank"}. Puede encontrar los pasos clave a continuación

<!--
For this migration, you must add below APIs in your project: **I/O Management API** and **Adobe Campaign**.

![](assets/do-not-localize/ims-products-and-services.png)-->

Para crear un nuevo proyecto, haga clic en **Crear nuevo proyecto** en la pantalla principal de la consola de Adobe Developer.

![](assets/New-Project.png)

Puede usar el complemento **Editar proyecto** para cambiar el nombre de este proyecto.


### Paso 2: Añadir API al proyecto {#ims-migration-step-2}

Desde la pantalla del proyecto recién creado, añada la API necesaria para poder utilizar este proyecto como una cuenta técnica para sus llamadas de API a Adobe Campaign.

Para añadir API al proyecto, siga estos pasos:

1. Haga clic en **Añadir API** para seleccionar las API que desea añadir al proyecto.
   ![](assets/do-not-translate/ims-updates-01.png)
1. Seleccione y añada la API de Adobe Campaign a su proyecto marcando la casilla en la esquina superior derecha de la tarjeta de Adobe Campaign que aparece cuando pasa el ratón sobre la tarjeta
   ![](assets/do-not-translate/ims-updates-02.png)
1. Clic **Siguiente** en la parte inferior de la pantalla.

### Paso 3: Selección del tipo de autenticación  {#ims-migration-step-3}

En el **Configurar API** , seleccione el tipo de autenticación necesario. **Servidor a servidor OAuth** Se requiere autenticación para este proyecto. Asegúrese de que está seleccionado y haga clic en **Siguiente** en la parte inferior de la pantalla.

![](assets/do-not-translate/ims-updates-03.png)

<!--
Once your project is created in the Adobe Developer Console, add an API that uses Server-to-Server authentication. Learn how to set up the OAuth Server-to-Server credential in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/){target="_blank"}.

When the API has been successfully connected, you can access the newly generated credentials including Client ID and Client Secret, as well as generate an access token.-->

### Paso 4: Selección de los perfiles de producto {#ims-migration-step-4}

Como se describe en la sección Requisitos previos, debe asignar los perfiles de producto adecuados para que los utilice el proyecto. En este paso, debe seleccionar los perfiles de producto que se utilizarán en la cuenta técnica que se está creando.

Si esta cuenta técnica se utiliza para realizar llamadas de API a la instancia del Centro de mensajes, asegúrese de seleccionar el Adobe crear perfil de producto que termina con `messagecenter`.

Para las llamadas API a las instancias de marketing, seleccione el perfil de producto correspondiente a la instancia y al grupo de operadores.

Una vez seleccionados los perfiles de producto necesarios, haga clic en **Guardar API configurada** en la parte inferior de la pantalla.

<!--
You can now add your Campaign product profile to the project, as detailed below:

1. Open the Adobe Campaign API.
1. Click the **Edit product profiles** button

    ![](assets/do-not-localize/ims-edit-api.png)

1. Assign all the relevant Product Profiles to the API, for example 'messagecenter', and save your changes.
1. Browse to the **Credential details** tab of your project, and copy the **Technical Account Email** value.-->

### Paso 5: Añadir la API de administración de E/S al proyecto {#ims-migration-step-5}


En la pantalla del proyecto, haga clic en **[!UICONTROL + Add to Project]** y elija **[!UICONTROL API]** en la parte superior izquierda de la pantalla para poder agregar la API de administración de E/S a este proyecto.

![](assets/do-not-translate/ims-updates-04.png)

En el **Añadir una API** , desplácese hacia abajo para buscar la **API de administración de E/S** Tarjeta de. Selecciónelo haciendo clic en la casilla de verificación que aparece al pasar el ratón por encima de la tarjeta. Luego haga clic en **Siguiente** en la parte inferior de la pantalla.

![](assets/do-not-translate/ims-updates-05.png)


En el **Configurar API** , la autenticación de servidor a servidor OAuth ya existe. Clic **Guardar API configurada** en la parte inferior de la pantalla.


![](assets/do-not-translate/ims-updates-06.png)

Esto le lleva de nuevo a la pantalla Proyecto dentro de la API de administración de I/O del proyecto recién creado. Haga clic en el nombre del proyecto en las rutas de exploración en la parte superior de la pantalla para que vuelva a la página principal de Detalles del proyecto.


### Paso 6: Verificación de la configuración del proyecto {#ims-migration-step-6}

Revise el proyecto para asegurarse de que tiene un aspecto similar al siguiente con la variable **API de administración de E/S** y **API de Adobe Campaign** visible en la sección Productos y servicios y **Servidor a servidor OAuth** en la sección Credenciales.

![](assets/do-not-translate/ims-updates-07.png)


### Paso 7: Validación de la configuración {#ims-migration-step-7}

Para probar la conexión, siga los pasos detallados en la [Guía de credenciales de la consola Adobe Developer](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/#generate-access-tokens){target="_blank"} para generar un token de acceso y copiar el comando cURL de ejemplo proporcionado. Puede crear una llamada soap utilizando estas credenciales para probar que puede autenticarse y conectarse correctamente a las instancias de Adobe Campaign. Se recomienda realizar esta validación antes de realizar todos los cambios en las integraciones de API de terceros.

### Paso 8: Actualización de las integraciones de API de terceros {#ims-migration-step-8}

Ahora debe actualizar las integraciones de la API de realizando llamadas a Adobe Campaign para utilizar la cuenta técnica recién creada.

Para obtener más información sobre los pasos de integración de la API, incluido un código de ejemplo para una integración sin problemas, consulte [Documentación de autenticación de la consola Adobe Developer](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}.

A continuación se muestran llamadas SOAP de ejemplo que muestran las llamadas de migración antes y después para los sistemas de terceros.

Una vez completado y validado el proceso de migración, las llamadas Soap se actualizan de la siguiente manera:



* Antes de la migración: no se admitía el token de acceso de la cuenta técnica.

  ```sql
  POST /nl/jsp/soaprouter.jsp HTTP/1.1
  Host: localhost:8080
  Content-Type: application/soap+xml;
  SOAPAction: "nms:rtEvent#PushEvent"
  charset=utf-8
  
  <?xml version="1.0" encoding="utf-8"?>  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
  <soapenv:Header/>
  <soapenv:Body>
      <urn:PushEvent>
          <urn:sessiontoken>SESSION_TOKEN</urn:sessiontoken>
          <urn:domEvent>
              <!--You may enter ANY elements at this point-->
              <rtEvent type="type" email="name@domain.com"/>
          </urn:domEvent>
      </urn:PushEvent>
  </soapenv:Body>
  </soapenv:Envelope>
  ```

* Después de la migración: no se admite el token de acceso de la cuenta técnica. Se espera que el token de acceso se proporcione en `Authorization` encabezado como token de portador. El uso del token de sesión debe ignorarse aquí, como se muestra en el siguiente ejemplo de llamada soap.

  ```sql
  POST /nl/jsp/soaprouter.jsp HTTP/1.1
  Host: localhost:8080
  Content-Type: application/soap+xml;
  SOAPAction: "nms:rtEvent#PushEvent"
  charset=utf-8
  Authorization: Bearer <IMS_Technical_Token_Token>
  
  <?xml version="1.0" encoding="utf-8"?>  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
  <soapenv:Header/>
  <soapenv:Body>
      <urn:PushEvent>
          <urn:sessiontoken></urn:sessiontoken>
          <urn:domEvent>
              <!--You may enter ANY elements at this point-->
              <rtEvent type="type" email="name@domain.com"/>
          </urn:domEvent>
      </urn:PushEvent>
  </soapenv:Body>
  </soapenv:Envelope>
  ```



### Paso 9: (opcional) Actualización del operador de cuenta técnica en la consola del cliente de Campaign {#ims-migration-step-9}

Este paso es opcional y solo está disponible dentro de las instancias de Marketing, no dentro de ninguna instancia del Centro de mensajes. Si se han definido permisos de carpeta específicos o derechos asignados para el operador técnico, no a través de los grupos de operadores asignados. Ahora deberá actualizar el usuario de la cuenta técnica recién creada en el Admin Console para conceder los permisos de carpeta o los derechos asignados necesarios.

Tenga en cuenta que el usuario de cuenta técnica NO existirá en Adobe Campaign hasta que se realice al menos una llamada de API a la instancia de Campaign, momento en el que IMS creará el usuario dentro de Campaign. Si no puede localizar a los usuarios técnicos en Campaign, asegúrese de que ha podido enviar correctamente una llamada de API como se ha descrito anteriormente [en el paso 7](#ims-migration-step-7).

1. Para aplicar los cambios necesarios para el nuevo usuario de cuenta técnica, localícelos en la consola del cliente de Campaign por dirección de correo electrónico. Esta dirección de correo electrónico se creó durante los pasos Creación de proyecto y Autenticación anteriores.

   Puede localizar esta dirección de correo electrónico haciendo clic en el icono **Servidor a servidor OAuth** encabezado en el **Credenciales** del proyecto.

   ![](assets/do-not-translate/ims-updates-07.png)

   En la pantalla de credenciales de, desplácese hacia abajo para localizar el ** de correo electrónico de cuenta técnica de ** y haga clic en **Copiar** botón.

   ![](assets/do-not-translate/ims-updates-08.png)

1. Ahora debe actualizar el operador técnico recién creado en la consola del cliente de Adobe Campaign. Debe aplicar los permisos de carpeta de operador técnico existentes al nuevo operador técnico.

   Para actualizar este operador, siga estos pasos:

   1. Desde el explorador de la consola del cliente de Campaign, vaya a **Administración > Administración de acceso > Operadores**.
   1. Acceda al operador técnico existente utilizado para las API.
   1. Vaya a los permisos de la carpeta y compruebe los derechos.
   1. Aplique los mismos permisos al operador técnico recién creado. El correo electrónico de este operador es el siguiente **Correo electrónico de cuenta técnica** valor copiado anteriormente.
   1. Guarde los cambios.


>[!CAUTION]
>
>El nuevo operador técnico debe haber realizado al menos una llamada de API para añadirla a la consola del cliente de Campaign.
>

### Paso 10: Eliminación del operador técnico antiguo de Adobe Campaign {#ims-migration-step-10}

Una vez que haya migrado todos los sistemas de terceros para utilizar la nueva cuenta técnica con autenticación IMS, puede eliminar el operador técnico antiguo de la consola del cliente de Campaign.

Para ello, inicie sesión en la consola del cliente de Campaign y navegue hasta **Administración > Administración de acceso > Operadores** y localizando los usuarios técnicos antiguos y eliminándolos.
