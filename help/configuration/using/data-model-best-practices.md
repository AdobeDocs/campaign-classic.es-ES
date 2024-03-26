---
product: campaign
title: Prácticas recomendadas del modelo de datos
description: Aprenda a trabajar con el modelo de datos de Campaign Classic
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
feature: Data Model
exl-id: 9c59b89c-3542-4a17-a46f-3a1e58de0748
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '4020'
ht-degree: 1%

---

# Prácticas recomendadas del modelo de datos{#data-model-best-practices}

Este documento describe las recomendaciones clave al diseñar el modelo de datos de Adobe Campaign.

Para comprender mejor las tablas integradas de Campaign y su interacción, consulte [esta sección](../../configuration/using/about-data-model.md) sección.

Leer más [esta documentación](../../configuration/using/about-schema-reference.md) para empezar a usar los esquemas de Campaign. Obtenga información sobre cómo configurar esquemas de extensión para ampliar el modelo de datos conceptuales de la base de datos de Adobe Campaign en [este documento](../../configuration/using/about-schema-edition.md).

## Información general {#overview}

El sistema Adobe Campaign es extremadamente flexible y se puede ampliar más allá de la implementación inicial. Sin embargo, aunque las posibilidades son infinitas, es fundamental tomar decisiones sabias y construir bases sólidas para empezar a diseñar el modelo de datos.

Este documento proporciona casos de uso comunes y prácticas recomendadas para aprender a crear correctamente su herramienta Adobe Campaign.

## Arquitectura del modelo de datos {#data-model-architecture}

Adobe Campaign es un potente sistema de administración de campañas en canales múltiples que le ayuda a alinear sus estrategias en línea y sin conexión para crear experiencias personalizadas con los clientes.

### Enfoque centrado en el cliente {#customer-centric-approach}

Aunque la mayoría de los proveedores de correo electrónico se comunican con los clientes mediante un enfoque centrado en listas, Adobe Campaign depende de una base de datos relacional para aprovechar una vista más amplia de los clientes y sus atributos.

Este enfoque centrado en el cliente se muestra en el gráfico siguiente. El **Destinatario** tabla en gris representa la tabla cliente principal alrededor de la cual se está creando todo:

![](assets/customer-centric-data-model.png)

Para acceder a la descripción de cada tabla, vaya a **[!UICONTROL Admin > Configuration > Data schemas]**, seleccione un recurso de la lista y haga clic en **[!UICONTROL Documentation]** pestaña.

El modelo de datos predeterminado de Adobe Campaign se presenta en [este documento](../../configuration/using/data-model-description.md).

