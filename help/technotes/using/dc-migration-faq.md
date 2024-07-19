---
product: campaign
title: Preguntas frecuentes sobre la migración a Adobe Managed Services (Nube pública)
description: Preguntas frecuentes sobre la migración de Campaign Classic a la nube pública
feature: Technote, Upgrade
role: User
level: Beginner
exl-id: a9cd08b0-55c2-4405-9fb8-f0c623cd4ccb
source-git-commit: 6803b6628313db9108a191fd143dac68ee799149
workflow-type: tm+mt
source-wordcount: '2225'
ht-degree: 40%

---

# Preguntas frecuentes sobre la migración a la nube pública{#dc-faq}



Adobe retira del servicio el centro de datos heredado: las instancias de Campaign Classic deben transferirse a la nube pública de Amazon Web Service (AWS). [Más información sobre esta iniciativa](dc-migration.md).

A continuación se muestra un conjunto de preguntas comunes sobre este proyecto, el impacto en los entornos de Campaign y otros recursos útiles.

Para cualquier otra pregunta, puede contactar con el [Servicio de atención al cliente de Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).

## Impacto de la infraestructura

![](assets/do-not-translate/database.png)

A continuación se enumeran los efectos globales en la base de datos e infraestructura.

* **¿Cambiará la base de datos? ¿Cuál es la versión de la nueva base de datos? ¿Qué sistema operativo se utilizará?**

  Adobe se reserva el derecho de elegir e implementar el motor de administración de bases de datos más adecuado para ofrecer el servicio de Adobe Campaign en condiciones óptimas.

  Además, para mantener el mejor nivel de seguridad, Adobe no proporcionará información detallada relacionada con la infraestructura.

* **¿Existe riesgo de pérdida de datos?**

  La base de datos se descargará del centro de datos heredado y se restaurará en la nube pública (AWS). Cuando se reinicia en el nuevo centro de datos, la aplicación se reanudará desde el estado exacto en que estaba antes de la migración. Los usuarios no verán ninguna diferencia, excepto que algunas tareas programadas se habrán retrasado.

* **¿Hay alguna diferencia en el tamaño del paquete entre el centro de datos heredado y la nube pública?**

  Estamos aprovisionando la nube pública (AWS) con nuevas definiciones de paquetes basadas en el tamaño de la base de datos actual, el tamaño del disco, etc. Por ejemplo, si un cliente tiene un servidor de aplicaciones en centros de datos heredados, puede tener dos servidores de aplicaciones en la nube pública (AWS) basados en definiciones de paquetes.

* **¿Va a cambiar el número de compilación o la versión de la campaña?**

  Como primer paso, vamos a mantener la misma compilación de Campaign Classic con la migración.

  En un paso adicional, procederemos a actualizar a la última versión de Campaign Classic GA. Para obtener más información, consulte [esta página](../../rn/using/rn-overview.md).

* **¿Cuál es el plan para abordar cualquier problema posterior a la migración?**

  Se realizarán pruebas exhaustivas antes de que se migraran los sistemas de producción. Sin embargo, en caso de problemas, [el Servicio de atención al cliente de Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support) seguirá siendo el principal punto de contacto. El Adobe ha creado un equipo de expertos para proporcionar asistencia avanzada, si es necesario.

## Impacto de la capacidad de entrega

![](assets/do-not-translate/features.png)

A continuación, se detalla el impacto global en las direcciones IP, la lista de bloqueados, subdominios y direcciones URL.

