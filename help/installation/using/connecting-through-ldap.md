---
solution: Campaign Classic
product: campaign
title: Conexión mediante LDAP
description: 'Aprenda a utilizar LDAP para iniciar sesión en la Campaña '
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 1%

---


# Conexión mediante LDAP{#connecting-through-ldap}

## Configuración de Campaña y LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>La configuración LDAP sólo es posible para instalaciones in situ o híbridas.

La configuración de LDAP se realiza en el asistente de implementación. La opción **[!UICONTROL LDAP integration]** debe seleccionarse durante el primer paso de configuración. Consulte [Asistente para implementación](../../installation/using/deploying-an-instance.md#deployment-wizard).

La ventana permite configurar la identificación de usuarios de Adobe Campaign mediante el directorio LDAP especificado.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Especifique la dirección del servidor LDAP en el campo **[!UICONTROL LDAP server]**. Puede agregar el número de puerto. De forma predeterminada, el puerto utilizado es 389.
* En la lista desplegable, seleccione el método de autenticación para los usuarios:

   * Contraseña cifrada (**md5**)

      Modo predeterminado.

   * Contraseña de texto sin formato + SSL (**TLS**)

      Se cifra todo el procedimiento de autenticación (se incluye la contraseña). El puerto seguro 636 no debe usarse en este modo: Adobe Campaign cambia automáticamente al modo seguro.

      Cuando utiliza este modo de autenticación, en Linux, el certificado se comprueba mediante una biblioteca de cliente openLDAP. Se recomienda utilizar un certificado SSL válido para que el procedimiento de autenticación esté cifrado. De lo contrario, la información estará en texto sin formato.

      El certificado también se comprueba en Windows.

   * Administrador de LAN de Windows NT (**NTLM**)

      Autenticación privada de Windows. El **[!UICONTROL Unique identifier]** se utiliza solamente para el nombre de dominio.

   * Autenticación de contraseña distribuida (**DPA**)

      Autenticación privada de Windows. El **[!UICONTROL Unique identifier]** se utiliza solamente para el nombre de dominio (domain.com).

   * Contraseña de texto sin formato

      No hay cifrado (solo para uso en fases de prueba).

* Seleccione el modo de autenticación de usuario: **[!UICONTROL Automatically compute the unique user identifier]** (consulte el paso [Cálculo del nombre distinguido](#distinguished-name-calculation)) o **[!UICONTROL Search the unique user identifier in the directory]** (consulte el paso [Búsqueda de identificadores](#searching-for-identifiers)).

## Compatibilidad {#compatibility}

Los sistemas compatibles dependen del mecanismo de autenticación seleccionado. A continuación se muestra una matriz de compatibilidad de sistemas operativos y servidores LDAP.

<table> 
 <thead> 
  <tr> 
   <th> </th> 
   <th> OpenLDAP<br /> </th> 
   <th> Active Directory<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> md5<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> TLS<br /> </td> 
   <td> Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> NTLM y DPA<br /> </td> 
   <td> </td> 
   <td> Windows<br /> </td> 
  </tr> 
  <tr> 
   <td> texto sin formato<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Cálculo de nombre distintivo {#distinguished-name-calculation}

Si desea calcular los identificadores de Nombre distintivo (DN), el siguiente paso del asistente de implementación le permite configurar el modo de cálculo.

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* Especifique el identificador único del usuario en el directorio (Nombre distintivo - DN) en el campo **[!UICONTROL Distinguished Name]**.

   **[!UICONTROL (login)]** se reemplazará por el identificador del operador de Adobe Campaign.

   >[!CAUTION]
   >
   >La configuración **[!UICONTROL dc]** debe estar en minúsculas.

* Seleccione la opción **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** para sincronizar las asociaciones de grupos y usuarios en el directorio LDAP y las asociaciones de grupos y usuarios en Adobe Campaign.

   Cuando selecciona esta opción, **[!UICONTROL Application level DN used for the search]** y **[!UICONTROL Password of the application login]** están activados.

   Si rellena estos dos campos, Adobe Campaign se conectará al servidor LDAP con su propio inicio de sesión y contraseña. Si están vacías, Adobe Campaign se conectará al servidor de forma anónima.

## Buscando identificadores {#searching-for-identifiers}

Si elige buscar un identificador, el asistente de implementación le permite configurar la búsqueda.

* En los campos **[!UICONTROL Application level DN used for the search]** y **[!UICONTROL Password of the application login]**, proporcione el identificador y la contraseña con los que Adobe Campaign se conectará para buscar el identificador. Si están vacías, Adobe Campaign se conectará al servidor de forma anónima.
* Especifique los campos **[!UICONTROL Base identifier]** y **[!UICONTROL Search scope]** para determinar un subconjunto del directorio LDAP desde el que se va a realizar el inicio de la búsqueda.

   Seleccione el modo requerido en la lista desplegable:

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      El directorio LDAP se busca en su totalidad, comenzando desde un nivel determinado.

   1. **[!UICONTROL Limited to the base]**.

      Todos los atributos se incluyen en la búsqueda.

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      La búsqueda se realiza en todos los atributos del directorio y a partir del primer nivel del atributo.

* El campo **[!UICONTROL Filter]** permite especificar un elemento para reducir el alcance de la búsqueda.

## Configuración de autorizaciones LDAP {#configuring-ldap-authorizations}

Esta ventana se muestra cuando selecciona la opción **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

Debe especificar varios parámetros para encontrar el grupo o los grupos a los que pertenece el usuario y sus derechos correspondientes, por ejemplo:

* el campo **[!UICONTROL Database identifier]**,
* el campo **[!UICONTROL Search scope]**,

   >[!NOTE]
   >
   >Si ha elegido buscar el DN, puede seleccionar **[!UICONTROL Reuse the DN search parameters]** para transferir los valores seleccionados para el DN y el ámbito de búsqueda de la pantalla anterior.

* el campo **[!UICONTROL Rights search filter]**, basado en el inicio de sesión y el nombre de reconocimiento del usuario,
* el campo **[!UICONTROL Attribute containing the group or authorization name]** relativo al usuario,
* el campo **[!UICONTROL Association mask]** que habilita la extracción del nombre del grupo en Adobe Campaign y sus derechos asociados. Puede utilizar expresiones regulares para buscar el nombre.
* Seleccione **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** para que el usuario reciba automáticamente derechos de acceso en la conexión.

Haga clic en **[!UICONTROL Save]** para finalizar la configuración de la instancia.

## Administración de operadores {#managing-operators}

Una vez confirmada la configuración, debe definir qué operadores de Adobe Campaign se administran mediante el directorio LDAP.

Para utilizar el directorio LDAP para autenticar un operador, edite el perfil correspondiente y haga clic en el vínculo **[!UICONTROL Edit the access parameters]**. Seleccione la opción **[!UICONTROL Use LDAP for authentication]**: El campo **[!UICONTROL Password]** está atenuado para este operador.

![](assets/s_ncs_install_operator_in_ldap.png)

## Ejemplos de uso {#use-cases}

Esta sección proporciona algunos casos de uso sencillos para ayudarle a lograr las configuraciones más apropiadas según sus necesidades.

1. Se ha creado un usuario en el directorio LDAP pero no en Adobe Campaign.

   Adobe Campaign se puede configurar para que el usuario acceda a la plataforma mediante su autenticación LDAP. Adobe Campaign debe poder controlar la validez de la combinación de ID y contraseña en el directorio LDAP, de modo que el operador se pueda crear sobre la marcha en Adobe Campaign. Para ello, marque la opción **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]**. En este caso, también es necesario configurar la sincronización de grupos: es necesario seleccionar la opción **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**.

1. El usuario se ha creado en Adobe Campaign pero no en el directorio LDAP.

   No podrán iniciar sesión en Adobe Campaign.

1. Hay un grupo en el directorio LDAP que no existe en Adobe Campaign.

   Este grupo no se creará en Adobe Campaign. Debe crear el grupo y sincronizar los grupos para habilitar una coincidencia mediante la opción **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**.

1. Existen grupos en Adobe Campaign y el directorio LDAP se activa después del evento: los grupos de usuarios de Adobe Campaign no se reemplazan automáticamente con el contenido de los grupos LDAP. Del mismo modo, si un grupo solo existe en Adobe Campaign, no se podrá agregar ningún usuario LDAP hasta que el grupo se haya creado y sincronizado en LDAP.

   Los grupos nunca se crean sobre la marcha, ya sea por Adobe Campaign o por LDAP. Deben crearse individualmente, tanto en Adobe Campaign como en el directorio LDAP.

   Los nombres de los grupos en el directorio LDAP deben coincidir con los nombres de los grupos de Adobe Campaign. Su máscara de asociación se define en la última etapa de configuración del asistente de implementación: Adobe Campaign_(.*), por ejemplo.

