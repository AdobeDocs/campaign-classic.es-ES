---
title: Actualización de la interfaz de Campaign después de la migración IMS
description: Obtenga información sobre cómo activar los impactos de la interfaz de migración del sistema Identity Management de Adobe
exl-id: 8b13fe4d-d8d3-43b3-bbe4-c8c5574f585a
source-git-commit: 8eadea9f9cc0a44522726024bfbc825e3b4cad98
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 1%

---

# Actualización de la interfaz de Campaign después de la migración IMS {#impact-ims-migration}

Una vez que haya [migrado los operadores técnicos de Campaign a Developer Console](ims-migration.md) y haya [realizado la transición a IMS para la autenticación del usuario final](migrate-users-to-ims.md), el último paso es habilitar la interfaz de usuario y las restricciones de API para eliminar las opciones y capacidades específicas de la autenticación nativa. Esta actualización está disponible a partir de la versión 7.4.1 de Campaign.

## Habilitar restricciones de IMS {#ims-restrictions}

Para finalizar la migración a Adobe Identify Management System (IMS), debe bloquear la creación de nuevos usuarios nativos, el inicio de sesión de usuarios nativos y el acceso a API para operadores nativos. A continuación, su entorno está protegido y estandarizado.

Como Cloud Service administrado/usuario alojado, póngase en contacto con el Adobe para habilitar esta restricción y las actualizaciones asociadas en la interfaz de usuario del producto.

Como usuario on-premise/híbrido, siga estos pasos:

1. Vaya a la sección `<imsConfig>` del archivo de configuración de instancia.
1. Para habilitar las restricciones de la interfaz de usuario, actualice la opción `nonIMSOperatorMgmtInClientConsoleRestricted`, dentro del elemento `nonIMSOperatorMgmtInClientConsole`, a `true`, como se muestra a continuación:


   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSOperatorMgmtInClientConsole nonIMSOperatorMgmtInClientConsoleRestricted="true"/>
       </imsConfig>
   </shared>
   </serverConf>
   ```

1. Para habilitar las restricciones de la API, actualice la opción `disableAPI`, dentro del elemento `nonIMSAuthnAPI`, a `true`, como se muestra a continuación:

   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSAuthnAPI disableAPI="true">
               ...
           </nonIMSAuthnAPI>
       </imsConfig>
   </shared>
   </serverConf>
   ```

Tenga en cuenta que algunos operadores pueden conectarse a Adobe Campaign con una autenticación nativa. Estos operadores técnicos están habilitados de forma predeterminada y no se deben modificar. Para permitir esta excepción, estos operadores técnicos se añaden de forma predeterminada a la lista de permitidos. Puede encontrar esta lista en la sección `<imsConfig>` del archivo de configuración de instancia, en la opción `allowOperator` dentro del elemento `nonIMSAuthnAPI`.

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

Si necesita agregar un operador a la lista de permitidos, agregue un nuevo elemento `allowOperator` con el nombre del operador. Por ejemplo, si desea agregar un operador nuevo con el nombre `test`, actualice esta sección de la siguiente manera:

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
            <allowOperator name="test"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

## Impactos en la interfaz de usuario {#ims-impacts}

Una vez finalizada la migración y aplicadas las restricciones tal como se describe a continuación, se aplican los siguientes cambios al producto y a su interfaz de usuario.

### Administración del operador {#manage-admin}

Ya no puede crear, editar, actualizar ni eliminar operadores con autenticación nativa desde la consola del cliente.

Como consecuencia, estas acciones se han deshabilitado en la consola del cliente.

La administración de operadores está centralizada en Adobe Admin Console y las siguientes tareas se gestionan ahora exclusivamente a través de esta consola. Aprenda a crear usuarios y asignar permisos en la [documentación de Campaign v8](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/admin/permissions/manage-permissions){target="_blank"}.

### Opciones no disponibles {#unavailable-migration}

Después de la migración, las siguientes tareas ya no estarán disponibles en la consola del cliente:

* Utilice la opción [Combinar líneas seleccionadas](../../platform/using/updating-data.md#merge-data) para combinar operadores.

* Actualice los campos siguientes para sus operadores:
   * Nombre
   * Contraseña
   * Etiqueta
   * Correo electrónico

* [Restablecer la contraseña de Campaign](../../production/using/lost-password.md)

* Editar la fuente XML de los operadores

* Operadores duplicados.


>[!MORELIKETHIS]
>
>* [Migración de usuarios finales a IMS](migrate-users-to-ims.md)
>* [Migración de operadores técnicos a la consola de Adobe Developer](ims-migration.md)
>* [Últimas notas de la versión de Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [Qué es el sistema Identity Management de Adobe (IMS)](https://helpx.adobe.com/es/enterprise/using/identity.html){target="_blank"}
