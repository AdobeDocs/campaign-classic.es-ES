---
solution: Campaign Classic
product: campaign
title: Introducción a las actualizaciones de la compilación
description: Conozca los pasos clave para actualizar a una nueva compilación
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 0abdbbc33350cf6ec85488483dadb177e685818b
workflow-type: tm+mt
source-wordcount: '2355'
ht-degree: 3%

---


# Realización de una actualización de versión{#performing-a-build-upgrade}

Esta sección le proporcionará un tutorial detallado sobre el proceso de actualización y los pasos para identificar y resolver conflictos.

La mejora de la construcción debe llevarse a cabo con cautela, sus efectos deben ser objeto de un examen previo y el procedimiento debe completarse con un alto nivel de disciplina. Para garantizar una actualización correcta, asegúrese de que solo los usuarios expertos realicen los pasos descritos a continuación. Además, recomendamos encarecidamente ponerse en contacto con [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) antes de iniciar cualquier actualización.

Se necesitan los siguientes requisitos previos:

* Comprensión de la Arquitectura de Campaña
* Conocimientos de sistemas y servidores
* Derechos y permisos administrativos

Puede encontrar más información en estas secciones: [Actualizando Adobe Campaign](../../production/using/upgrading.md), [Migrando a una nueva versión](../../migration/using/about-migration.md).

En el caso de instancias hospedadas e híbridas, debe solicitar la actualización de la compilación al equipo de operaciones técnicas de Adobe. Para obtener más información sobre esto, consulte la sección Preguntas más frecuentes en la parte inferior si esta página. Consulte también las [preguntas frecuentes sobre la actualización de la compilación](../../platform/using/faq-build-upgrade.md).

## Preparación de la actualización

![](assets/do-not-localize/icon_planification.png)

Antes de iniciar la actualización de la compilación, debe realizar una preparación completa como se describe a continuación.
Una vez que el sistema está listo para ser actualizado, una actualización de la compilación tarda **al menos** 2 horas.

El proceso de actualización de la compilación requiere los siguientes recursos:

* un arquitecto de Adobe: para comprender las estructuras de la base de datos (esquemas listos para usar y cualquier esquema adicional que se haya agregado, diseños de campaña y cualquier funcionalidad de ruta crítica que se deba iniciar y probar en un orden específico).
* un jefe de proyecto: En el caso de que la actualización de la compilación involucre muchas instancias diferentes (producción, ensayo, pruebas) y otros servidores y aplicaciones de terceros (bases de datos, sitios SFTP, proveedores de servicio de mensajería), se considera una práctica recomendada contar con un administrador de proyectos para coordinar todas las pruebas.
* un administrador de Adobe Campaign: su administrador conoce la configuración del servidor, incluida, entre otras cosas: requisitos de seguridad, presentación de carpetas, sistema de informes e importación/exportación. No realice una actualización de compilación sin el administrador.
* un operador de Adobe Campaign (usuario de marketing): una actualización correcta depende de la capacidad del usuario para realizar correctamente sus tareas diarias. Por este motivo, incluya siempre al menos uno de los operadores diarios en las pruebas de los servidores actualizados.

### Planificación

Estos son los puntos clave sobre cómo planificar una actualización de compilación:

1. Reserva al menos 2 horas para la actualización.
1. Distribuya los datos de contacto para el Adobe y el personal del cliente.
1. Para instancias hospedadas: El personal de Adobes y clientes coordinará el tiempo de la actualización y quién la ejecutará.
1. Para instancias in situ: el personal del cliente gestiona todo el proceso: si se necesita asistencia para probar flujos de trabajo personalizados y lógica de envío, se deben incorporar servicios de consultoría.
1. Determine y confirme a qué versión de Adobe Campaign desea actualizar: consulte las [notas de la versión de Adobe Campaign Classic](../../rn/using/rn-overview.md).
1. Confirme la posesión de ejecutables de actualización.

### Personas clave

El proceso de actualización de la compilación requiere la participación de las siguientes personas:

