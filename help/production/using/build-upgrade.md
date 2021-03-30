---
solution: Campaign Classic
product: campaign
title: Introducción a las actualizaciones de versiones
description: Conozca los pasos clave para actualizar a una nueva versión
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 7b1e6dd00943e10dff693d78b3aa7cf2ad3e6727
workflow-type: tm+mt
source-wordcount: '2355'
ht-degree: 4%

---


# Realización de una actualización de versión{#performing-a-build-upgrade}

Esta sección le proporcionará un tutorial en profundidad sobre el proceso de actualización y los pasos para identificar y resolver conflictos.

La actualización de la compilación debe llevarse a cabo con precaución, sus efectos deben ser considerados de antemano y el procedimiento debe completarse con un alto nivel de disciplina. Para garantizar una actualización correcta, asegúrese de que solo los usuarios expertos realicen los pasos descritos a continuación. Además, recomendamos encarecidamente que se ponga en contacto con [Adobe Customer Care](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) antes de iniciar cualquier actualización.

Se necesitan los siguientes requisitos previos:

* Explicación de la arquitectura de Campaign
* Conocimientos de los sistemas y del servidor
* Derechos y permisos administrativos

Puede encontrar más información en estas secciones: [Actualización de Adobe Campaign](../../production/using/upgrading.md), [Migración a una nueva versión](../../migration/using/about-migration.md).

En el caso de instancias alojadas e híbridas, debe solicitar la actualización de la compilación al equipo de operaciones técnicas de Adobe. Para obtener más información, consulte la sección Preguntas frecuentes en la parte inferior de esta página. Consulte también las [preguntas frecuentes sobre la actualización de la versión](../../platform/using/faq-build-upgrade.md).

## Preparación de la actualización

![](assets/do-not-localize/icon_planification.png)

Antes de iniciar la actualización de la compilación, debe realizar una preparación completa como se describe a continuación.
Una vez que el sistema está listo para ser actualizado, una actualización de compilación tarda **al menos** 2 horas.

El proceso de actualización de la compilación requiere los siguientes recursos:

* un arquitecto de Adobe: para comprender las estructuras de la base de datos (esquemas predeterminados y cualquier esquema adicional que se haya añadido, diseños de campaña y cualquier funcionalidad de ruta crítica que se deba iniciar y probar en un orden específico).
* un administrador de proyectos : en el caso de que la actualización de la compilación involucre muchas instancias diferentes (producción, ensayo, prueba) y otros servidores y aplicaciones de terceros (bases de datos, sitios SFTP, proveedores de servicios de mensajería), contar con un administrador de proyectos para coordinar todas las pruebas se considera una práctica recomendada.
* un administrador de Adobe Campaign: su administrador conoce la configuración del servidor, que incluye, entre otras cosas: requisitos de seguridad, diseño de carpetas, informes e importación/exportación. No realice una actualización de la compilación sin su administrador.
* un operador de Adobe Campaign (usuario de marketing): una actualización correcta depende de la capacidad del usuario para realizar sus tareas diarias correctamente. Por este motivo, incluya siempre al menos uno de sus operadores diarios en la prueba de los servidores actualizados.

### Planificación

Estos son los puntos clave sobre cómo planificar una actualización de compilación:

1. Reserve al menos 2 horas para la actualización.
1. Distribuya los detalles de contacto para el Adobe y el personal del cliente.
1. Para instancias alojadas: El personal del Adobe y del cliente coordinará el tiempo para la actualización y quién la ejecutará.
1. Para instancias locales: el personal del cliente gestiona todo el proceso: si se necesita asistencia para probar flujos de trabajo personalizados y lógica de entrega, se deben incorporar servicios de consultoría.
1. Determine y confirme a qué versión de Adobe Campaign desea actualizar: consulte las [notas de la versión de Adobe Campaign Classic](../../rn/using/rn-overview.md).
1. Confirme la posesión de los ejecutables de actualización.

### Personas clave

El proceso de actualización de la compilación requiere la participación de las siguientes personas:

* arquitecto de Adobe: para arquitecturas alojadas o híbridas, el arquitecto debe coordinarse con Adobe Campaign Client Care.

* Administrador de proyectos:
   * para instalaciones On Premise: el líder interno del proyecto del cliente dirige la actualización y administra las pruebas de ciclo vital.

   * para la instalación alojada: el equipo de alojamiento se asociará con el equipo de Atención al cliente de Adobe Campaign y el cliente para coordinar el cronograma de actualización de todas las instancias.

* Administrador de Adobe Campaign:
   * para instalaciones On Premise: el administrador realiza la actualización.

   * para instalaciones alojadas: el equipo de alojamiento realizará la actualización.

* Operador de Adobe Campaign\usuario de marketing: el operador ejecuta pruebas en instancias de desarrollo, prueba y producción.

