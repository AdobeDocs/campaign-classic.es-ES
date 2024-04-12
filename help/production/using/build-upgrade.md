---
product: campaign
title: Introducción a las actualizaciones de versiones
description: Conozca los pasos clave para actualizar a una nueva compilación
feature: Monitoring, Upgrade
badge-v7-prem: label="On-Premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: c5a9c99a-4078-45d8-847b-6df9047a2fe2
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 2%

---

# Realización de una actualización de versión{#performing-a-build-upgrade}



En esta sección se proporciona una guía detallada sobre el proceso de actualización y los pasos para identificar y resolver conflictos.

La mejora de la construcción debe llevarse a cabo con precaución, sus impactos deben ser considerados de antemano y el procedimiento debe completarse con un alto nivel de disciplina. Para garantizar que la actualización se realice correctamente, asegúrese de que solo los usuarios expertos realizan los pasos descritos a continuación. Además, recomendamos encarecidamente ponerse en contacto con [Adobe del Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) antes de iniciar cualquier actualización.

Se necesitan los siguientes requisitos previos:

* Comprensión de la arquitectura de Campaign
* Conocimientos sobre sistemas y servidores
* Derechos y permisos administrativos

Puede encontrar más información en estas secciones: [Actualización de Adobe Campaign](../../production/using/upgrading.md), [Migración a una nueva versión](../../migration/using/about-migration.md).

Para las instancias alojadas e híbridas, debe solicitar la actualización de la compilación al equipo de operaciones técnicas de Adobe. Para obtener más información, consulte la sección Preguntas más frecuentes en la parte inferior de esta página. Consulte también la [preguntas frecuentes sobre actualización de compilación](../../platform/using/faq-build-upgrade.md).

## Preparación de la actualización

![](assets/do-not-localize/icon_planification.png)

Antes de iniciar la actualización de la compilación, debe realizar una preparación completa como se describe a continuación.
Una vez que el sistema esté listo para actualizarse, se requiere una actualización de la compilación **al menos** 2 horas.

El proceso de actualización de la compilación requiere los siguientes recursos:

* un arquitecto de Adobe: para comprender las estructuras de la base de datos (esquemas predeterminados y cualquier esquema adicional que se haya agregado, diseños de campaña y cualquier funcionalidad de ruta crítica que se deba iniciar y probar en un orden específico).
* un jefe de proyecto: en caso de que la actualización de la compilación implique muchas instancias diferentes (producción, ensayo y pruebas) y otros servidores y aplicaciones de terceros (bases de datos, sitios SFTP, proveedores de servicios de mensajería), se considera una práctica recomendada disponer de un jefe de proyecto para coordinar todas las pruebas.
* un administrador de Adobe Campaign: el administrador conoce la configuración del servidor, incluidos, entre otros, los requisitos de seguridad, diseño de carpetas, creación de informes e importación y exportación. No realice una actualización de compilación sin su administrador.
* un operador de Adobe Campaign (usuario de marketing): una actualización correcta depende de la capacidad del usuario para realizar correctamente sus tareas diarias. Por este motivo, incluya siempre al menos uno de los operadores diarios en las pruebas de los servidores actualizados.

### Planificación

Estos son los puntos clave sobre cómo planificar una actualización de compilación:

1. Reserve al menos 2 horas para la actualización.
1. Distribuya los datos de contacto para el Adobe y el personal del cliente.
1. Para instancias alojadas: el personal del Adobe y del cliente coordinará el tiempo de la actualización y quién la ejecutará.
1. Para instancias locales: el personal del cliente gestiona todo el proceso. Si se necesita asistencia para probar flujos de trabajo personalizados y lógica de entrega, se deben incluir servicios de consultoría.
1. Determine y confirme a qué versión de Adobe Campaign desea actualizar: consulte la [Notas de la versión de Adobe Campaign Classic](../../rn/using/rn-overview.md).
1. Confirme la posesión de ejecutables de actualización.

### Personas clave

El proceso de actualización de la compilación requiere la participación de las siguientes personas:

