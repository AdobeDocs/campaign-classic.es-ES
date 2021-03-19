---
solution: Campaign Classic
product: campaign
title: Notas de la versión de Campaign 18.4
description: Notas de la versión 18.4 de Campaign
feature: null
role: null
level: null
translation-type: tm+mt
source-git-commit: ce60b2bd0a9d75ca429af2f740832b408ce3c48b
workflow-type: tm+mt
source-wordcount: '2267'
ht-degree: 99%

---


# Versión 18.4{#release-18-4}

## Versión 18.4.5: compilación 8937{#release-18-4-5-build-8937}

21 de noviembre de 2018

**Mejoras**

* Se solucionaron varios problemas al ejecutar flujos de trabajo con MySQL en FDA. (NEO-11652)
* Se ha corregido un problema por el que una parte de la población de entrega permanecía en estado pendiente en casos específicos. (NEO-11336)
* Se ha corregido un problema intermitente con la respuesta automática de SMS. (NEO-11811)
* Se ha corregido un problema de agotamiento de ID al utilizar direcciones semilla en una entrega. (NEO-11842)
* Se ha corregido un error de sintaxis al realizar una ordenación en una actividad de flujo de trabajo de enriquecimiento. (NEO-11394)
* Se ha corregido un problema que podría provocar el bloqueo de un servidor web al reiniciar IIS. (NEO-10862)
* Se ha corregido un problema que podría provocar que el flujo de trabajo de seguimiento falle tras una actualización de compilación (FDA - SQL). (NEO-11635)
* Se ha corregido un problema que podría provocar que se pierdan los datos de la lista de flujos de trabajo. (NEO-11696)
* Se ha corregido un problema de rendimiento al enviar notificaciones push. (NEO-11787)
* Se ha corregido un problema que impedía que el seguimiento web funcionara para los dominios “com.au” (NEO-4385).
* Se ha corregido un problema con el bloqueo del cliente que podría producirse al utilizar flujos de trabajo complejos. (NEO-11847)
* Se ha corregido un error de Oracle al guardar una nueva entrega después de seleccionar un elemento de un esquema específico (NEO-11682).
* Se ha corregido un problema que se producía al consultar un campo que contiene caracteres con acentos (FDA/Teradata). La cuenta externa ahora permite cambiar la codificación utilizada para comunicarse con el controlador de Teradata. (NEO-11818).
* Se ha corregido un problema con el seguimiento al pasar direcciones URL en variables adicionales en una notificación inmediata que podría provocar datos incorrectos o sin formato recibidos por la aplicación móvil. (NEO-11468, NEO-11960)
* Se ha corregido un problema que ocasionaba un problema de visualización al utilizar una distribución de valores con un vínculo 1:N. (NEO-11820)
* Se ha corregido un problema que impedía que la carga masiva funcionara en Teradata 16.
* Se ha aumentado el tamaño del búfer para la marca de tiempo en Teradata para evitar problemas de vínculo con el controlador 15.10.
* Se ha mejorado la administración de los índices de nombres largos que podrían causar problemas después de la actualización.
* Se ha mejorado el tiempo disponible de memoria compartida durante el procesamiento secundario (MTA).
* Se ha corregido un posible bloqueo en Apache (seguimiento).

## Versión 18.4.4: compilación 8936{#release-18-4-4-build-8936}

1 de agosto de 2018

**Mejoras**