### Preparación de la actualización de compilación

Antes de iniciar la actualización de la compilación, los clientes locales deben realizar la siguiente preparación:

1. Asegúrese de que cualquier trabajo de desarrollo se pueda exportar antes de la actualización y exportar como paquetes.

1. Realice una copia de seguridad completa de las bases de datos para todas las instancias de los entornos de origen y destino.

1. Obtenga la última versión de su [archivo de configuración del servidor](../../installation/using/the-server-configuration-file.md).

1. [Descargue la última versión](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html). [Más información](https://docs.adobe.com/content/help/es-ES/experience-cloud/software-distribution/home.html).

También necesita conocer todas las [líneas de comandos útiles](../../installation/using/command-lines.md) antes de iniciar una actualización de compilación:

* **nlserver pdump**: listas ejecutar procesos
* **nlserver pdump -who**: enumera las sesiones de cliente activas
* **nlserver monitor -missing**: listas de propiedades que faltan
* **inicio de nlserver process@instanceName**: inicia un proceso
* **nlserver stop process@instanceName**: detiene un proceso
* **nlserver restart process@instanceName**: reinicia un proceso
* **nlserver shutdown**: detiene todos los procesos de Campaign
* **nlserver watchdog -svc**: inicia el watchdog (solo UNIX)

## Realizar la actualización

![](assets/do-not-localize/icon_process.png)

Los siguientes procedimientos solo los realizan los clientes **locales**. Para los clientes alojados, el equipo de alojamiento se encarga de ello. Para actualizar Adobe Campaign a una nueva versión, a continuación se describe el procedimiento detallado.

### Duplicar el entorno

Así se duplica un entorno de Adobe Campaign para restaurar un entorno de origen en un entorno de destino, lo que da como resultado dos entornos de trabajo idénticos.

Para realizar esto, siga los pasos a continuación:

1. Cree una copia de las bases de datos en todas las instancias del entorno de origen.

1. Restaure estas copias en todas las instancias del entorno de destino.

1. Ejecute el script de cauterización **nms:frozenInstance.js** en el entorno de destino antes de iniciarlo. Esto detendrá todos los procesos que interactúan con el exterior: registros, seguimiento, envíos, flujos de trabajo de campaña, etc.

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. Compruebe la cauterización de la siguiente manera:

   * Compruebe que la única parte del envío es la que tiene el ID establecido en **0**:

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

### Apagar servicios

Para reemplazar todos los archivos con la nueva versión, es necesario que todas las instancias de nlserverservice estén apagadas.

1. Apague los siguientes servicios:

   * Servicios Web (IIS): **iisreset /stop**
   * Servicio de Adobe Campaign: **net stop nlserver6**

   >[!NOTE]
   >
   >Asegúrese de que el servidor de redirección (webmdl) esté detenido para que el archivo nlsrvmod.dll utilizado por IIS pueda reemplazarse por la nueva versión.

1. Valide que no haya tareas activas ejecutando el comando **nlserver pdump**. Si no hay tareas, la salida debería parecerse a la siguiente:

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. Compruebe el Administrador de tareas de Windows para confirmar que todos los procesos se han detenido.

### Actualizar la aplicación de servidor de Adobe Campaign

1. Ejecute el archivo **Setup.exe**. Si necesita descargar este archivo, acceda [al Centro de descargas](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html).

1. Seleccione el modo de instalación: **Actualizar** o **Reparar**.

1. Haga clic en **Next**.

1. Haga clic en **Finish**: el programa de instalación copia los nuevos archivos.

1. Una vez finalizada la operación, haga clic en **Finish**.

### Sincronizar recursos

1. Abra la línea de comandos.

1. Ejecute **nlserver config -postupgrade -allinstances** para realizar lo siguiente:

   * Sincronizar recursos
   * Actualizar esquemas
   * Actualizar la base de datos

   >[!NOTE]
   >
   >Esta operación solo debe realizarse una vez y solo en un servidor de aplicaciones nlserverweb.

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

La consola de cliente debe estar en la misma compilación que la instancia de servidor.

En el equipo en el que está instalado el servidor de aplicaciones de Adobe Campaign (nlserverweb), descargue y copie el archivo:

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

La próxima vez que se conecten consolas de cliente, una ventana informará a los usuarios sobre la disponibilidad de una nueva actualización y les ofrecerá la posibilidad de descargarla e instalarla.

### Tareas adicionales específicas

Algunas configuraciones requieren tareas adicionales específicas para actualizar a una nueva compilación.

#### Mensajería transaccional

Cuando la mensajería transaccional (centro de mensajes) está habilitada en la instancia de Campaign, debe realizar estos pasos adicionales para actualizar:

1. Actualice el servidor de producción del Centro de mensajes a la versión elegida.
1. Ejecute los scripts posteriores a la actualización.
1. Ejecute pruebas y asegúrese de que los correos electrónicos se reciben correctamente a través de la instancia de producción del Centro de mensajes.
1. Actualice los clientes y borre la caché.
1. Exportar paquetes:
   * Exportación de paquetes mediante la herramienta de exportación de paquetes de cliente
   * Importar paquete de esquema
   * Desconecte y vuelva a conectar el cliente
   * Actualizar base de datos
   * Desconecte y vuelva a conectar
   * Importar paquete de administración
   * Importar paquete de contenido
   * Importar paquete de gestión de contenido
   * Desconecte y vuelva a conectar
   * Realizar una comprobación rápida de la validez de los flujos de trabajo

1. Publique plantillas del Centro de mensajes para garantizar que la interfaz entre servidores y la instancia del Centro de mensajes funcione.
1. Ejecute pruebas para asegurarse de que los correos electrónicos se reciben correctamente a través de la instancia de producción del Centro de mensajes.
1. Ejecute pruebas de flujo de trabajo en producción para garantizar que se reciban los envíos.

#### Mid-sourcing

En el contexto de un entorno de mid-sourcing, debe realizar estos pasos adicionales para actualizar:

1. Póngase en contacto con [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para coordinar la actualización del servidor intermediario.
1. Valide que la versión se haya actualizado ejecutando un vínculo de prueba. Por ejemplo:

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>El servidor intermediario siempre debe ejecutar la misma versión (o más reciente) que para los servidores de marketing.


## En caso de conflicto

### Identificar conflictos

Debe comprobar el resultado de la sincronización. Este procedimiento solo lo realizan los clientes locales. Para los clientes alojados, el equipo de alojamiento se encarga de ello. Existen dos formas de ver el resultado de la sincronización:

En la interfaz de la línea de comandos, los errores se materializan mediante una triple cadena &#39;>>>&#39; y la sincronización se detiene automáticamente. Las advertencias se materializan mediante una doble cadena &#39;>>&#39; y deben resolverse una vez finalizada la sincronización. Al final de la actualización posterior, se muestra un resumen en el símbolo del sistema. Puede tener este aspecto:

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

Si la advertencia se refiere a un conflicto de recursos, es necesario que el usuario preste atención para resolverlo.

El archivo **postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** contiene el resultado de la sincronización. Está disponible de forma predeterminada en el siguiente directorio: **installationDirectory/var/instanceName/postupgrade**. Los errores y las advertencias se indican mediante los atributos de error y advertencia.

### Analizar conflictos

**¿Cómo se encuentra un conflicto?**

Los conflictos se pueden encontrar dentro del archivo postupgrade.log en el servidor en cuestión o dentro de la interfaz del cliente de Campaign (Administración > Configuración > Administración de paquetes > Editar conflictos).

El documento con identificador &quot;stockOverview&quot; y tipo &quot;nms:webApp&quot; está en conflicto con la nueva versión.

Si se encuentra un conflicto, compruebe si las siguientes condiciones coinciden:

* ¿El cliente ha modificado o personalizado el objeto?
* ¿Ha cambiado el objeto en el producto?

Si no se aplica ninguna de estas condiciones, se trata de un falso positivo. Si se aplican ambas condiciones, se ha encontrado un conflicto real.

**¿El cliente ha modificado el objeto?**

1. Identifique el objeto conflictivo.
1. Pregunte al cliente si modificó el objeto.
1. ¿Hay algo inusual con el objeto?
1. ¿La fecha de la última modificación está establecida en el código del objeto?
1. Examine el código XML del conflicto en busca de atributos &quot;_conflict&quot;. ¿Se parece a una personalización?

**¿Se ha cambiado el objeto en la nueva compilación?**

1. ¿Algún &quot;sospechoso habitual&quot;? Aplicaciones web o informes integrados (por ejemplo: &#39;deliveryValidation&#39;, &#39;deliveryOverview&#39;, &#39;budget&#39;).
1. Examine los registros de cambios para ver si hay actualizaciones.
1. Consulte a los expertos de Adobe Campaign.
1. Realice una &quot;diferencia&quot; en el código.

### Resolver un conflicto

Para resolver conflictos, siga el siguiente proceso:

1. En el explorador de Adobe Campaign, vaya a **Administration > Configuration > Package management > Edit conflicts**.

1. Seleccione el conflicto que desee resolver en la lista.
Hay tres opciones para resolver conflictos: **Acepte la nueva versión**, **Mantenga la versión actual**, **Combine el código (y declare como resuelto)**, **Ignore el conflicto (no recomendado)**.

**¿Cuándo puedo aceptar la nueva versión?**

* Si desea utilizar las funciones estándar.
* Si no tiene personalizaciones (se eliminarán todas las personalizaciones)

**¿Cuándo puedo mantener la versión actual?**

* Si tiene personalizaciones
* Si no desea combinar
* Si no necesita correcciones en el objeto conflictivo de la actualización

**¿Cuándo realizar una combinación?**

* Solo se pueden combinar formularios, informes y aplicaciones web.
* Algunas combinaciones menores se pueden resolver sin comprender el código.
* Las fusiones más complejas deben realizarlas personas con las habilidades y capacidades adecuadas.
* Consulte [Realizar una combinación](#perform-a-merge).

**¿Y si ignoro los conflictos?**

* El conflicto seguirá
* El objeto no se actualiza
* Impactos a largo plazo: incompatibilidades de la versión, el cliente no se beneficiará de las correcciones de errores.

>[!IMPORTANT]
>Es muy recomendable resolver los conflictos.


### Realizar una combinación{#perform-a-merge}

Existen diferentes tipos de combinaciones:

1. Combinación sencilla: los elementos personalizados y nuevos son pequeños y no están relacionados, y no se requiere código.
1. Sin cambios: aceptar nueva versión, solo se ha cambiado la fecha de la última actualización, solo comentarios, pestañas, espacios o nuevas líneas. Ejemplo: guardado accidental.
1. Cambios triviales: solo se ha cambiado una línea. Ejemplo: xpathToLoad
1. Combinación compleja: cuando sea necesario codificar. Se necesitan habilidades de desarrollo. Consulte [Combinaciones complejas](#complex-merges).

#### ¿Cómo se combina?

1. Obtenga las tres versiones: la versión original, la nueva versión y la versión personalizada.
1. Ejecute una &quot;diferencia&quot; entre las versiones original y nueva.
1. Aísle los cambios.
1. Si no hay cambios, resuelva manteniendo la versión actual.

#### ¿Dónde encontrar el código?

1. El código integrado se almacena en archivos XML en la carpeta datakit. Busque el archivo XML que coincida con el objeto conflictivo. Ejemplo: installationDirectory\datakit\nms\fra\form\recipient.xml
1. Recupere la versión original: a través del [Download center](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) u otra instalación no actualizada del producto.
1. Recupere la nueva versión: a través del [Centro de descargas](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) o los archivos instalados del cliente.
1. Recupere la versión personalizada: recupere el código fuente del objeto desde el cliente de Campaign.

### ¿Cómo hacer una diferencia?

1. Instale un editor de texto o de combinación, por ejemplo Notepad ++, AraxisMerge, WinMerge.
1. Abra el archivo original y el nuevo archivo en el editor.
1. Ejecute la comparación de diferencias (compare los dos archivos).
1. Identifique cualquier diferencia.

### ¿Cómo se combina?

1. Comience desde la versión personalizada.
1. Aplique los cambios.
1. Resuelva el conflicto declarándolo resuelto.
1. Compruebe si hay no regresiones.

Si decide resolver el conflicto manualmente, proceda de la siguiente manera:

1. En la sección inferior de la ventana, busque **_conflict_string_** para localizar las entidades con conflictos. La entidad instalada con la nueva versión contiene el nuevo argumento , la entidad que coincide con la versión anterior contiene el argumento personalizado.
1. Elimine la versión que no desee conservar. Elimine la cadena **_conflict_discussion_** de la entidad que mantiene.
1. Vaya al conflicto que ha resuelto. Haga clic en el icono **Actions** y seleccione **Declarar como resuelto**.
1. Guarde los cambios: el conflicto ya está resuelto.

#### Combinaciones complejas{#complex-merges}

1. Comprenda lo que hace el cambio: aplique ingeniería inversa de los cambios, examine los registros de cambios y realice un seguimiento con los expertos de Adobe Campaign.
1. Decida qué hacer con el cambio.
1. Comprenda lo que hacen las personalizaciones: ingeniería inversa de los cambios

Estos son los pasos para realizar una combinación compleja:

1. Copiar bits de código del conjunto de cambios
1. Pegar en la versión personalizada
1. Prueba de no regresiones de personalización
1. Comprobación de la función de los cambios
1. Realizar pruebas de aceptación de usuario
1. Realizar en un entorno de prueba


>[!IMPORTANT]
>Se necesitan habilidades de desarrollo para realizar combinaciones complejas.


**Temas relacionados**

* [Preguntas frecuentes sobre la actualización de versiones](../../platform/using/faq-build-upgrade.md)
* [Notas de la versión de Campaign Classic ](../../rn/using/rn-overview.md)
* [Opciones de ayuda y asistencia para Campaign Classic](../../support.md)
* [[!DNL Gold Standard] programa](../../rn/using/gs-overview.md)