* arquitecto de Adobe: para las arquitecturas alojadas o híbridas, el arquitecto debe coordinarse con el servicio de atención al cliente de Adobe Campaign.

* Gestor de proyecto:
   * para instalaciones locales: el jefe de proyecto interno del cliente dirige la actualización y gestiona las pruebas del ciclo vital.

   * para instalaciones alojadas: el equipo de alojamiento se asociará con el equipo de Atención al cliente de Adobe Campaign y el cliente para coordinar la cronología de actualización de todas las instancias.

* Administrador de Adobe Campaign:
   * para instalaciones locales: el administrador realiza la actualización.

   * para instalaciones alojadas: el equipo de alojamiento realiza la actualización.

* Adobe Campaign operator\marketing user: el operador ejecuta pruebas en instancias de desarrollo, prueba y producción.

### Preparación de la actualización de compilación

Antes de iniciar la actualización de la compilación, los clientes locales deben realizar la siguiente preparación:

1. Asegúrese de que cualquier trabajo de desarrollo se pueda exportar antes de la actualización y exporte como paquetes.

1. Realizar una copia de seguridad completa de las bases de datos para todas las instancias de los entornos de origen y destino.

1. Obtenga la versión más reciente de su [archivo de configuración del servidor](../../installation/using/the-server-configuration-file.md).

1. [Descargar la última versión](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html). [Más información](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=es).

También necesita conocer todos los [líneas de comandos útiles](../../installation/using/command-lines.md) antes de iniciar una actualización de compilación:

* **nlserver pdump**: enumera los procesos en ejecución
* **nlserver pdump -who**: enumera las sesiones de cliente activas
* **Falta el monitor nlserver.**: faltan propiedades en la lista
* **nlserver start process@instance-name**: inicia un proceso
* **nlserver stop process@instance-name**: detiene un proceso
* **nlserver restart process@instance-name**: reinicia un proceso
* **apagado de nlserver**: detiene todos los procesos de Campaign
* **nlserver watchdog -svc**: inicia el vigilante (solo UNIX)

## Realización de la actualización

![](assets/do-not-localize/icon_process.png)

Los procedimientos siguientes solo los realiza **on-premise** clientes. Para los clientes alojados, el equipo de alojamiento se encarga de ello. A continuación se describe el procedimiento detallado para actualizar Adobe Campaign a una nueva versión.

### Duplicación del entorno

Así se duplica un entorno de Adobe Campaign para restaurar un entorno de origen en un entorno de destino, lo que da como resultado dos entornos de trabajo idénticos.

Para realizar esto, siga los pasos a continuación:

1. Cree una copia de las bases de datos en todas las instancias del entorno de origen.

1. Restaure estas copias en todas las instancias del entorno de destino.

1. Ejecute el **nms:congelaciónInstance.js** script de cauterización en el entorno de destino antes de iniciarlo. Esto detendrá todos los procesos que interactúan con el exterior: registros, seguimiento, envíos, flujos de trabajo de campaña, etc.

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. Compruebe la cauterización como se indica a continuación:

   * Compruebe que la única parte del envío sea la que tenga el ID establecido en. **0**:

     ```
     SELECT * FROM neolane.nmsdeliverypart;
     ```

   * Compruebe que la actualización del estado de entrega sea correcta:

     ```
     SELECT iSate, count(*) FROM neolane.nmsdeliveryGroup By iProd;
     ```

   * Compruebe que la actualización del estado del flujo de trabajo sea correcta:

     ```
     SELECT iState, count (*) FROM neolane.xtkworkflowGROUP BY iState;
     SELECT iStatus, count (*) FROM neolane.xtkworkflowGROUP BY iStatus;
     ```

### Cerrar servicios

Para reemplazar todos los archivos con la nueva versión, es necesario cerrar todas las instancias del servicio nlserverservice.