* Adobe, arquitecto: en el caso de las arquitecturas alojadas o híbridas, el arquitecto debe coordinarse con Adobe Campaign Client Care.

* Administrador de proyectos:
   * para instalaciones in situ: el jefe de proyecto interno del cliente dirige la actualización y administra las pruebas del ciclo vital.

   * para la instalación alojada: el equipo de alojamiento se asociará con el equipo de Adobe Campaign Client Care y el cliente para coordinar la cronología de actualización de todas las instancias.

* Administrador de Adobe Campaign:
   * para instalaciones in situ: el administrador realiza la actualización.

   * para instalaciones alojadas: el equipo de alojamiento realiza la actualización.

* Operador de Adobe Campaign\usuario de marketing: el operador ejecuta pruebas en instancias de desarrollo, prueba y producción.

### Preparación de la actualización de la compilación

Antes de iniciar la actualización de la compilación, los clientes internos deben realizar la siguiente preparación:

1. Asegúrese de que cualquier trabajo de desarrollo se pueda exportar antes de la actualización, exporte como paquetes.

1. Realice una copia de seguridad completa de las bases de datos para todas las instancias de los entornos de origen y destinatario.

1. Obtenga la versión más reciente del [archivo de configuración del servidor](../../installation/using/the-server-configuration-file.md).