* Se han mejorado los registros de archivos de correo electrónico, lo que facilita la comprobación de los mensajes de correo electrónico que se han entregado o no se han enviado correctamente a través del archivo BCC. (NEO-10675)
* Se ha corregido un problema que provocaba la visualización de las direcciones IP del equilibrador de carga en lugar de las direcciones IP del cliente en los registros de seguimiento. (NEO-11295)
* Se ha corregido un error con la codificación LATIN1 al utilizar una conexión de FDA con una base de datos PostgreSQL. (NEO-11299)
* Se ha corregido un problema que se producía al utilizar la opción de entrega **[!UICONTROL Prepare the personalization data with a workflow]**. (NEO-11047, NEO-11301)
* Se ha corregido un problema aleatorio que ocasionaba que las propiedades de una entrega se sobrescriban erróneamente. (NEO-11015)
* Se ha corregido un problema que se producía al utilizar campos calculados en una actividad de flujo de trabajo **[!UICONTROL Survey answers]**. (NEO-11382)
* Se ha corregido un problema que se producía al utilizar datos almacenados en XML en una actividad de flujo de trabajo **[!UICONTROL Survey answers]**. (NEO-10816)
* Se ha corregido un problema que se producía al realizar la actualización del servidor con la compilación 8935.
* Se ha corregido un problema que mostraba errores no viables en el registro posterior de actualización cuando una actividad de flujo de trabajo **[!UICONTROL Survey answers]** no estaba completamente configurada.
* Teradata FDA: Se ha corregido un problema con campos autoincrementados e índices en tablas SQL.

## Versión 18.4.3: compilación 8935{#release-18-4-3-build-8935}

22 de junio de 2018

**Mejoras**

* Se ha corregido un problema en la codificación de seguimiento con Microsoft Edge e Internet Explorer. (NEO-11257)
* Se ha corregido un problema con la personalización de vínculos de imágenes en las entregas LINE. (NEO-11077)
* Se ha corregido un problema que impedía que el mecanismo de generación de secuencia de ID funcionara correctamente. (NEO-11115)
* Se ha corregido un problema que impedía que las solicitudes de privacidad (RGPD) funcionen al utilizar un área de nombres personalizada con una clave de reconciliación de tipo entero. (NEO-11123)
* Se ha corregido un error que se producía al utilizar la opción **[!UICONTROL Distribution of values]** en las actividades de flujo de trabajo **[!UICONTROL Query]**. (NEO-10958)
* Se ha corregido un problema que se producía al sincronizar los espacios de oferta de la instancia de marketing a la instancia de interacción. (NEO-11162)
* Se ha mejorado la administración de los índices de nombres largos posterior a la actualización

## Versión 18.4.2: compilación 8932{#release-18-4-2-build-8932}

22 de mayo de 2018

**Mejoras**

* Se ha corregido un problema que impedía que la actualización de Windows Server funcionara correctamente.
* Se ha corregido un problema en la actividad **[!UICONTROL Survey Result]** al utilizar datos almacenados en XML. El informe se mostraba incorrectamente. (NEO-10816)
* Se ha corregido un problema de rendimiento que podría ocurrir con el proceso de inMail al utilizar un servidor de correo de rebote. (NEO-10641)
* Se ha corregido un problema con la actualización de base de datos que se podría producir al actualizar más de 1000 esquemas.

## Versión 18.4: compilación 8931{#release-18-4-build-8931}

24 de abril de 2018

**Novedades**

<table> 
 <thead> 
  <tr> 
   <th> Funcionalidad<br /> </th> 
   <th> Descripción<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Reglamento General de Protección de Datos.<br /> </td> 
   <td> <p>El Reglamento General de Protección de Datos (RGPD) es la nueva normativa sobre privacidad de la Unión Europea que unifica y moderniza los requisitos de protección de datos y entrará en vigencia el 25 de mayo de 2018. El RGPD se aplica a los clientes de Adobe Campaign que albergan datos de sujetos de datos que residan en la UE.</p> <p>Además de las funcionalidades de privacidad disponibles en Adobe Campaign (incluida la administración de consentimiento, configuración de retención de datos y funciones de usuario), estamos tomando esta oportunidad en nuestro rol como procesador de datos para incluir funcionalidades adicionales, para ayudar a facilitar su preparación como controlador de datos para ciertas solicitudes de RGPD:</p> 
    <ul> 
     <li> <p>Derecho de acceso: permite que el sujeto de datos reciba una copia de sus datos personales recopilados por los controladores de datos, incluso los datos almacenados en Adobe Campaign.</p> </li> 
     <li> <p>Derecho a borrado: autoriza al sujeto de datos a que sus datos personales recopilados por los controladores de datos se borren, lo que incluye datos almacenados en Adobe Campaign.</p> </li> 
    </ul> Para obtener más información, consulte la <a href="https://helpx.adobe.com/es/campaign/kb/acc-privacy.html">documentación detallada</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Perfiles activos<br /> </td> 
   <td> <p>Adobe Campaign ahora proporciona la lista de perfiles activos, actualizados mensualmente a través de un flujo de trabajo dedicado.</p> <p>Para obtener más información, consulte la <a href="../../platform/using/about-profiles.md#active-profiles">documentación detallada</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> Mejora del conector de Android<br /> </td> 
   <td> <p>El conector Android se ha mejorado para ofrecer un mayor rendimiento. </p> <p>Para obtener más información, consulte la <a href="../../delivery/using/configuring-the-mobile-application.md">documentación detallada</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Mejoras de seguridad**

