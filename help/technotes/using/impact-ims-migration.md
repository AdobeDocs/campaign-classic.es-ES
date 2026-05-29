---
title: Actualización de la interfaz de Campaign después de la migración IMS
description: Obtenga información sobre cómo activar los impactos de la interfaz de migración del sistema de Adobe Identity Management
exl-id: 8b13fe4d-d8d3-43b3-bbe4-c8c5574f585a
TQID: https://experienceleague.adobe.com/RkgX2M0BnO5pjgI7oAp7NlycXY551manwFHhcA1LMjw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2:
  - id: a39dbcf0-89cb-4765-9bcb-cf9dfbe2875f
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 463
ht-degree: 1%

---

# Actualización de la interfaz de Campaign después de la migración IMS {#impact-ims-migration}

Una vez que haya [migrado los operadores técnicos de Campaign a Developer Console](ims-migration.md) y haya [realizado la transición a IMS para la autenticación del usuario final](migrate-users-to-ims.md), el último paso es habilitar la interfaz de usuario y las restricciones de API para eliminar las opciones y capacidades específicas de la autenticación nativa. Esta actualización está disponible a partir de la versión 7.4.1 de Campaign.

## Habilitar restricciones de IMS {#ims-restrictions}

Para finalizar la migración a Adobe Identify Management System (IMS), debe bloquear la creación de nuevos usuarios nativos, el inicio de sesión de usuarios nativos y el acceso a la API para los operadores nativos. A continuación, su entorno está protegido y estandarizado.

Como usuario de Cloud Service administrado o alojado, póngase en contacto con Adobe para habilitar esta restricción y las actualizaciones asociadas en la interfaz de usuario del producto.

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

La administración de operadores está centralizada en Adobe Admin Console y las siguientes tareas se gestionan ahora exclusivamente a través de esta consola. Obtenga información sobre cómo crear usuarios y asignar permisos en [Documentación de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/manage-permissions){target="_blank"}.

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
>* [Qué es Adobe Identity Management System (IMS)](https://helpx.adobe.com/es/enterprise/using/identity.html){target="_blank"}
