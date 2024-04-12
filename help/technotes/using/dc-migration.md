---
product: campaign
title: Migración a la nube pública
description: Obtenga más información sobre la migración de Campaign Classic a la nube pública
feature: Technote, Upgrade
role: User
level: Beginner
exl-id: 2b282221-d048-4f6e-b52e-f8e584af2c0e
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1533'
ht-degree: 48%

---

# Información general{#dc-ovv}



## Contexto

Como valioso cliente de Adobe Campaign Classic, estamos comprometidos a proporcionarle la mejor experiencia y el mayor valor posibles. A lo largo de los años, nos hemos dado cuenta del valor y la fiabilidad de alojar a nuestros clientes en la nube.  Como parte de nuestro [Iniciativa de actualización anual](../../rn/using/rn-overview.md#yearly-upgrade)Por lo tanto, estamos trasladando a todos nuestros clientes a Adobe Managed Services (Nube pública en AWS) para proporcionar servicios mejores y más fiables.

Este programa tiene tres objetivos principales:

* Hacer frente a las vulnerabilidades de seguridad identificadas trasladando la infraestructura a un entorno seguro y moderno (AWS).
* Elimine los procesos de ampliación potencialmente engorrosos y proporcione acceso a nuestros [MTA mejorados](../../delivery/using//sending-with-enhanced-mta.md) y mejorar todos los niveles de servicio de mantenimiento.
* Prepare su instancia para el futuro de Adobe Campaign Classic, incluidas actualizaciones más automatizadas y regulares que no requieran tantos recursos ni tanto tiempo.

### Glosario

* **Actualización de compilación** : Cuando el software de Adobe Campaign Classic se actualiza al último número de compilación segura, pero permanece en el mismo nivel de compilación principal/menor. Por ejemplo: Campaign 7 versión 20.2.3 compilación 9182 a Campaign 7 versión 21.2.5 compilación 9188. [Más información](../../platform/using/faq-build-upgrade.md).
* **MID/RT** : Servidores de ejecución de mensajes alojados en Adobe Cloud (MID para campañas por lotes y RT para mensajes unitarios en tiempo real)
* **Programa de actualización anual** - este programa proporciona una mayor seguridad, soporte, mantenimiento y estabilidad. También facilita las futuras actualizaciones y proporciona acceso a nuevas funciones en Campaign.  [Más información](../../rn/using/rn-overview.md#yearly-upgrade).
* **AWS** - Amazon Web Service (nube pública de Amazon)
* **SFTP** - Protocolo seguro de transferencia de archivos. [Más información](../../platform/using/sftp-server-usage.md).


>[!NOTE]
>La migración de Campaign Classic v7 a la nube pública afecta a los clientes que utilizan **Adobe Managed Services** solo.


## Ventajas

**Seguridad**

* Últimas correcciones de seguridad
* Cifrado de datos en reposo 
* Autenticación mejorada (IMS)

**Infraestructura**

* Adaptación de hardware Agile
* Restauración más rápida
* Mayor fiabilidad y estabilidad
* Procedimientos operativos armonizados

**Rendimientos**

* Capacidad de correo electrónico mejorada
* Bases de datos más grandes
* Versión de campaña probada

**Brinde una solución sólida y fiable a los clientes de Adobe Campaign Classic**

1. Mejores procedimientos de producción, que llevan a una mayor fiabilidad, una reactividad más rápida en caso de problemas y una recuperación más rápida en caso de incidentes graves.
1. Mayor capacidad de envío de correo electrónico. Las instancias alojadas en el nuevo centro de datos tendrán la posibilidad de beneficiarse de una infraestructura especializada para la entrega por correo electrónico. Esto podría dar como resultado una mayor velocidad de envío de correo electrónico o permitir el uso de menos direcciones IP de envío.
1. Mejor adaptación de hardware. Aumentar los recursos de hardware se puede hacer mucho más rápido. Técnicamente, se tardaría en torno a 1 hora en lugar de varios días.

**Las actualizaciones anuales facilitan las futuras actualizaciones**

1. Cuanto más tiempo pasa su organización esperando que se produzca la actualización, más compleja se vuelve la misma y aumenta el potencial de sufrir vulnerabilidades (especialmente al pasar de una versión anterior).
1. Con la actualización anual de Campaign (iniciativa Gold Standard), su instancia se modernizará y estará lista para recibir actualizaciones más automatizadas y regulares con menos intervención manual y menos recursos.

![](assets/GSMigrations.png)

## Acerca de la migración

Para comenzar como es debido, las cuentas que requieran esta migración recibirán un mensaje de Adobe por correo electrónico con una cronología y acceso a la documentación. Esta notificación le indica que se ha programado la migración de su cuenta.

Se puede iniciar una migración mediante [abrir un nuevo ticket de asistencia al cliente](https://experienceleague.adobe.com/?support-solution=Campaign#support). Utilice la línea de asunto &quot;Migrar a AWS&quot;.

### ¿Es obligatoria esta migración?

Esta migración a la nube es **primer paso para la [programa de actualización anual](../../rn/using/rn-overview.md#yearly-upgrade)** de las instancias de Adobe Campaign. Esta migración es obligatoria si está alojado en un centro de datos que no es de la nube pública (AWS).

La nube de Adobe Managed Services está alojada en Amazon Web Service (AWS), un entorno moderno, seguro y optimizado. [Más información sobre AWS](https://aws.amazon.com/application-hosting/benefits/).

Adobe planea eliminar el antiguo centro de datos, las instancias de Adobe Campaign que se ejecuten allí deben transferirse al nuevo centro de datos de referencia, AWS.

A partir de ahí, hay que realizar el proceso con mucho cuidado ya que su ubicación actual puede estar expuesta a **vulnerabilidades de seguridad y rendimiento**.

Además, esta migración es ahora una **requisito previo para cualquier actualización futura de la compilación** de su Adobe Campaign. La actualización de compilación ya no es posible en el centro de datos heredado.

Adobe se ha comprometido a proteger sus datos y prepararle para el futuro de Adobe Campaign. Necesitamos su colaboración para que sea un éxito conjunto.


**Hemos organizado un equipo** de representantes del Servicio de atención al cliente, responsables de éxito de clientes, gerentes de productos, ingenieros, especialistas en TechOps y consultores de productos dedicados para ayudar y garantizar que la experiencia sea fluida y se desarrolle sin problemas. Nos comprometemos a garantizar que dispone de la información de contacto y del proyecto pertinente.

Hemos invertido un gran esfuerzo en desarrollar tecnologías que nos ayudarán a llevar a cabo esta migración de forma rápida, fluida y segura.

### Restricciones

* Es inevitable que la migración conlleve algo de tiempo de inactividad. El objetivo de este plan es guiar para minimizar este tiempo de inactividad.
* Cambio de IP para integraciones de datos.
* Aumento de la capacidad de entrega de nuevas IP de envío. Sin embargo, el plan es hacer que esta operación sea transparente para el negocio, a diferencia de la mejora inicial que se realiza durante el lanzamiento.

Obtenga más información en Migración de Campaign a [Preguntas frecuentes sobre Public Cloud](dc-migration-faq.md).


## Ruta de migración a la nube pública

Adobe se encarga de la mayoría de las acciones. Lo necesitamos para la validación y la aprobación.

![](assets/MigrationPath.png)

## Directrices de migración

### Enfoque global

**Database**

La base de datos se descargará del centro de datos heredado y se restaurará en la nube pública (AWS). Cuando se reinicia en el nuevo centro de datos, la aplicación se reanudará desde el estado exacto en que estaba antes del cierre. Los usuarios no verán ninguna diferencia, excepto que algunas tareas programadas se habrán retrasado.

**IP de envío de correo electrónico**

Cuando se complete la migración, la instancia de Campaign tendrá direcciones IP de envío completamente distintas. Con el fin de garantizar una transición sin problemas, Adobe implementará una ampliación de las nuevas direcciones IP de envío cambiando progresivamente el tráfico de las direcciones IP antiguas a las nuevas.

**IP de integración de datos**

La integración de datos en el lado del cliente puede verse afectada por el cambio de direcciones IP para la integración de datos. El cambio puede afectar a ambas direcciones, dependiendo de si Campaign actúa como servidor o como cliente.
Casos habituales:

* SFTP, posiblemente ambas direcciones
* HTTP, posiblemente ambas direcciones
* SMPP (conexión con el proveedor de SMS), Campaign como cliente, cambio de la IP de origen

En general, esto significa que el cliente debe comprobar las posibles restricciones IP establecidas en sus servidores de seguridad y adaptarlas en consecuencia.*

**Servidores de Campaign**

Los servidores de Campaign existentes (contenedores) se moverán a la nube pública (AWS) con un enfoque &quot;lift-and-shift&quot;. Es decir, no se necesitará una nueva instalación del servidor, pero todo el servidor se transferirá al nuevo centro de datos. La operación no requerirá más trabajo que una reconfiguración técnica de bajo nivel.

**Nombres de servidor**

En los subdominios utilizados para la comunicación de marketing: seguirán siendo los mismos. Sin embargo, según la implementación, es posible que haya que hacer alguna cosa en el lado del cliente:

* Si se produce una delegación de subdominios (el caso habitual), Adobe se encargará de todos los cambios y garantizará una transición sin problemas
* En caso de configuración de CNAME (excepción), se solicitará al cliente que implemente los cambios. Será necesaria la coordinación con Adobe.

Para el acceso de los usuarios y la integración de datos, los nombres de neolane.net no cambiarán.

Esto significa que el cambio será transparente para los usuarios y las implementaciones de integración de datos, si los nombres de los servidores no fueron reemplazados por direcciones IP no codificadas.

### Preparación

**IP de envío de correo electrónico**

En primer lugar, la Capacidad de entrega de Adobe evaluará el estado de entrega de la plataforma y recomendará un plan para el cambio a las nuevas IP.

El Adobe proporcionará el mismo número de IP en el nuevo centro de datos.

La ampliación de nuevas direcciones IP puede comenzar en cuanto se aprovisionan las nuevas.

**Limpieza de aplicaciones**
La transferencia de datos entre centros de datos se encuentra en la ruta crítica del tiempo de inactividad.

Los datos se almacenan de dos maneras:

1. De lejos, la base de datos más importante
1. Archivos en el servidor de aplicaciones (importación y exportación de datos)

Reducir el tamaño de la base de datos es muy importante para acelerar la transferencia de datos.

Sugerencias:

* Reduzca los períodos de retención de datos históricos (registros de entrega, registros de seguimiento, etc.)
* Eliminar registros inútiles en otras tablas (entregas, destinatarios, tablas personalizadas)

### Ejecución

**Pausar ejecuciones**

Recomendamos reducir la velocidad y pausar todas las ejecuciones justo antes de cerrar la aplicación en el centro de datos heredado: entregas y flujos de trabajo. Esto facilitará el reinicio en la nube pública (AWS), ya que se habrá dado tiempo a los procesos para pausar &quot;correctamente&quot; y guardar cualquier estado de ejecución en curso.

**Durante la migración**

Mientras se produce la migración, solo seguirá funcionando un servicio: Redirección de vínculos de correo electrónico. Es decir, todos los destinatarios podrán llegar a la página de destino cuando hagan clic en un mensaje de correo electrónico. Sin embargo, no se registrarán estos clics, por lo que las tasas de clics de las entregas que se iniciaron poco antes de que la migración serán inferiores a las habituales.

**Restart**

Una vez migrada al nuevo entorno, la aplicación se reiniciará de forma progresiva:

* Acceso a la primera consola, para que los usuarios puedan comprobar el estado sin que nada se encuentre ejecutándose en ese momento
* A continuación, flujos de trabajo y entregas

### Posterior a la migración

**Eliminación de instancias en el centro de datos heredado**

Una vez completada la migración de la aplicación, no hay ningún plan para volver a ejecutar procesos en el centro de datos heredado. Esperamos que toda la información del centro de datos heredado se pueda borrar, excepto con fines de copia de seguridad temporal, hasta que los procesos de copia de seguridad programados se hayan ejecutado en la nube pública (AWS).

**Delegación de DNS**

Normalmente, el dominio utilizado para enviar correo electrónico (empieza a la derecha del signo @ en la dirección de error) desde Campaign se ha delegado a Adobe. La delegación puede cambiarse e implementarse hacia los servidores DNS de AWS.


## Asistencia y otros vínculos útiles{#support}

* [Preguntas frecuentes sobre la migración a Adobe Managed Services (Nube pública)](dc-migration-faq.md)
* [Actualizaciones anuales de Campaign](../../rn/using/rn-overview.md)
* [Preguntas frecuentes sobre la actualización de versiones](../../platform/using/faq-build-upgrade.md)