* La expansión de entidades externas está desactivada para evitar ataques potenciales de usuarios no autenticados. (NEO-10173)
* Se han endurecido los permisos para impedir que los usuarios estándar cambien los parámetros de configuración de la instancia, como URL de acceso a la aplicación, configuración de LDAP, etc. (NEO-10171)
* Se ha corregido un problema que pudiera revelar la información confidencial mediante los seguimientos de segmentación. Los detalles de error ahora se registran en el proceso de finalización a una ubicación inaccesible desde la red externa. (NEO-10176)
* Se han endurecido los permisos para impedir que los usuarios estándar vean los documentos cargados o paquetes exportados de un administrador. (NEO-10170)

**Mejoras**

* **Canal LINE: mejoras en la arquitectura**: Al igual que sucede con los demás canales de Adobe Campaign, el canal LINE ahora se admite en todos los tipos de implementación: alojada, híbrido y locales.
* **Generación automática de secuencias**: El mecanismo de generación de ID se ha mejorado para aumentar la duración de las instancias de Campaign con grandes cantidades de objetos. Para obtener más información, consulte esta [nota técnica](https://helpx.adobe.com/es/campaign/kb/sequence_auto_generation.html).

**Otros cambios**

* Hay disponible un nuevo modo para la importación de paquetes mediante la línea de comandos, lo que permite dependencias circulares (no recomendado para paquetes grandes). Consulte la sección “Evoluciones técnicas” para obtener más información. (NEO-8979)
* Se mejoró el rendimiento para una gran cantidad de datos en Teradata y Se ha corregido un problema que impedía mostrar el valor correcto de datos procesados en el registro. (NEO-10429)
* La importación de audiencias desde el Gestor de colaboradores ahora funciona con archivos divididos. Anteriormente, el último archivo del segmento se importó mediante el flujo de trabajo técnico Importar audiencia compartida. (NEO-10156)
* En Windows, la ruta de instalación predeterminada del servidor Campaign ha cambiado. Al iniciar la configuración de la versión de 64 bits, la ruta de instalación predeterminada ahora es: **C:\Archivos de programa\Adobe\Adobe Campaign Classic v7** en lugar de **C:\Archivos de programa (x86)\Adobe\Adobe Campaign Classic v7**.
* Las reglas MX predeterminadas se han mejorado para incluir más dominios y optimizar el rendimiento.
* Restricciones de acceso mejoradas en la llamada SOAP del asistente de implementación (xtk:serverOptions#SaveOptions).
* La biblioteca obsoleta weka.jar se ha eliminado y la biblioteca OpenSSL se ha actualizado para la mejorar la seguridad.
* Se mejoró el flujo de trabajo técnico de facturación para asegurar la eficacia de las instancias.
* Se ha restaurado la capacidad para que los administradores definan o restablezcan la contraseña de cualquier operador. Para ello, haga clic con el botón derecho del ratón en un operador, seleccione **[!UICONTROL Actions]** >**[!UICONTROL Reset password]** y establezca la nueva contraseña del operador. Recomendamos que los operadores cambien su contraseña cuando vuelvan a conectarse por primera vez. Para obtener más información, consulte la [documentación detallada](../../production/using/lost-password.md).
* Para admitir la nueva función de inquilinos múltiples en Adobe Target, ahora se puede añadir un nuevo parámetro “at_property” a las URL al configurar opciones y cuentas externas para la integración con Target. El valor que se utiliza para este parámetro se puede encontrar en Adobe Target y se utilizará Campaign al realizar llamadas a Target. Para obtener más información, consulte la [documentación detallada](../../integrations/using/inserting-a-dynamic-image.md).
* Ahora puede especificar una página de aterrizaje predeterminada para abrirla al hacer clic en una imagen ofrecida por Adobe Target. Anteriormente, al hacer clic en la imagen principal el conjunto de imágenes predeterminado al crear el correo electrónico. Para obtener más información, consulte la [documentación detallada](../../integrations/using/inserting-a-dynamic-image.md).
* Se agregó la casilla de verificación **Habilitar los trazos** de niebla en la cuenta externa para forzar el seguimiento de la salida. Para obtener más información, consulte la [documentación detallada](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Evoluciones técnicas**

queryDef

queryDef se ha modificado acerca de la cláusula “orderBy”. Antes del cambio, la clave principal de la tabla de consulta se agregaría implícitamente a las cláusulas “orderBy”. En algunos motores de base de datos (postgresql al menos), impide el uso de índices (todos los campos de la cláusula orderBy deben estar cubiertos por el mismo índice). Si queda pendiente de este comportamiento, tendrá que añadir explícitamente la clave principal en la cláusula “orderBy”.

Por ejemplo, si tiene la siguiente consulta:

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
     <node expr="@logDate"/>
   </orderBy>
</queryDef>`
```

Se entregaría implícitamente como (antes de que 18.4 cambie):

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitely added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

una función urlEncode

La función de JavaScript “urlEncode” no funcionaba correctamente para caracteres no ASCII. Se ha corregido y ahora debería funcionar con todos los caracteres Unicode (incluidos los caracteres japoneses). Si confía en el comportamiento “urlEncode” para el carácter no ASCII, tendrá que adaptar el código.

Empaquetar el nuevo modo de importación

Hay disponible un nuevo modo para la importación de paquetes mediante la línea de comandos, lo que permite dependencias circulares (no recomendado para paquetes grandes). Se mantiene la funcionalidad existente. Para estos paquetes con dependencias circulares, se ha añadido un nuevo indicador **-usejs** a la importación del paquete de la línea de comandos. Cuando se ejecuta, utilizará JSEngine como cuando se realiza la importación del paquete desde la interfaz.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**Parches**

* Se ha corregido un problema con la sincronización al replicar los registros de entrega y seguimiento de Adobe Campaign Standard a Adobe Campaign Classic. (NEO-10023)
* Se ha corregido un problema con el control de las tablas Error y Registro en Teradata cuando un flujo de trabajo de ETL se reanuda tras producirse un error en una operación de carga rápida. Las tablas de error y registro se han eliminado correctamente cada vez que se reanuda el flujo de trabajo. (NEO-10672)
* Se ha corregido un problema posterior a la actualización para instalar automáticamente el paquete Hive (necesario para Hadoop) si está instalado el paquete FDA. (NEO-10592)
* Se ha corregido un error que trataba los dominios no válidos como un error **no definido**. (NEO-10248)
* Se ha corregido un problema que duplicaba registros en la tabla deliveryLogStats al realizar entregas push de Android. (NEO-10234)
* Se ha corregido un problema que podría provocar que algunos formatos de código de barra no se puedan leer con escáneres de códigos de barra. (NEO-10125)
* Se ha corregido un problema con la función JavaScript “urlEncode” al utilizar caracteres no ASCII. Consulte la sección “Evoluciones técnicas” para obtener más información. (NEO-10123)
* Se ha corregido un problema que se producía al ejecutar una consulta que incluye funciones sha256 en bases de datos Teradata. (NEO-10119)
* Se corrigieron errores de memoria de flujo de trabajo que podrían producirse en la actividad de SalesForce al utilizar tablas SalesForce muy grandes. (NEO-9900)
* Se ha corregido un problema con la opción **Generar complemento** en las actividades de flujo de trabajo de destino al utilizar FDA. (NEO-9878)
* Se ha corregido un problema que podría provocar que las métricas **Procesado** y de **Éxito** no se actualicen en la instancia de marketing al utilizar intermediarios. (NEO-9454)
* Se corrigieron reglas de no reproposición de interacción cuando se acumulan más de 10 000 ofertas en total en la plataforma (NEO-9352)
* Se ha corregido un problema que podría evitar especificar el destino de una entrega al utilizar un archivo externo XML. (NEO-9312)
* Se ha corregido un problema que podría provocar errores de flujo de trabajo al ejecutar una hipótesis en una oferta y actualizar el estado de la propuesta. (NEO-9304)
* Se corrigieron errores que se producen durante el análisis de la entrega al utilizar reglas de presión basadas en un atributo de la asignación de entrega de Android. (NEO-9202)
* Se ha corregido un problema que se producía al ordenar columnas en la lista de destinatarios que podría provocar problemas de rendimiento. Para obtener más información sobre las modificaciones de queryDef, consulte la sección “Evoluciones técnicas” más abajo. (NEO-9042)
* Se ha corregido un problema en el cual los vínculos de un correo electrónico de aprobación podrían señalar a una URL de inicio de sesión incorrecta, especialmente cuando se utiliza un tipo de inicio de sesión de Federated ID. (NEO-9011)
* Se ha corregido un problema que podría provocar la visualización de fechas incorrectas en los selectores de fecha de los informes para ciertas zonas horarias. (NEO-9007)
* Se ha corregido un problema que impedía ver el destino de una salida cuando se utiliza una base de datos de SQL FDA. (NEO-8924)
* Se ha corregido un problema que provocaba que el conector de MS Dynamics CRM no logre extraer los datos durante los primeros 7 días del mes. (NEO-8803)
* Se ha corregido un error en la integración de Analytics que impedía a los usuarios incluir caracteres internacionales. (NEO-8719)
* Se ha corregido un problema que podría permitir la edición del flujo de trabajo sin los derechos adecuados. (NEO-8708)
* Se ha corregido un problema con FDA sobre direcciones HTTP cuando se utiliza el Centro de mensajes en una arquitectura híbrida, con el fin de establecer la conexión o pérdida de conexión (tiempo de espera). (NEO-8438)
* Se corrigieron los errores de flujo de trabajo que se producen en la actividad de consulta incremental para los ID negativos. (NEO-8229)
* Se ha corregido un problema que podría provocar la visualización de barras de desplazamiento doble en determinadas pantallas. (NEO-8208)
* Se ha corregido un problema que provocaba que se mostrara un mensaje de error al ejecutar el asistente de estructura de la base de datos de actualización. El componente PostUpgrade ejecutará un nombre de índices con nombres de más de 30. Tenga en cuenta que para tablas grandes, la sustitución de índices tardará un tiempo. (NEO-7983)
* Se ha corregido un problema que se producía cuando los registros de seguimiento no se sincronizaban correctamente a partir de la instancia de ejecución del Centro de mensajes para controlar la instancia. (NEO-7286)
* Se ha corregido un problema de rendimiento con la actividad de enriquecimiento de la oferta. (NEO-7263)
* Se ha corregido un problema que impedía utilizar la función DaysAgo al consultar la base de datos Redshift a través de FDA. (NEO-7099)
* Se ha corregido una regresión en la gestión de datos que impedía la creación de índices en actividades de flujo de trabajo de enriquecimiento.
* Se ha solucionado un problema que podría ocurrir al crear recursos externos con el título @id.
* Se ha corregido un problema que se podía producir al cargar archivos comprimidos a través de un servidor FTP o al cargar archivos con caracteres comodín en el nombre del archivo.
* Se ha corregido un problema con las enumeraciones de tipos base largas en los recursos personalizados externos creados en Campaign Standard.
* Se ha corregido un problema que podría provocar la entrega de SMS incluso cuando la conexión con el proveedor falla en las pérdidas de SMS.
* Se ha corregido un error que permite que la conexión SMTP se bloquee indefinidamente.
* Se ha corregido un problema con las reglas de tipología de presión durante la preparación del mensaje al utilizar una asignación LINE o cuando los esquemas de filtrado y segmentación son diferentes.