1. Descargue la última compilación. [Obtenga más información sobre el centro](https://docs.adobe.com/content/help/es-ES/experience-cloud/software-distribution/home.html) de descargas.

También necesita conocer todas las [líneas de comandos útiles](../../installation/using/command-lines.md) antes de iniciar una actualización de compilación:

* **nlserver pdump**: listas que ejecutan procesos
* **nlserver pdump -quien**: listas de sesiones de cliente activas
* **monitor nlserver -falta**: Faltan propiedades en las listas
* **inicio de NLServer process@instanceName**: inicio un proceso
* **nlserver stop process@instanceName**: detiene un proceso
* **nlserver Restart process@instanceName**: reinicia un proceso
* **nlserver shutdown**: detiene todos los procesos de Campaña
* **nlserver watchdog -svc**: inicio el vigilante (solo UNIX)

## Realizar la actualización

![](assets/do-not-localize/icon_process.png)

Los procedimientos que se describen a continuación sólo los realizan **clientes internos**. Para los clientes alojados, el equipo de alojamiento se encarga de ello. Para actualizar Adobe Campaign a una nueva compilación, a continuación se describe el procedimiento detallado.

### Duplicado del entorno

Así es como se duplicado un entorno de Adobe Campaign para restaurar un entorno de origen a un entorno de destinatario, lo que resulta en dos entornos de trabajo idénticos.

Para realizar esto, siga los pasos a continuación:

1. Cree una copia de las bases de datos en todas las instancias del entorno de origen.

1. Restaure estas copias en todas las instancias del entorno de destinatario.

1. Ejecute la secuencia de comandos de cauterización **nms:PLInstance.js** en el entorno de destinatario antes de iniciarla. Esto detendrá todos los procesos que interactúen con el exterior: registros, seguimiento, envíos, flujos de trabajo de la campaña, etc.

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. Compruebe la cauterización como se indica a continuación:

   * Compruebe que la única parte de envío es la que tiene el ID establecido en **0**:

      ```
      SELECT * FROM neolane.nmsdeliverypart;
      ```

   * Compruebe que la actualización del estado del envío es correcta:

      ```
      SELECT iSate, count(*) FROM neolane.nmsdeliveryGroup By iProd;
      ```

   * Compruebe que la actualización de estado del flujo de trabajo es correcta:

      ```
      SELECT iState, count (*) FROM neolane.xtkworkflowGROUP BY iState;
      SELECT iStatus, count (*) FROM neolane.xtkworkflowGROUP BY iStatus;
      ```

### Cerrar servicios

Para reemplazar todos los archivos con la nueva versión, es necesario que se cierren todas las instancias de nlserverservice.

1. Cierre los siguientes servicios:

   * Servicios Web (IIS): **iisreset /stop**
   * Servicio Adobe Campaign: **net stop nlserver6**

   >[!NOTE]
   >
   >Asegúrese de que el servidor de redirección (webmdl) está detenido, para que el archivo nlsrvmod.dll utilizado por IIS pueda reemplazarse por la nueva versión.

1. Valide que no haya tareas activas ejecutando el comando **nlserver pdump**. Si no hay tareas, la salida debería parecerse a la siguiente:

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. Consulte el Administrador de Tareas de Windows para confirmar que todos los procesos se han detenido.

### Actualización de la aplicación Adobe Campaign Server

1. Ejecute el archivo **Setup.exe**. Si necesita descargar este archivo, acceda [al centro de descargas](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html).

1. Seleccione el modo de instalación: **Actualizar** o **Reparar**.

1. Haga clic en **Next**.

1. Haga clic en **Finalizar**: el programa de instalación copia los nuevos archivos.

1. Una vez finalizada la operación, haga clic en **Finalizar**.

### Sincronizar recursos

1. Abra la línea de comandos.

1. Ejecute **nlserver config -postupgrade -allinstance** para realizar lo siguiente:

   * Sincronizar recursos
   * Actualizar esquemas
   * Actualizar la base de datos

   >[!NOTE]
   >
   >Esta operación solo debe realizarse una vez y sólo en un servidor de aplicaciones web nlserverweb.

   Para sincronizar solo una base de datos, ejecute el siguiente comando:

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. Compruebe si la sincronización ha generado errores o advertencias.

### Reiniciar servicios

Es necesario reiniciar los siguientes servicios:

* Servicios Web (IIS): **issreset /inicio**
* Servicio Adobe Campaign: **net inicio nlserver6**

### Actualización de consolas de cliente

En el equipo en el que está instalado el servidor de aplicaciones de Adobe Campaign (nlserverweb), descargue y copie el archivo:

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```


La próxima vez que se conecten las consolas de cliente, una ventana informará a los usuarios sobre la disponibilidad de una nueva actualización y les oferta la posibilidad de descargarlas e instalarlas.

### Tareas adicionales específicas

Algunas configuraciones requieren tareas adicionales específicas para actualizarse a una nueva compilación.

#### Mensajería transaccional

Cuando la mensajería transaccional (centro de mensajes) está habilitada en la instancia de Campaña, debe realizar estos pasos adicionales para actualizar:

1. Actualice el servidor de producción de Message Center a la versión seleccionada.
1. Ejecute las secuencias de comandos posteriores a la actualización.
1. Ejecute pruebas y asegúrese de que los mensajes de correo electrónico se reciben correctamente a través de la instancia de producción de Message Center.
1. Actualice los clientes y borre la caché.
1. Exportar paquetes:
   * Exportar paquetes mediante la herramienta de exportación de paquetes de cliente
   * Importar paquete de esquema
   * Desconectar y reconectar cliente
   * Actualizar base de datos
   * Desconectar y reconectar
   * Importar paquete de administración
   * Importar paquete de contenido
   * Importar paquete de Gestor de contenido
   * Desconectar y reconectar
   * Realizar una comprobación rápida de la salud de los flujos de trabajo

1. Publique plantillas de centro de mensajes para asegurarse de que la interfaz entre servidores y la instancia de centro de mensajes funciona.
1. Ejecute pruebas para asegurarse de que los mensajes de correo electrónico se reciben correctamente a través de la instancia de producción de Message Center.
1. Ejecute pruebas de flujo de trabajo en producción para asegurarse de que se reciben envíos.

#### Intermediaria

En el contexto de un entorno de intermediaria, debe realizar estos pasos adicionales para actualizar:

1. Póngase en contacto con [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para coordinar la actualización del servidor Intermediaria.
1. Valide que la versión se haya actualizado ejecutando un vínculo de prueba. Por ejemplo:

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>El servidor Intermediaria siempre debe ejecutar la misma versión (o más reciente) que los servidores de marketing.


## En caso de conflicto

### Identificar conflictos

Debe comprobar el resultado de la sincronización. Este procedimiento sólo lo realizan los clientes locales. Para los clientes alojados, el equipo de alojamiento se encarga de ello. Existen dos formas de vista del resultado de la sincronización:

En la interfaz de la línea de comandos, los errores se materializan mediante un triple elemento de cadena &#39;>>>&#39; y la sincronización se detiene automáticamente. Las advertencias son materializadas por un doble de chevron &#39;>>&#39; y deben resolverse una vez finalizada la sincronización. Al final de la posactualización, se muestra un resumen en el símbolo del sistema. Puede tener este aspecto:

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

Si la advertencia se refiere a un conflicto de recursos, se requiere la atención del usuario para resolverlo.

El archivo **postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** contiene el resultado de la sincronización. Está disponible de forma predeterminada en el siguiente directorio: **installationDirectory/var/instanceName/postupgrade**. Los errores y las advertencias se indican mediante los atributos de error y advertencia.

### Analizar conflictos

**¿Cómo se encuentra un conflicto?**

Los conflictos se pueden encontrar dentro del archivo post-upgrade.log en el servidor en cuestión o dentro de la interfaz de cliente de Campaña (Administración > Configuración > Administración de paquetes > Editar conflictos).

El documento con el identificador &quot;stockOverview&quot; y el tipo &quot;nms:webApp&quot; está en conflicto con la nueva versión.

Si se encuentra un conflicto, compruebe si coinciden las siguientes condiciones:

* ¿El cliente ha modificado o personalizado el objeto?
* ¿Ha cambiado el objeto en el producto?

Si ninguna de estas condiciones se aplica, se trata de un falso positivo. Si ambas condiciones se aplican, se ha encontrado un conflicto real.

**¿El cliente ha modificado el objeto?**

1. Identifique el objeto en conflicto.
1. Pregunte al cliente si ha modificado el objeto.
1. ¿Hay algo inusual con el objeto?
1. ¿Se ha establecido la fecha de la última modificación en el código del objeto?
1. Examine el código XML desde el conflicto para ver los atributos &quot;_Conflict&quot;. ¿Parece una personalización?

**¿Se ha cambiado el objeto en la nueva compilación?**

1. ¿Algún &quot;sospechoso habitual&quot;? Informes o aplicaciones Web integradas (por ejemplo: &#39;deliveryValidation&#39;, &#39;deliveryOverview&#39;, &#39;budget&#39;).
1. Examine los registros de cambios en busca de actualizaciones.
1. Pregunte a los expertos de Adobe Campaign.
1. Realice una &quot;diferencia&quot; en el código.

### Resolver un conflicto

Para resolver conflictos, aplique el siguiente proceso:

1. En el explorador de Adobe Campaign, vaya a **Administración > Configuración > Administración de paquetes > Editar conflictos**.

1. Seleccione el conflicto que desee resolver en la lista.
Existen tres opciones para resolver conflictos: **Acepte la nueva versión**, **Mantenga la versión actual**, **Combine el código (y declare como resuelto)**, **Ignore el conflicto (no se recomienda)**.

**¿Cuándo puedo aceptar la nueva versión?**

* Si desea las funciones estándar.
* Si no tiene personalizaciones (todas las personalizaciones se eliminarán)

**¿Cuándo puedo mantener la versión actual?**

* Si tiene personalizaciones
* Si no desea combinar
* Si no necesita ninguna corrección en el objeto en conflicto de la actualización

**¿Cuándo realizar una combinación?**

* Solo se pueden combinar formularios, informes y aplicaciones web.
* Algunas combinaciones menores se pueden resolver sin comprender el código.
* Las fusiones más complejas deben ser realizadas por alguien con las habilidades y capacidades adecuadas.
* Consulte [Realizar una combinación](#perform-a-merge).

**¿Qué pasa si ignoro los conflictos?**

* El conflicto seguirá
* No se actualizará el objeto
* Efectos a largo plazo: incompatibilidades de versiones, el cliente no se beneficiará de las correcciones de errores.

>[!IMPORTANT]
>Se recomienda encarecidamente resolver los conflictos.


### Realizar una combinación{#perform-a-merge}

Existen diferentes tipos de combinaciones:

1. Combinación sencilla: los elementos personalizados y nuevos son pequeños y no están relacionados, y no se requiere codificación.
1. Sin cambios: aceptar nueva versión, solo se cambió la fecha de la última actualización, solo los comentarios, las fichas, los espacios o las líneas nuevas. Ejemplo: guardar accidentalmente.
1. Cambios triviales: sólo se cambió una línea. Ejemplo: xpathToLoad
1. Combinación compleja: cuando se requiera la codificación. Se necesitan habilidades de desarrollo. Consulte [Combinaciones complejas](#complex-merges).

#### ¿Cómo combinar?

1. Obtenga las tres versiones: la versión original, la nueva versión y la versión personalizada.
1. Ejecute una &quot;diferencia&quot; entre la versión original y la nueva.
1. Aísle los cambios.
1. Si no hay cambios, resuelva manteniendo la versión actual.

#### ¿Dónde encontrar el código?

1. El código integrado se almacena en archivos XML de la carpeta de datos. Busque el archivo XML que coincide con el objeto en conflicto. Ejemplo: installationDirectory\datakit\nms\fra\form\recipient.xml
1. Recuperar la versión original: mediante el [Centro de descarga](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html) u otra instalación no actualizada del producto.
1. Recuperar la nueva versión: mediante el [centro de descarga](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html) o los archivos instalados del cliente.
1. Recuperar la versión personalizada: recupere el código fuente del objeto desde el cliente de Campaña.

### ¿Cómo hacer una diferencia?

1. Instale un editor de texto o de combinación, por ejemplo Bloc de notas ++, AraxisMerge, WinMerge.
1. Abra el archivo original y el nuevo archivo en el editor.
1. Ejecute la diferencia (compare los dos archivos).
1. Identificar cualquier diferencia.

### ¿Cómo combinar?

1. Inicio de la versión personalizada.
1. Aplique los cambios.
1. Resuelva el conflicto declarándolo resuelto.
1. Compruebe la existencia de no regresiones.

Si decide resolver el conflicto manualmente, siga este procedimiento:

1. En la sección inferior de la ventana, busque la **_cadena_de_conflicto_** para localizar las entidades con conflictos. La entidad instalada con la nueva versión contiene el nuevo argumento; la entidad que coincide con la versión anterior contiene el argumento personalizado.
1. Elimine la versión que no desee conservar. Elimine la cadena **_argumento_conflicto_** de la entidad que mantiene.
1. Vaya al conflicto que ha resuelto. Haga clic en el icono **Acciones** y seleccione **Declarar como resueltas**.
1. Guarde los cambios: el conflicto ya está resuelto.

#### Combinaciones complejas{#complex-merges}

1. Comprender lo que hace el cambio: haga ingeniería inversa de los cambios, examine los registros de cambios y realice un seguimiento con expertos de Adobe Campaign.
1. Decida qué hacer con el cambio.
1. Comprender lo que hacen las personalizaciones: ingeniería inversa de los cambios

Estos son los pasos para realizar una combinación compleja:

1. Copiar bits de código del conjunto de cambios
1. Pegar en la versión personalizada
1. Prueba de no regresiones de personalización
1. Prueba de la función de los cambios
1. Realizar prueba de aceptación del usuario
1. Realizar en el entorno de prueba


>[!IMPORTANT]
>Se necesitan habilidades de desarrollo para realizar combinaciones complejas.


**Temas relacionados**

* [Preguntas frecuentes sobre la actualización de versiones](../../platform/using/faq-build-upgrade.md)
* [Notas de la versión de Campaign Classic ](../../rn/using/rn-overview.md)
* [Opciones de ayuda y asistencia técnica para Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)
* [Programa estándar Gold](https://helpx.adobe.com/es/campaign/kb/gold-standard.html)