1. Cierre los siguientes servicios:

   * Servicios Web (IIS): **iisreset /stop**
   * Servicio de Adobe Campaign: **net stop nlserver6**

   >[!NOTE]
   >
   >Asegúrese de que el servidor de redirección (webmdl) esté detenido para que el archivo nlsrvmod.dll utilizado por IIS pueda reemplazarse por la nueva versión.
   >

1. Valide que no haya tareas activas ejecutando la variable **nlserver pdump** comando. Si no hay tareas, el resultado debe ser similar al siguiente:

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. Compruebe el Administrador de tareas de Windows para confirmar que se han detenido todos los procesos.

### Actualizar la aplicación de Adobe Campaign Server

1. Ejecute el **Setup.exe** archivo. Si necesita descargar este archivo, acceda a [el Centro de descargas](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html).

1. Seleccione el modo de instalación: **Actualizar** o **Reparar**.

1. Haga clic en **Next**.

1. Clic **Finalizar**: el programa de instalación copia los nuevos archivos.

1. Una vez finalizada la operación, haga clic en **Finalizar**.

### Sincronización de recursos

1. Abra la línea de comandos.

1. Ejecutar **nlserver config -postupgrade -allinstances** para realizar lo siguiente:

   * Sincronización de recursos
   * Actualización de esquemas
   * Actualizar la base de datos

   >[!NOTE]
   >
   >Esta operación solo debe realizarse una vez y solo en un servidor de aplicaciones nlserverweb.
   >

   Para sincronizar solo una base de datos, ejecute el siguiente comando:

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. Compruebe si la sincronización ha generado errores o advertencias.

### Reiniciar servicios

Es necesario reiniciar los siguientes servicios:

* Servicios Web (IIS): **issreset /start**
* Servicio de Adobe Campaign: **net start nlserver6**

### Actualización de consolas de cliente

La consola de cliente debe tener la misma compilación como instancia de servidor.

En el equipo donde está instalado el servidor de aplicaciones de Adobe Campaign (nlserverweb), descargue y copie el archivo:

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

La próxima vez que se conecten las consolas de cliente, una ventana informará a los usuarios sobre la disponibilidad de una nueva actualización y les ofrecerá la posibilidad de descargarla e instalarla.

### Tareas adicionales específicas

Algunas configuraciones requieren tareas adicionales específicas para actualizarse a una nueva compilación.

#### Mensajería transaccional

Cuando la mensajería transaccional (centro de mensajes) está habilitada en la instancia de Campaign, debe realizar estos pasos adicionales para actualizar:

1. Actualice el servidor de producción del Centro de mensajes a la versión elegida.
1. Ejecute los scripts posteriores a la actualización.
1. Ejecute pruebas y asegúrese de que los correos electrónicos se reciben correctamente a través de la instancia de producción del Centro de mensajes.
1. Actualizar clientes y borrar la caché.
1. Exportar paquetes:
   * Exportación de paquetes mediante la herramienta de exportación de paquetes de cliente
   * Importar paquete de esquema
   * Desconexión y reconexión del cliente
   * Actualizar base de datos
   * Desconectar y volver a conectar
   * Importar paquete de administración
   * Importar paquete de contenido
   * Importar paquete de Content Management
   * Desconectar y volver a conectar
   * Realizar una comprobación rápida de los flujos de trabajo

1. Publique las plantillas del Centro de mensajes para asegurarse de que la interfaz entre los servidores y la instancia del Centro de mensajes funcione.
1. Ejecute pruebas para asegurarse de que los correos electrónicos se reciben correctamente a través de la instancia de producción del Centro de mensajes.
1. Ejecute pruebas de flujo de trabajo en producción para asegurarse de que se reciben los envíos.

#### Intermediario

En el contexto de un entorno de intermediario, debe realizar estos pasos adicionales para actualizar:

1. Contacto [Adobe del Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para coordinar la actualización del servidor intermediario.
1. Compruebe que la versión se ha actualizado ejecutando un vínculo de prueba. Por ejemplo:

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>El servidor intermediario siempre debe ejecutar la misma versión (o más reciente) que para los servidores de marketing.
>

## En caso de conflictos

### Identificar conflictos

Debe comprobar el resultado de la sincronización. Este procedimiento solo lo realizan los clientes locales. Para los clientes alojados, el equipo de alojamiento se encarga de ello. Existen dos formas de ver el resultado de la sincronización:

En la interfaz de línea de comandos, los errores se materializan mediante un corchete triple &#39;>>&#39; y la sincronización se detiene automáticamente. Las advertencias se materializan mediante comillas angulares dobles &#39;>>&#39; y deben resolverse una vez completada la sincronización. Al final de la posactualización, se muestra un resumen en el símbolo del sistema. Puede tener este aspecto:

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

Si la advertencia se refiere a un conflicto de recursos, se requiere la atención del usuario para resolverlo.

El **postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** contiene el resultado de la sincronización. Está disponible de forma predeterminada en el siguiente directorio: **installationDirectory/var/`<instance-name>`/postupgrade**. Los errores y las advertencias se indican mediante los atributos de error y advertencia.

### Analizar conflictos

**¿Cómo se encuentra un conflicto?**

Los conflictos se pueden encontrar dentro del archivo postupgrade.log en el servidor en cuestión o en la interfaz de cliente de Campaign (Administration > Configuration > Package management > Edit conflicts).

El documento con el identificador &quot;stockOverview&quot; y el tipo &quot;nms:webApp&quot; entran en conflicto con la nueva versión.

Si se encuentra un conflicto, compruebe si coinciden las siguientes condiciones:

* ¿El cliente ha modificado o personalizado el objeto?
* ¿Ha cambiado el objeto en el producto?

Si no se aplica ninguna de estas condiciones, se trata de un falso positivo. Si se aplican ambas condiciones, se ha encontrado un conflicto real.

**¿El cliente ha modificado el objeto?**

1. Identifique el objeto en conflicto.
1. Pregunte al cliente si ha modificado el objeto.
1. ¿Hay algo inusual con el objeto?
1. ¿Se ha definido la fecha de la última modificación en el código del objeto?
1. Examine el código XML del conflicto para ver los atributos &quot;_conflicts&quot;. ¿Tiene el aspecto de una personalización?

**¿Se ha cambiado el objeto en la nueva compilación?**

1. ¿Algún &quot;sospechoso habitual&quot;? Informes o aplicaciones web integradas (por ejemplo: &quot;deliveryValidation&quot;, &quot;deliveryOverview&quot;, &quot;budget&quot;).
1. Examine los registros de cambios para ver si hay actualizaciones.
1. Consulte a los expertos de Adobe Campaign.
1. Realice una &quot;diferenciación&quot; en el código.

### Resolver un conflicto

Para resolver conflictos, siga el siguiente proceso:

1. En el explorador de Adobe Campaign, vaya a **Administration > Configuration > Package management > Edit conflicts**.

1. Seleccione el conflicto que desee resolver en la lista.
Existen tres opciones para resolver conflictos: **Aceptar la nueva versión**, **Mantener la versión actual**, **Combine el código (y declare como resuelto)**, **Ignorar el conflicto (no recomendado)**.

**¿Cuándo puedo aceptar la nueva versión?**

* Si desea las funciones estándar.
* Si no tiene personalizaciones (se eliminarán todas)

**¿Cuándo puedo mantener la versión actual?**

* Si tiene personalizaciones
* Si no desea realizar la combinación
* Si no necesita ninguna corrección en el objeto en conflicto de la actualización

**¿Cuándo se debe realizar una combinación?**

* Solo se pueden combinar formularios, informes y aplicaciones web.
* Algunas combinaciones menores se pueden resolver sin comprender el código.
* Las combinaciones más complejas deben ser realizadas por alguien con las habilidades y capacidades adecuadas.
* Consulte [Realización de una combinación](#perform-a-merge).

**¿Qué pasa si ignoro los conflictos?**

* El conflicto se mantendrá
* El objeto no se actualizará
* Impactos a largo plazo: incompatibilidades de la versión, el cliente no se beneficiará de las correcciones de errores.

>[!IMPORTANT]
>Es muy recomendable resolver conflictos.
>

### Realización de una combinación{#perform-a-merge}

Existen diferentes tipos de combinaciones:

1. Fácil combinación: los elementos personalizados y nuevos son pequeños y no están relacionados, y no se requiere codificación.
1. Sin cambios: aceptar nueva versión, solo se cambió la fecha de la última actualización, solo comentarios, pestañas, espacios o líneas nuevas. Ejemplo: guardado accidental.
1. Cambios triviales: solo cambió una línea. Ejemplo: xpathToLoad
1. Combinación compleja: cuando se requiere codificación. Se requieren habilidades de desarrollo. Consulte [Combinaciones complejas](#complex-merges).

#### ¿Cómo combinar?

1. Obtenga las tres versiones: la original, la nueva y la personalizada.
1. Ejecute una &quot;diferencia&quot; entre las versiones original y nueva.
1. Aísle los cambios.
1. Si no hay cambios, resuelva manteniendo la versión actual.

#### ¿Dónde encontrar el código?

1. El código integrado se almacena en archivos XML en la carpeta de conjuntos de datos. Busque el archivo XML que coincida con el objeto en conflicto. Ejemplo: installationDirectory\datakit\nms\fra\form\recipient.xml
1. Recupere la versión original: a través de la [Centro de descargas](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html) u otra instalación no actualizada del producto.
1. Recupere la nueva versión: a través de la [Centro de descargas](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html) o los archivos instalados del cliente.
1. Recupere la versión personalizada: recupere el código fuente del objeto desde el cliente de Campaign.

### ¿Cómo hacer una diferencia?

1. Instale un editor de texto o de combinación; por ejemplo, Notepad ++, AraxisMerge o WinMerge.
1. Abra el archivo original y el nuevo archivo en el editor.
1. Ejecute la comparación (compare los dos archivos).
1. Identifique cualquier diferencia.

### ¿Cómo combinar?

1. Comience desde la versión personalizada.
1. Aplique los cambios.
1. Resuelva el conflicto declarándolo como resuelto.
1. Compruebe si hay regresiones.

Si decide resolver el conflicto manualmente, siga este procedimiento:

1. En la sección inferior de la ventana, busque la variable **_Conflict_string_** para localizar las entidades con conflictos. La entidad instalada con la nueva versión contiene el nuevo argumento; la entidad que coincide con la versión anterior contiene el argumento personalizado.
1. Elimine la versión que no desee conservar. Elimine el **_Conflict_argument_** cadena de la entidad que está conservando.
1. Vaya al conflicto que ha resuelto. Haga clic en **Acciones** y seleccione **Declarar como resuelto**.
1. Guarde los cambios: el conflicto se ha resuelto.

#### Combinaciones complejas{#complex-merges}

1. Comprenda lo que hace el cambio: realizar ingeniería inversa de los cambios, examinar los registros de cambios y realizar un seguimiento con expertos en Adobe Campaign.
1. Decida qué hacer con el cambio.
1. Comprenda qué hacen las personalizaciones: aplicar ingeniería inversa a los cambios

Estos son los pasos para realizar una combinación compleja:

1. Copiar bits de código del conjunto de cambios
1. Pegar en la versión personalizada
1. Prueba de no regresión de la personalización
1. Prueba de la función de los cambios
1. Realizar prueba de aceptación de usuarios
1. Realizar en el entorno de prueba


>[!IMPORTANT]
>Se requieren habilidades de desarrollo para realizar combinaciones complejas.
>

**Temas relacionados**

* [Preguntas frecuentes sobre la actualización de versiones](../../platform/using/faq-build-upgrade.md)
* [Notas de la versión de Campaign Classic](../../rn/using/rn-overview.md)
* [Opciones de ayuda y asistencia de Campaign Classic](../../support.md)
* [Programa de actualización anual de Campaign](../../rn/using/rn-overview.md)
