---
title: Migrar a Adobe Identity Management System (IMS)
description: Obtenga información sobre cómo migrar el proceso de autenticación a Adobe Identity Management System (IMS)
source-git-commit: 106f0409f452595209f0e2aa2fa187a2e04338a9
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 1%

---

# Migrar a Adobe Identity Management System (IMS) {#migrate-to-ims}

Como parte del esfuerzo por reforzar la seguridad y el proceso de autenticación, Adobe Campaign recomienda migrar el modo de autenticación del usuario final de la autenticación nativa de inicio de sesión/contraseña a [Adobe Identity Management System (IMS)](https://helpx.adobe.com/es/enterprise/using/identity.html){target="_blank"}.

Además, la aplicación cliente de Adobe Campaign ahora llama a las API de Campaign directamente mediante el token de cuenta técnica de IMS. Debe migrar los operadores técnicos a la consola de Adobe Developer.

>[!CAUTION]
>
>Este cambio ya se aplica en Campaign Classic v7 y se **obligatorio** para pasar a Campaign v8. La autenticación de usuario/contraseña nativa no está permitida en Campaign v8. **El Adobe recomienda realizar esta migración a partir de la versión 7.3.5 de Campaign para poder migrar sin problemas a la versión 8 de Campaign.**
>

## Pasos de migración {#ims-steps}

Migración a [Adobe Identity Management System (IMS)](https://helpx.adobe.com/es/enterprise/using/identity.html){target="_blank"} Es un imperativo de seguridad hacer que sus entornos sean seguros y estandarizados, ya que la mayoría de las otras soluciones y aplicaciones de Adobe Experience Cloud ya están en IMS.

El Adobe le ayuda en este esfuerzo de migración. Puede encontrar información detallada sobre el contexto y las directrices paso a paso en los siguientes artículos:

* La migración para la autenticación de usuarios finales se detalla en [esta página](migrate-users-to-ims.md).
* La migración para la autenticación de operadores técnicos se detalla en [esta página](ims-migration.md).
* A partir de la versión 7.4.1 de Campaign, habilite la interfaz de usuario y las restricciones de la API para eliminar las opciones y funcionalidades específicas de la autenticación nativa, como se detalla en [esta página](impact-ims-migration.md).


## Versiones compatibles con la migración IMS {#ims-versions}

Un requisito previo para esta migración es actualizar su entorno a una de las siguientes versiones de producto:

* Campaign v7.4.1 (recomendado)
* Campaign v7.3.5
* Campaign v7.3.3.IMS
* Campaign v7.3.2.IMS

Estas versiones de Campaign se detallan en la sección [Notas de versión](../../rn/using/latest-release.md).

## Preguntas frecuentes {#ims-migration-faq}

### ¿Cuándo puedo iniciar la migración? {#ims-migration-start}

Una recomendación para la migración a [Adobe Identity Management System (IMS)](https://helpx.adobe.com/es/enterprise/using/identity.html){target="_blank"} es actualizar su entorno a Campaign Classic v7.4.1 (o un [Versión compatible con la migración IMS](#ims-versions)).

Puede iniciar la migración de IMS en el entorno de ensayo, una vez que se actualice a la versión más reciente y, en consecuencia, planificar el entorno de producción.

### ¿Qué sucede después de la actualización de la compilación a Campaign Classic v7.4.1? {#ims-migration-after-upgrade}

Una vez que los entornos se hayan actualizado a Campaign Classic v7.4.1 (o un [Versión compatible con la migración IMS](#ims-versions)), puede iniciar la transición a [Adobe Identity Management System (IMS)](https://helpx.adobe.com/es/enterprise/using/identity.html){target="_blank"}.

### ¿Cuándo se completa la migración? {#ims-migration-end}

Una vez completada la migración del usuario final y la migración de los operadores técnicos a Adobe Identity Management System (IMS), debe actualizar su entorno para eliminar las opciones específicas de la autenticación nativa y que ya no son aplicables a la autenticación IMS. Esta actualización solo está disponible a partir de la versión 7.4.1 de Campaign. [Más información](impact-ims-migration.md)



## Vínculos útiles {#ims-useful-links}

* [Migración de usuarios finales a IMS](migrate-users-to-ims.md)
* [Migración de operadores técnicos a la consola de Adobe Developer](ims-migration.md)
* [Últimas notas de la versión de Adobe Campaign Classic v7](../../rn/using/latest-release.md)
* [¿Qué es Adobe Identity Management System (IMS)?](https://helpx.adobe.com/es/enterprise/using/identity.html){target="_blank"}