>[!NOTE]
>
>Adobe Campaign Classic permite crear una tabla de cliente personalizada. Sin embargo, en la mayoría de los casos, se recomienda aprovechar el estándar [Tabla de destinatarios](../../configuration/using/about-data-model.md#default-recipient-table) que ya tiene tablas y funciones adicionales creadas previamente.

### Datos para Adobe Campaign {#data-for-campaign}

¿Qué datos deben enviarse a Adobe Campaign? Es fundamental determinar los datos necesarios para las actividades de marketing.

>[!NOTE]
>
>Adobe Campaign no es un almacén de datos ni una herramienta de creación de informes. Por lo tanto, no intente importar todos los clientes posibles y su información asociada en Adobe Campaign, ni importe datos que solo se utilizarán para crear informes.

Para tomar la decisión de si un atributo sería necesario o no en Adobe Campaign, pregúntese si caería dentro de una de estas categorías:

* Atributo utilizado para **segmentación**
* Atributo utilizado para **procesos de administración de datos** (cálculo acumulado, por ejemplo)
* Atributo utilizado para **personalización**

Si no entra en ninguna de estas situaciones, lo más probable es que no necesite este atributo en Adobe Campaign.

### Elección de tipos de datos {#data-types}

Para garantizar la buena arquitectura y el rendimiento de su sistema, siga las prácticas recomendadas a continuación para configurar los datos en Adobe Campaign.

* Una tabla grande debe tener principalmente campos numéricos y contener vínculos a tablas de referencia (cuando se trabaja con una lista de valores).
* El **expr** El atributo permite definir un atributo de esquema como un campo calculado en lugar de como un valor físico definido en una tabla. Esto permite acceder a la información en un formato diferente (como por ejemplo, edad y fecha de nacimiento) sin necesidad de almacenar ambos valores. Esta es una buena manera de evitar la duplicación de campos. Por ejemplo, la tabla Destinatario utiliza una expresión para el dominio, que ya está presente en el campo de correo electrónico.
* Sin embargo, cuando el cálculo de la expresión es complejo, no se recomienda utilizar la variable **expr** como cálculo sobre la marcha puede afectar al rendimiento de las consultas.
* El **XML** El tipo es una buena manera de evitar la creación de demasiados campos. Pero también ocupa espacio en disco, ya que utiliza una columna CLOB en la base de datos. También puede generar consultas SQL complejas y afectar al rendimiento.
* La longitud de un **cadena** El campo siempre debe definirse con la columna. De forma predeterminada, la longitud máxima en Adobe Campaign es 255, pero Adobe recomienda mantener el campo más corto si ya sabe que el tamaño no excederá una longitud más corta.
* Es aceptable tener un campo más corto en Adobe Campaign que en el sistema de origen si está seguro de que el tamaño en el sistema de origen se ha sobreestimado y no se alcanzaría. Esto podría significar una cadena más corta o un entero más pequeño en Adobe Campaign.

### Elección de campos {#choice-of-fields}

Es necesario almacenar un campo en una tabla si tiene un propósito de segmentación o personalización. En otras palabras, si un campo no se utiliza para enviar un correo electrónico personalizado o se utiliza como criterio en una consulta, ocupa espacio en disco mientras que no es útil.

Para instancias híbridas y locales, FDA (Acceso de datos federado, una función opcional que permite acceder a datos externos) cubre la necesidad de agregar un campo &quot;sobre la marcha&quot; durante un proceso de campaña. No es necesario importar todo si tiene FDA. Para obtener más información, consulte [Acerca del acceso de datos federado](../../installation/using/about-fda.md).

### Elección de claves {#choice-of-keys}

Además de las **autopk** definido de forma predeterminada en la mayoría de las tablas, debe considerar la posibilidad de agregar algunas claves lógicas o empresariales (número de cuenta, número de cliente, etc.). Se puede utilizar más adelante para importaciones/reconciliación o paquetes de datos. Para obtener más información, consulte [Identificadores](#identifiers).

Las claves eficientes son esenciales para el rendimiento. Los tipos de datos numéricos siempre deben preferirse como claves para las tablas.

Para la base de datos de SQLServer, podría considerar el uso de &quot;índice agrupado&quot; si se necesita rendimiento. Dado que Adobe no gestiona esto, debe crearlo en SQL.

### Tablespaces dedicados {#dedicated-tablespaces}

El atributo tablespace del esquema permite especificar un tablespace dedicado para una tabla.

El asistente de instalación le permite almacenar objetos por tipo (datos, temporales e índices).

Los tablespaces dedicados son mejores para la partición, las reglas de seguridad y permiten una administración fluida y flexible, una mejor optimización y rendimiento.

## Identificadores {#identifiers}

Los recursos de Adobe Campaign tienen tres identificadores y es posible añadir uno adicional.

En la tabla siguiente se describen estos identificadores y su propósito.

| Identificador | Descripción | Prácticas recomendadas |
|--- |--- |--- |
| Identificación | <ul><li>El ID es la clave primaria física de una tabla de Adobe Campaign. Para las tablas listas para usarse, se trata de un número generado de 32 bits a partir de una secuencia</li><li>Este identificador suele ser único para una instancia de Adobe Campaign específica. </li><li>Un ID generado automáticamente puede ser visible en una definición de esquema. Busque en *autopk=&quot;true&quot;* atributo.</li></ul> | <ul><li>Los identificadores generados automáticamente no deben utilizarse como referencia en un flujo de trabajo o en una definición de paquete.</li><li>No se debe dar por hecho que el ID siempre será un número creciente.</li><li>El ID de una tabla predeterminada es un número de 32 bits y no se debe cambiar este tipo. Este número se toma de una &quot;secuencia&quot; cubierta en la sección con el mismo nombre.</li></ul> |
| Nombre (o nombre interno) | <ul><li>Esta información es un identificador único de un registro de una tabla. Este valor se puede actualizar de forma manual, normalmente con un nombre generado.</li><li>Este identificador mantiene su valor cuando se implementa en una instancia diferente de Adobe Campaign y no debe estar vacío.</li></ul> | <ul><li>Cambie el nombre del registro generado por Adobe Campaign si el objeto debe implementarse de un entorno a otro.</li><li>Cuando un objeto tiene un atributo namespace (*esquema* por ejemplo), este área de nombres común se aprovechará en todos los objetos personalizados creados. Algunas áreas de nombres reservadas no deben usarse: *nms*, *xtk*, *nl*, *ncl*, *crm*, *xxl*.</li><li>Cuando un objeto no tiene ningún área de nombres (*workflow* o *envío* por ejemplo), esta noción de área de nombres se agregaría como prefijo de un objeto de nombre interno: *namespaceMyObjectName*.</li><li>No utilice caracteres especiales como el espacio &quot;&quot;, punto y coma &quot;:&quot; o guión &quot;-&quot;. Todos estos caracteres se sustituirían por un guion bajo &quot;_&quot; (carácter permitido). Por ejemplo, &quot;abc-def&quot; y &quot;abc:def&quot; se almacenarían como &quot;abc_def&quot; y se sobrescribirían mutuamente.</li></ul> |
| Etiqueta | <ul><li>La etiqueta es el identificador comercial de un objeto o registro en Adobe Campaign.</li><li>Este objeto permite espacios y caracteres especiales.</li><li>No garantiza la exclusividad de un registro.</li></ul> | <ul><li>Se recomienda determinar una estructura para las etiquetas de objetos.</li><li>Esta es la solución más fácil de usar para identificar un registro u objeto para un usuario de Adobe Campaign.</li></ul> |

## Claves internas personalizadas {#custom-internal-keys}

Las claves principales son necesarias para cada tabla creada en Adobe Campaign.

La mayoría de las organizaciones están importando registros de sistemas externos. Aunque la clave física de la tabla de destinatarios es el atributo &quot;id&quot;, es posible determinar además una clave personalizada.

Esta clave personalizada es la clave principal del registro real en el sistema externo que alimenta a Adobe Campaign.

Cuando una tabla predeterminada tiene una clave interna y una autopk, la clave interna se establece como un índice único en la tabla de la base de datos física.

Al crear una tabla personalizada, tiene dos opciones:
* Una combinación de clave generada automáticamente (id) y clave interna (personalizada). Esta opción es interesante si la clave del sistema es una clave compuesta o no un número entero. Los enteros proporcionarán un mayor rendimiento en las tablas grandes y se unirán con otras tablas.
* Uso de la clave principal como clave principal externa del sistema. Esta solución suele ser la preferida, ya que simplifica el método de importación y exportación de datos, con una clave coherente entre los distintos sistemas. La selección automática debe deshabilitarse si la clave se denomina &quot;id&quot; y se espera que se rellene con valores externos (no generados automáticamente).

>[!IMPORTANT]
>
>No se debe utilizar autopk como referencia en flujos de trabajo.

## Secuencias {#sequences}

La clave principal de Adobe Campaign es un ID generado automáticamente para todas las tablas predeterminadas y puede ser el mismo para las tablas personalizadas. Para obtener más información, consulte [esta sección](#identifiers).

Este valor se toma de lo que se denomina **Secuencia**, que es un objeto de base de datos utilizado para generar una secuencia numérica.

Existen dos tipos de secuencias:
* **Compartido**: más de una tabla elegiría su id de la misma secuencia. Significa que si una tabla utiliza un ID &quot;X&quot;, ninguna otra tabla que comparta la misma secuencia tendría un registro con ese ID &quot;X&quot;. **XtkNewId** es la secuencia compartida predeterminada disponible en Adobe Campaign.
* **Dedicado**: solo una tabla está eligiendo sus ID de la secuencia. El nombre de la secuencia generalmente contendría el nombre de la tabla.

>[!IMPORTANT]
>
>La secuencia es un valor entero de 32 bits, con un número máximo finito de valores disponibles: 2140 millones. Después de alcanzar el valor máximo, la secuencia vuelve a 0 para reciclar los ID.
>
>Si no se han purgado los datos antiguos, el resultado será una infracción de clave única, que se convierte en un bloqueador para el estado y el uso de la plataforma. Adobe Campaign no podría enviar comunicaciones (cuando afecta a la tabla de registro de envíos) y el rendimiento se vería muy afectado.

Por lo tanto, un cliente que envíe 6000 millones de correos electrónicos al año con un periodo de retención de 180 días para sus registros se quedaría sin ID en 4 meses. Para evitar este desafío, asegúrese de tener la configuración de depuración según sus volúmenes. Para obtener más información, consulte [esta sección](#data-retention).

Cuando se crea una tabla personalizada en Adobe Campaign con una clave principal como PK automática, se debe asociar sistemáticamente una secuencia dedicada personalizada a esa tabla.

De forma predeterminada, una secuencia personalizada tendrá valores que oscilan entre +1.000 y +2,1BB. Técnicamente, es posible obtener una gama completa de 4BB habilitando identificadores negativos. Esto debe utilizarse con cuidado y se perderá un ID al pasar de números negativos a positivos: Adobe Campaign suele ignorar el registro 0 en las consultas SQL generadas.

Para obtener más información sobre el agotamiento de secuencias, consulte [este vídeo](https://helpx.adobe.com/customer-care-office-hours/campaign/sequences-exhaustion-campaign-classic.html).

## Índices {#indexes}

Los índices son esenciales para el rendimiento. Al declarar una clave en el esquema, Adobe crea automáticamente un índice en los campos de la clave. También puede declarar más índices para las consultas que no utilicen la clave.

Adobe recomienda definir índices adicionales, ya que puede mejorar el rendimiento.

Sin embargo, tenga en cuenta lo siguiente:

* El uso del índice está enlazado a su patrón de acceso. La optimización de la indexación suele ser una parte clave del diseño de la base de datos y deben gestionarla expertos. La adición de índices suele ser un flujo de trabajo iterativo adjunto al mantenimiento de la base de datos. Se lleva a cabo con el tiempo, paso a paso, para abordar los problemas de rendimiento cuando se producen.
* Los índices aumentan el tamaño total de la tabla (para almacenar el índice en sí).
* Añadir un índice en las columnas puede mejorar el rendimiento del acceso de lectura de datos (SELECT), pero puede disminuir el rendimiento del acceso de escritura de datos (UPDATE).
* Dado que esto afecta al rendimiento durante la inserción de datos, los índices deben tener un tamaño y un número limitados.
* No agregue índices cuando no sea necesario. Asegúrese de que sea necesario y que aumente el rendimiento general de las consultas (prueba y aprendizaje).
* En términos generales, un índice es eficaz si sabe que las consultas no recuperarán más del 10 % de los registros.
* Seleccione cuidadosamente los índices que debe definir.
* No elimine los índices nativos de las tablas predeterminadas.

<!--When you are performing an initial import with very high volumes of data insert in Adobe Campaign database, it is recommended to run that import without custom indexes at first. It will allow to accelerate the insertion process. Once you’ve completed this important import, it is possible to enable the index(es).-->

### Ejemplo

La administración de índices puede llegar a ser muy compleja, por lo que es importante comprender cómo funcionan. Para ilustrar esta complejidad, veamos un ejemplo básico, como buscar destinatarios filtrando por nombre y apellido. Para ello, haga lo siguiente:
1. Vaya a la carpeta que muestra todos los destinatarios de la base de datos. Para obtener más información, consulte [Administración de perfiles](../../platform/using/managing-profiles.md).
1. Haga clic con el botón derecho en **[!UICONTROL First name]** field.
1. Seleccione **[!UICONTROL Filter on this field]**.

   ![](assets/data-model-index-example.png)

1. Repita esta operación para el **[!UICONTROL Last name]** field.

Los dos filtros correspondientes se añaden en la parte superior de la pantalla.

![](assets/data-model-index-search.png)

Ahora puede filtrar la búsqueda en **[!UICONTROL First name]** y **[!UICONTROL Last name]** según las distintas condiciones de filtro.

Ahora, para acelerar la búsqueda en estos filtros, puede añadir índices. Pero, ¿qué índices deben utilizarse?

>[!NOTE]
>
>Este ejemplo se aplica a los clientes alojados que utilizan una base de datos PostgreSQL.

La siguiente tabla muestra en qué casos se utilizan o no los tres índices descritos a continuación según el patrón de acceso mostrado en la primera columna.

| Criterios de búsqueda | Índice 1 (Nombre + Apellidos) | Índice 2 (solo nombre) | Índice 3 (solo apellidos) | Comentarios |
|--- |--- |--- |--- |--- |
| Nombre igual a &quot;Johnny&quot; | Utilizado | Utilizado | No se usa | Como el nombre está en la primera posición en el índice 1, se utilizará de todos modos: no es necesario añadir un criterio en el apellido. |
| El nombre es igual a &quot;Johnny&quot; Y el apellido es igual a &quot;Smith&quot; | Utilizado | No se usa | No se usa | Como ambos atributos se buscan en la misma consulta, solo se utilizará el índice que combine ambos atributos. |
| Apellido igual a &quot;Smith&quot; | No se usa | No se usa | Utilizado | Se tiene en cuenta el orden de los atributos en el índice. Si no coincide con este orden, es posible que no se utilice el índice. |
| El nombre empieza con &quot;John&quot; | Utilizado | Utilizado | No se usa | La &quot;búsqueda de la izquierda&quot; activará los índices. |
| El nombre termina con &quot;nny&quot; | No se usa | No se usa | No se usa | La &quot;búsqueda correcta&quot; desactivará los índices y se realizará un análisis completo. Algunos tipos de índice específicos podrían manejar este caso de uso, pero no están disponibles de forma predeterminada en Adobe Campaign. |
| El nombre contiene &quot;John&quot; | No se usa | No se usa | No se usa | Esta es una combinación de búsquedas &quot;izquierda&quot; y &quot;derecha&quot;. Debido a esto último, se desactivan los índices y se realiza un análisis completo. |
| El nombre es igual a &quot;john&quot; | No se usa | No se usa | No se usa | Los índices distinguen entre mayúsculas y minúsculas. Para que no distinga entre mayúsculas y minúsculas, debe crear un índice específico que incluya una función SQL como &quot;upper(firstname)&quot;. Debe hacer lo mismo con otras transformaciones de datos, como unemphasis(firstname). |

## Vínculos y cardinalidad {#links-and-cardinality}

### Vínculos {#links}

Tenga cuidado con la integridad &quot;propia&quot; en tablas grandes. La eliminación de registros que tienen tablas anchas en integridad &quot;propia&quot; puede detener la instancia. La tabla está bloqueada y las eliminaciones se realizan una por una. Por lo tanto, es mejor utilizar la integridad &quot;neutral&quot; en tablas secundarias que tengan grandes volúmenes.

Declarar un vínculo como una unión externa no es bueno para el rendimiento. El registro de ID cero emula la funcionalidad de unión externa. No es necesario declarar uniones externas si el vínculo utiliza la función autopk.

Aunque es posible unir cualquier tabla en un flujo de trabajo, Adobe recomienda definir vínculos comunes entre recursos directamente en la definición de la estructura de datos.

El vínculo debe definirse en consonancia con los datos reales de las tablas. Una definición incorrecta podría afectar a los datos recuperados mediante vínculos como, por ejemplo, la duplicación inesperada de registros.

Asigne un nombre al vínculo que sea coherente con el nombre de la tabla: el nombre del vínculo debe ayudar a comprender qué es la tabla distante.

No asigne un nombre a un vínculo con &quot;id&quot; como sufijo. Por ejemplo, asígnele el nombre &quot;transaction&quot; en lugar de &quot;transactionId&quot;.

De forma predeterminada, Adobe Campaign crea un vínculo con la clave principal de la tabla externa. Para una mayor claridad, es preferible definir explícitamente la unión en la definición del vínculo.

Se añade un índice a los atributos utilizados en un vínculo.

Los vínculos creado por y modificado por última vez están presentes en muchas tablas. Es posible deshabilitar el índice utilizando el atributo noDbIndex en el vínculo si la empresa no utiliza esta información.

### Cardinalidad {#cardinality}

Cuando diseñe un vínculo, asegúrese de que el registro de destino sea único cuando se haya declarado una relación 1-1. De lo contrario, la unión puede devolver varios registros cuando solo se espera uno. Esto provoca errores durante la preparación del envío cuando &quot;la consulta devuelve más filas de lo esperado&quot;. Establezca el nombre del vínculo con el mismo nombre que el esquema de destino.

Defina un vínculo con una cardinalidad (1-N) en el esquema del lado (1). Por ejemplo, la relación Destinatario (1) - (N) Transacción debe definirse en el esquema de transacción.

Tenga en cuenta que una cardinalidad inversa de un vínculo es (N) de forma predeterminada. Es posible definir un vínculo (1-1) añadiendo el atributo revCardinality=&#39;single&#39; a la definición del vínculo.

Si el vínculo inverso no debe ser visible para el usuario, puede ocultarlo con la definición del vínculo revLink=&#39;_NINGUNO_&#39;. Un buen caso de uso para esto es definir un vínculo desde el destinatario a la última transacción completada, por ejemplo. Solo necesita ver el vínculo del destinatario a la última transacción y no se requiere que ningún vínculo inverso sea visible desde la tabla de transacciones.

Los vínculos que realizan una unión externa (1-0..1) deben utilizarse con cuidado, ya que afectarán al rendimiento del sistema.

## Retención de datos: limpieza y depuración {#data-retention}

Adobe Campaign no es un almacén de datos ni una herramienta de creación de informes. Por lo tanto, para garantizar el buen rendimiento de la solución de Adobe Campaign, el crecimiento de la base de datos debe mantenerse bajo control. Para lograrlo, puede ser útil seguir algunas de las prácticas recomendadas a continuación.

De forma predeterminada, los registros de envío y seguimiento de Adobe Campaign tienen una duración de retención de 180 días. Se ejecuta un proceso de limpieza para eliminar cualquier registro anterior a ese.

* Si desea mantener los registros más tiempo, esta decisión debe tomarse con cuidado en función del tamaño de la base de datos y del volumen de mensajes enviados. Como recordatorio, la secuencia de Adobe Campaign es un entero de 32 bits.
* Se recomienda no tener más de 1000 millones de registros a la vez en estas tablas (aproximadamente el 50 % de los 2140 millones de ID disponibles) para limitar los riesgos de consumir todos los ID disponibles. Esto requerirá que algunos clientes reduzcan la duración de retención por debajo de 180 días.

Obtenga más información sobre la retención de datos en [Directrices de seguridad y privacidad de Campaign](../../platform/using/privacy-and-recommendations.md).

Descubra más información sobre el flujo de trabajo Limpieza de base de datos de Campaign [en esta sección](../../production/using/database-cleanup-workflow.md).

>[!IMPORTANT]
>
>Las tablas personalizadas no se depuran con el proceso de limpieza estándar. Aunque esto puede no ser necesario en el primer día, no olvide crear un proceso de depuración para las tablas personalizadas, ya que podría provocar desafíos de rendimiento.

Hay algunas soluciones para minimizar la necesidad de registros en Adobe Campaign:
* Exporte los datos en un almacén de datos fuera de Adobe Campaign.
* Genere valores agregados que utilicen menos espacio a la vez que sean suficientes para sus prácticas de marketing. Por ejemplo, no necesita el historial completo de transacciones de clientes en Adobe Campaign para realizar un seguimiento de las últimas compras.

Puede declarar el atributo &quot;deleteStatus&quot; en un esquema. Es más eficaz marcar el registro como eliminado y posponer la eliminación en la tarea de limpieza.

## Rendimiento {#performance}

Para garantizar un mejor rendimiento en cualquier momento, siga las prácticas recomendadas a continuación.

### Recomendaciones generales {#general-recommendations}

* Evite utilizar operaciones como &quot;CONTAINS&quot; en consultas. Si sabe lo que se espera y desea filtrar, aplique la misma condición con un operador &quot;EQUAL TO&quot; u otro operador de filtro específico.
* Evite unirse a campos no indexados al crear datos en flujos de trabajo.
* Intente y asegúrese de que los procesos de importación y exportación se produzcan fuera del horario laboral.
* Asegúrese de que haya un horario para todas las actividades diarias y apéguese al horario.
* Si uno o varios de los procesos diarios fallan y si es obligatorio ejecutarlos ese mismo día, asegúrese de que no haya procesos en conflicto ejecutándose cuando se inicie el proceso manual, ya que esto podría afectar el rendimiento del sistema.
* Asegúrese de que ninguna de las campañas diarias se ejecute durante el proceso de importación o cuando se ejecute cualquier proceso manual.
* Utilice una o varias tablas de referencia en lugar de duplicar un campo en cada fila. Al utilizar pares clave/valor, se prefiere elegir una clave numérica.
* Una cadena corta sigue siendo aceptable. Si las tablas de referencias ya están en su lugar en un sistema externo, la reutilización de las mismas facilitará la integración de datos con Adobe Campaign.

### Relaciones &quot;uno a varios&quot; {#one-to-many-relationships}

* El diseño de datos afecta la facilidad de uso y la funcionalidad. Si diseña el modelo de datos con muchas relaciones &quot;uno a varios&quot;, a los usuarios les resulta más difícil construir una lógica significativa en la aplicación. La lógica de filtro uno a varios puede resultar difícil para los especialistas en marketing no técnico de construir y comprender correctamente.
* Es bueno tener todos los campos esenciales en una tabla porque facilita a los usuarios la creación de consultas. A veces también es bueno para el rendimiento duplicar algunos campos entre tablas si se puede evitar una combinación.
* Algunas funcionalidades integradas no podrán hacer referencia a relaciones &quot;uno a varios&quot;, por ejemplo, la fórmula de ponderación de oferta y las entregas.

## Mesas grandes {#large-tables}

Adobe Campaign se basa en motores de base de datos de terceros. Según el proveedor, la optimización del rendimiento para tablas más grandes puede requerir un diseño específico.

A continuación se describen algunas prácticas recomendadas comunes que deben seguirse al diseñar el modelo de datos con tablas grandes y uniones complejas.

* Cuando utilice tablas de destinatarios personalizadas adicionales, asegúrese de tener una tabla de registro dedicada para cada asignación de entrega.
* Reduzca la cantidad de columnas, especialmente identificando las que no se utilizan.
* Optimice las relaciones del modelo de datos evitando uniones complejas, como uniones en varias condiciones o varias columnas.
* Para las claves de combinación, utilice siempre datos numéricos en lugar de cadenas de caracteres.
* Reduzca al máximo la profundidad de la retención de registros. Si necesita un historial más profundo, puede acumular cálculos o gestionar tablas de registro personalizadas para almacenar un historial más grande.

### Tamaño de las tablas {#size-of-tables}

El tamaño de la tabla es una combinación del número de registros y el número de columnas por registro. Ambos pueden afectar al rendimiento de las consultas.

* A **de pequeño tamaño** es similar a la tabla Delivery.
* A **tamaño medio** es el mismo tamaño que la tabla de destinatarios. Tiene un registro por cliente.
* A **de gran tamaño** es similar a la tabla Registro general. Tiene muchos registros por cliente.
Por ejemplo, si la base de datos contiene 10 millones de destinatarios, la tabla Registro general contiene entre 100 y 200 millones de mensajes, y la tabla Envío contiene algunos miles de registros.

En PostgreSQL, una fila no debe superar los 8 KB para evitar [BRINDIS](https://wiki.postgresql.org/wiki/TOAST) mecanismo. Por lo tanto, intente reducir lo más posible el número de columnas y el tamaño de cada fila para preservar el rendimiento óptimo del sistema (memoria y CPU).

El número de filas también afecta al rendimiento. La base de datos de Adobe Campaign no está diseñada para almacenar datos históricos que no se utilizan de forma activa con fines de segmentación o personalización; se trata de una base de datos operativa.

Para evitar cualquier problema de rendimiento relacionado con el alto número de filas, mantenga únicamente los registros necesarios en la base de datos. Cualquier otro registro debe exportarse a un almacén de datos de terceros y eliminarse de la base de datos operativa de Adobe Campaign.

Estas son algunas prácticas recomendadas con respecto al tamaño de las tablas:

* Diseñe tablas grandes con menos campos y más datos numéricos.
* No utilice un tipo de columna de número grande (por ejemplo: Int64) para almacenar números pequeños como valores booleanos.
* Elimine las columnas no utilizadas de la definición de tabla.
* No mantenga datos históricos o inactivos en la base de datos de Adobe Campaign (exportación y limpieza).

Este es un ejemplo.

![](assets/transaction-table-example.png)

En este ejemplo:
* El *Transacción* y *Elemento de transacción* las mesas son grandes: más de 10 millones.
* El *Product* y *Almacenar* las tablas son más pequeñas: menos de 10 000.
* La etiqueta del producto y la referencia se han colocado en el *Product* tabla.
* El *Elemento de transacción* La tabla solo tiene un vínculo a *Product* , que es numérica.