* **¿Cómo se gestionará la dirección IP en la lista de permitidos? ¿Necesitarán los clientes agregar nuevas direcciones IP a la lista de permitidos para el tráfico entrante de Campaign?**

  La dirección IP de los servidores de Adobe cambiará. Por lo tanto, es posible que los clientes tengan que agregar esas nuevas direcciones IP a la lista de permitidos de su sistema.

  [Más información](#config) sobre la dirección IP en la lista de permitidos.

* **¿Cómo administraremos el puerto agregado a la lista de permitidos para el acceso SFTP/FTP?**

  La configuración de SFTP (claves públicas + IP en la lista de permitidos) también se moverá del centro de datos heredado a la nube pública (AWS). El cliente no tiene que hacer nada más.

* **¿Estamos cambiando las direcciones IP?**

  La dirección IP de los servidores de Adobe cambiará. Por lo tanto, es posible que los clientes tengan que agregar esas nuevas direcciones IP a la lista de permitidos de su sistema.

  [Más información](#config) sobre la dirección IP en la lista de permitidos.

* **¿Cómo se gestionará la delegación de subdominios?**

  Los subdominios existentes se moverán del centro de datos heredado a la nube pública (AWS). Este artículo será gestionado por el equipo de entrega de Adobe como parte del proceso de migración.

  >[!NOTE]
  >
  >La participación del equipo de entregabilidad se basa en el contrato y los clientes deben ponerse en contacto con su representante de Adobe para obtener información relacionada con la participación en la entregabilidad.

  Adobe guiará al cliente a través de las pruebas necesarias para garantizar que la configuración se esté ejecutando en los nuevos servidores de la nube pública (AWS) después de la migración.

* **¿Generará la migración nuevas direcciones URL para el seguimiento, los recursos y las aplicaciones web?**

  No, conservaremos las direcciones URL existentes.

* **¿Habrá un cambio en el subdominio de Neolane.net a campaign.adobe.com?**

  Tanto `neolane.net` como `campaign.adobe.com` estarán en su lugar después de la migración. Para hacerlo simple: redireccionaremos neolane.net a nuevas instancias en la nube pública (AWS), por lo que no se requieren cambios por parte del cliente.

* **¿Cuál es el plan para el calentamiento de IP?**

  En primer lugar, la Capacidad de entrega de Adobe evaluará el estado de entrega de la plataforma y recomendará un plan para el cambio a las nuevas IP

  No se requiere calentamiento después de la migración. Podría ser una excepción y, en ese caso, [el Servicio de atención al cliente de Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support) se pondrá en contacto con los clientes.

  Sin embargo, el plan es hacer que esta operación sea transparente para el negocio, a diferencia de la mejora inicial que se realiza durante el lanzamiento.

  Cuando se complete la migración, la instancia de Campaign tendrá direcciones IP de envío completamente distintas. Con el fin de garantizar una transición sin problemas, Adobe implementará una ampliación de las nuevas direcciones IP de envío cambiando progresivamente el tráfico de las direcciones IP antiguas a las nuevas.

* **¿Nos movemos sobre la dirección URL en la lista de permitidos?**

  Sí, esto se almacena en el archivo de configuración del servidor que se copiará del origen a la nueva instancia.

* **¿Cuál debería ser el impacto con nuestro subdominio delegado que usamos para personalizar nuestra comunicación?**

  Los subdominios utilizados para la comunicación de marketing siguen siendo los mismos. Sin embargo, según la implementación, es necesario realizar acciones en el lado del cliente:
   * En caso de delegación de subdominios al Adobe (predeterminado), el Adobe se encarga de todos los cambios y garantiza una transición sin problemas.
   * En caso de configuración de CNAME (excepción), se solicita al cliente que implemente los cambios en coordinación con el Adobe.

## Impacto en la configuración y la conectividad

![](assets/do-not-translate/maintenance.png)

### Nota sobre la dirección IP en la lista de permitidos{#config}

La migración a la nube pública incluirá nuevas direcciones IP para los servidores de aplicaciones de Adobe Campaign, de modo que el cambio de la dirección IP puede afectar a la conectividad entre los servidores de Adobe y sus sistemas de información.

![](assets/migration.png)

Consideremos los dos casos :

* Tráfico entrante: Toda la actividad de red que se inicia desde sus sistemas o desde un tercero en los servidores de Adobe Campaign. La configuración será gestionada por Adobe y, a continuación, se copiará de la nube heredada a la nube pública durante la migración. A continuación, la conectividad para el tráfico entrante se conservará tal cual después de la migración y no se espera ninguna acción por parte del cliente

* Tráfico saliente: Toda la actividad de red iniciada por los servidores de Adobe Campaign en su sistema de información o en cualquier otro sistema de terceros (por ejemplo: un proveedor de SMS). Según las políticas de seguridad implementadas en su organización, el cambio de direcciones IP puede requerir la operación de lista de permitidos desde el sistema de información o desde otro sistema de terceros

### Impactos globales

A continuación se enumeran los efectos globales en la configuración, conectividad con otros sistemas y productos, API y zona horaria.

* **¿Afectará la migración a la conectividad con cuentas externas?**

  Sí. Las integraciones de terceros como, por ejemplo, los proveedores de SMS, deben agregar nuevas direcciones IP de servidores de aplicaciones Adobe Campaign a la lista de permitidos.

* **¿Afectará la migración a la conectividad con Adobe Analytics mediante el conector de Genesis? ¿Qué sucede si se agregan direcciones IP de Campaign a la lista de permitidos del lado de Adobe Analytics?**

  Las direcciones IP de los servidores de aplicaciones de Adobe Campaign cambiarán. Este paso será gestionado por el Servicio de atención al cliente de Adobe después de la migración.

* **¿Afectará la migración a la conectividad con otras soluciones de Adobe AEM (, Target, etc.)?**

  Las integraciones son una combinación de direcciones IP declaradas en la configuración de cuenta de la lista de permitidos y el servicio web. Esto se contabilizará y será propiedad del Servicio de atención al cliente de Adobe.

  Habrá direcciones IP en la lista de permitidos que serán necesarias en la solución externa, ya que la IP de los servidores de aplicaciones cambiará. Se proporcionará esta información. Otras partes de la integración están basadas en IMS y deben funcionar tal cual.

* **¿Qué sucede con los clientes que no están conectados a la integración de ID de organización para IMS?**

  A los clientes que no tengan IMS se les proporcionará uno. Se adjuntará un ID de organización a su instancia.

* **¿La migración afecta a las configuraciones de varias marcas?**

  Tan pronto como el subdominio y toda la configuración relacionada se muevan o redirijan correctamente desde el centro de datos heredado a la nube pública (AWS), no debemos esperar ningún problema.

* **¿Se ve afectada la conectividad de API por la migración?**

  La dirección IP de los servidores de Adobe cambiará. Por lo tanto, es posible que los clientes tengan que agregar esas nuevas direcciones IP a la lista de permitidos de su sistema.

  [Más información](#config) sobre la IP en la lista de permitidos.

* **¿Nos aseguraremos de que todos los parámetros de configuración de memoria de JavaScript se establezcan correctamente después de la migración?**

  Se copiará la configuración de instancias del centro de datos heredado a la nube pública (AWS), de modo que estos valores se conservarán tras la migración.

* **¿Existe algún riesgo para el acceso a ciertas extensiones de archivo?**

  Es posible que el cliente desee permitir que los archivos de fuente y los archivos de la reunión de Outlook se carguen en la carpeta de recursos públicos. Esta configuración se realiza en el archivo `config-<instance>.xml` actual. Esto se copiará junto a los archivos de configuración.

* **¿Cambiará la zona horaria en el nuevo servidor? ¿Podrá el cliente mantener su huso horario actual?**

  Puede cambiar según la nueva ubicación de los servidores. Sin embargo, el cliente podrá conservar su huso horario actual.

  [Más información](../../workflow/using/managing-time-zones.md) acerca de la administración de huso horario en Adobe Campaign Classic v7.


## Seguridad y permisos

![](assets/do-not-translate/security.png)

Con esta migración a la nube pública (AWS), los entornos de los clientes se mantendrán actualizados con todos los requisitos de seguridad necesarios. Esto incluye:

* Revisiones periódicas de seguridad y SO más recientes
* Aislamiento de la infraestructura por cliente
* Revisiones de seguridad y auditoría administradas para admitir la infraestructura de nube, como equilibradores de carga, reglas de seguridad de red y cifrado de almacenamiento.

A continuación se enumeran los efectos en los permisos, certificados y acceso al SFTP.

* **¿Se van a mover todos los certificados a los nuevos servidores?**

  Sí, todos los certificados se moverán como parte de esta migración.

* **¿Necesitamos solicitar nuevas claves de acceso STP al cliente?**

  No, el Adobe copiará las claves de acceso SFTP como en el nuevo servidor.

* **¿Cómo se administran los permisos de SFTP?**

  Garantizamos que el nuevo servidor SFTP, los usuarios, directorios y archivos tengan exactamente los mismos niveles de permisos.

* **Si no se pudo establecer la conexión SFTP, ¿cuál es la solución o plan para mantener al cliente en funcionamiento?**

  El único problema de conectividad que puede surgir se relaciona con la lista de permitidos del lado del cliente. El cliente debe agregar esta prueba en un entorno que no sea de producción para asegurarse de que funciona antes de pasar a producción.

* **¿Hay alguna configuración de lista de permitidos específica del centro de datos que necesite utilizar?**

  No, no hay ninguna configuración de lista de permitidos específica del centro de datos que se deba administrar.

* **¿Nos aseguramos de que los scripts personalizados se ejecuten correctamente en el nuevo entorno?**

  La implementación del cliente puede utilizar secuencias de comandos personalizadas (Perl/Shell/Python/JavaScript) en flujos de trabajo para, por ejemplo, manipular archivos y carpetas.

  En la instancia alojada, las secuencias de comandos solo se ejecutan mediante el motor de JavaScript. Estas implementaciones específicas pueden provocar lagunas de seguridad y problemas posteriores a la actualización. No son compatibles.

* **Con la integración de IMS, ¿funcionará como hasta ahora en una nueva instancia o se necesitará alguna actualización de configuración adicional?**

  Como mantenemos los mismos nombres de DNS, debería funcionar como después de la migración.


## Ejecución de la migración

![](assets/do-not-translate/upgrades.png)

El impacto global durante la migración se enumera a continuación.

* **¿Es necesario planificar la detención de la actividad de marketing durante la migración?**

  Adobe recomienda reducir la velocidad y pausar todas las ejecuciones justo antes de cerrar la aplicación en el centro de datos heredado: entregas y flujos de trabajo. Esto facilitará el reinicio en el servidor en la nube (AWS), ya que se habrá dado tiempo a los procesos para pausar &quot;correctamente&quot; y guardar cualquier estado de ejecución en curso.

* **¿Esperamos tiempo de inactividad de nuestro servicio Adobe Campaign?**

  Es inevitable que la migración conlleve algo de tiempo de inactividad. El objetivo de este plan es guiar para minimizar este tiempo de inactividad.

  La transferencia entre centros de datos se encuentra en la ruta crítica del tiempo de inactividad. Los datos se almacenan de dos maneras:

   * De lejos, la base de datos más importante
   * Archivos en el servidor de aplicaciones (importación y exportación de datos)

  Reducir el tamaño de la base de datos es muy importante para acelerar la transferencia de datos. Sugerencias:

   * Reduzca los períodos de retención de datos históricos (registros de entrega, registros de seguimiento, etc.)
   * Eliminar registros inútiles en otras tablas (entregas, destinatarios, tablas personalizadas)

* **¿Cuál es el tiempo de inactividad estimado para migrar una instancia?**

  El tiempo de inactividad depende totalmente del tamaño de la base de datos del cliente y de los tamaños de almacenamiento de archivos SFTP. Contacte con el Servicio de atención al cliente para obtener una duración estimada.

* **Qué sucede con los mensajes enviados desde el servidor heredado. ¿Los vínculos siempre serán accesibles?**

  Mientras se esté ejecutando la migración, solo un servicio seguirá funcionando: Redirección de vínculos de correo electrónico. Todos los destinatarios podrán llegar a la página de destino cuando hagan clic en un mensaje de correo electrónico. Sin embargo, no se rastrearán estos clics, por lo que las tasas de clics de los envíos que se iniciaron poco antes de que la migración serán inferiores a las habituales.

* **¿Qué sucede con los entornos intermediarios/RT?**

  El abastecimiento de MID y RT se gestiona como cualquier otra infraestructura alojada.

* **¿En qué orden se realizarán las migraciones?**

  Los entornos se migrarán en el siguiente orden:

   1. Entornos de desarrollo
   1. Entornos de ensayo
   1. Entornos de producción
   1. Entornos RT
   1. Entornos de intermediario

* **¿Cuál es el plan de reversión?**

  El plan de reversión es volver a cambiar el DNS y establecer la base de datos de origen desde solo lectura a lectura-escritura. Con el tiempo, conseguiremos hacerlo de manera automática.

* **Después de la migración, ¿aún podemos acceder a instancias antiguas?**

  Una vez completada la migración de la aplicación, no hay ningún plan para volver a ejecutar procesos en el centro de datos heredado. Esperamos que toda la información del centro de datos heredado se pueda borrar, excepto con fines de copia de seguridad temporal, hasta que los procesos de copia de seguridad programados se hayan ejecutado en la nube pública (AWS).

* **¿Cuánto tiempo se permitirá probar cada instancia después de la migración a la nube pública?**

  Según la complejidad del cliente, se requiere un tiempo de procesamiento mínimo de 1 semana entre el entorno de ensayo y las migraciones al entorno de producción.

* **¿Quién administrará la adición de nuevas direcciones IP a la lista de permitidos?**

  El equipo del Servicio de atención al cliente de Adobe se encargará de garantizar que el cliente y los terceros puedan acceder al nuevo sistema añadiendo nuevas IP a la lista de permitidos.

## Asistencia y otros vínculos útiles{#support}

* [Migración a Adobe Managed Services (Nube pública)](dc-migration.md)
* [Actualización anual de Campaign](../../rn/using/rn-overview.md#yeary-upgrade)
* [Preguntas frecuentes sobre la actualización de versiones](../../platform/using/faq-build-upgrade.md)
