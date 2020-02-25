---
title: Uso de la tabla Destinatarios de Adobe Campaign Classic
description: Descubra cómo utilizar la tabla de destinatarios lista para usar en Adobe Campaign Classic al diseñar su modelo de datos.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a8bfeaecc8a4832cac96f479ea1a0b11cd73c1e8

---


# Prácticas recomendadas del modelo de datos{#data-model-best-practices}

Este documento describe las recomendaciones clave al diseñar el modelo de datos de Adobe Campaign.

Para comprender mejor las tablas integradas de Campaign y su interacción, consulte la sección del modelo [de datos de](../../configuration/using/about-data-model.md) Campaign Classic.

Lea esta [documentación](../../configuration/using/about-schema-reference.md) para empezar a utilizar los esquemas de campañas. Obtenga información sobre cómo configurar esquemas de extensión para ampliar el modelo de datos conceptuales de la base de datos de Adobe Campaign en este [documento](../../configuration/using/about-schema-edition.md).

## Información general {#overview}

El sistema Adobe Campaign es extremadamente flexible y puede ampliarse más allá de la implementación inicial. Sin embargo, aunque las posibilidades son infinitas, es fundamental tomar decisiones acertadas y construir bases sólidas para empezar a diseñar el modelo de datos.

Este documento proporciona casos de uso comunes y prácticas recomendadas para aprender a diseñar correctamente la herramienta Adobe Campaign.

## Arquitectura del modelo de datos {#data-model-architecture}

Adobe Campaign Standard es un potente sistema de administración de campañas multicanal que puede ayudarle a alinear sus estrategias en línea y sin conexión para crear experiencias personalizadas con los clientes.

### Enfoque centrado en el cliente {#customer-centric-approach}

Aunque la mayoría de los proveedores de servicios de correo electrónico se comunican a los clientes mediante un enfoque centrado en las listas, Adobe Campaign depende de una base de datos relacional para aprovechar una vista más amplia de los clientes y sus atributos.

Este enfoque centrado en el cliente se muestra en el gráfico siguiente. La tabla **Destinatario** en gris representa la tabla de cliente principal alrededor de la cual se está generando todo:

![](assets/customer-centric-data-model.png)

Para acceder a la descripción de cada tabla, vaya a **[!UICONTROL Admin > Configuration > Data schemas]**, seleccione un recurso de la lista y haga clic en la **[!UICONTROL Documentation]** ficha.

El modelo de datos predeterminado de Adobe Campaign se presenta en este [documento](https://final-docs.campaign.adobe.com/doc/AC/en/technicalResources/_Datamodel_Description_of_the_main_tables.html).

>[!NOTE]
>
>Adobe Campaign Classic permite crear una tabla de cliente personalizada. Sin embargo, en la mayoría de los casos, se recomienda aprovechar la tabla [](../../configuration/using/default-recipient-table.md) Destinatario estándar que ya tiene tablas y funciones adicionales prediseñadas.

### Datos de Adobe Campaign {#data-for-campaign}

¿Qué datos se deben enviar a Adobe Campaign? Es fundamental determinar los datos necesarios para las actividades de marketing.

>[!NOTE]
>
>Adobe Campaign no es ni un almacén de datos ni una herramienta de generación de informes. Por lo tanto, no intente importar todos los clientes posibles y la información asociada a Adobe Campaign, ni importe datos que solo se utilizarán para generar informes.

Para tomar la decisión de si un atributo sería necesario o no en Adobe Campaign, pregunte si se incluiría en una de estas categorías:

* Atributo utilizado para la **segmentación**
* Atributo utilizado para procesos **de administración de** datos (cálculo agregado, por ejemplo)
* Atributo utilizado para la **personalización**

Si no se incluye en ninguno de estos elementos, lo más probable es que no necesite este atributo en Adobe Campaign.

## Elección de tipos de datos {#data-types}

Para garantizar una buena arquitectura y un buen rendimiento del sistema, siga las optimizaciones que se describen a continuación para configurar los datos en Adobe Campaign.

* Una tabla grande debe tener principalmente campos numéricos y contener vínculos a tablas de referencia (al trabajar con una lista de valores).
* El atributo **expr** permite definir un atributo de esquema como un campo calculado en lugar de un valor de conjunto físico en una tabla. Esto puede permitir el acceso a la información en un formato diferente (por ejemplo, en cuanto a la edad y la fecha de nacimiento) sin necesidad de almacenar ambos valores. Es una buena manera de evitar la duplicación de campos. Por ejemplo, la tabla Destinatario utiliza una expresión para el dominio, que ya está presente en el campo Correo electrónico.
* Sin embargo, cuando el cálculo de la expresión es complejo, no se recomienda usar el atributo **expr** porque el cálculo sobre la marcha puede afectar al rendimiento de las consultas.
* El tipo **XML** es una buena forma de evitar la creación de demasiados campos. Pero también ocupa espacio en disco porque utiliza una columna CLOB en la base de datos. También puede generar consultas SQL complejas y afectar al rendimiento.
* La longitud de un campo de **cadena** siempre debe definirse con la columna. De forma predeterminada, la longitud máxima en Adobe Campaign es 255, pero Adobe recomienda mantener el campo más corto si ya sabe que el tamaño no excederá una longitud más corta.
* Es aceptable tener un campo más corto en Adobe Campaign que en el sistema de origen si está seguro de que el tamaño del sistema de origen se sobreestimó y no se alcanzaría. Esto podría significar una cadena más corta o un número entero menor en Adobe Campaign.

## Identificadores {#identifiers}

Los recursos de Adobe Campaign tienen tres identificadores y es posible agregar un identificador adicional.

En la tabla siguiente se describen estos identificadores y su finalidad.

| Identifier | Descripción | Prácticas recomendadas |
|--- |--- |--- |
| Id | <ul><li>La ID es la clave principal física de una tabla de Adobe Campaign. Para las tablas integradas, se trata de un número generado de 32 bits a partir de una secuencia</li><li>Este identificador suele ser exclusivo de una instancia de Adobe Campaign específica. </li><li>Una identificación generada automáticamente puede ser visible en una definición de esquema. Busque el atributo *autopk=&quot;true&quot;* .</li></ul> | <ul><li>Los identificadores generados automáticamente no deben utilizarse como referencia en un flujo de trabajo o en una definición de paquete.</li><li>No se debe suponer que la identificación siempre será un número creciente.</li><li>El identificador de una tabla lista para usar es un número de 32 bits y este tipo no debe cambiarse. Este número se toma de una &quot;secuencia&quot; cubierta en la sección con el mismo nombre.</li></ul> |
| Nombre (o nombre interno) | <ul><li>Esta información es un identificador único de un registro de una tabla. Este valor se puede actualizar manualmente, generalmente con un nombre generado.</li><li>Este identificador mantiene su valor cuando se implementa en una instancia diferente de Adobe Campaign y no debe estar vacío.</li></ul> | <ul><li>Cambie el nombre del registro generado por Adobe Campaign si el objeto está diseñado para implementarse de un entorno a otro.</li><li>Cuando un objeto tiene un atributo de espacio de nombres (*esquema* , por ejemplo), este espacio de nombres común se aprovecha en todos los objetos personalizados creados. Algunos espacios de nombres reservados no deben usarse: *nms*, *xtk*.</li><li>Cuando un objeto no tiene espacio de nombres (*flujo de trabajo* o *entrega* , por ejemplo), esta noción de espacio de nombres se agregaría como prefijo de un objeto de nombre interno: *namespaceMyObjectName*.</li><li>No utilice caracteres especiales como espacio &quot;&quot;, semicolumna &quot;:&quot; o guión &quot;-&quot;. Todos estos caracteres se reemplazarían por un guión bajo &quot;_&quot; (carácter permitido). Por ejemplo, &quot;abc-def&quot; y &quot;abc:def&quot; se almacenarían como &quot;abc_def&quot; y se sobrescribirían entre sí.</li></ul> |
| Etiqueta | <ul><li>La etiqueta es el identificador comercial de un objeto o registro en Adobe Campaign.</li><li>Este objeto permite espacios y caracteres especiales.</li><li>No garantiza la singularidad de un registro.</li></ul> | <ul><li>Se recomienda determinar una estructura para las etiquetas de los objetos.</li><li>Esta es la solución más sencilla para identificar un registro u objeto para un usuario de Adobe Campaign.</li></ul> |

## Claves internas personalizadas {#custom-internal-keys}

Se requieren claves principales para cada tabla creada en Adobe Campaign.

La mayoría de las organizaciones están importando registros de sistemas externos. Aunque la clave física de la tabla Destinatario es el atributo &quot;id&quot;, también es posible determinar una clave personalizada.

Esta clave personalizada es la clave principal del registro real en el sistema externo que alimenta a Adobe Campaign.

Cuando una tabla lista para usar tiene una autoprueba y una clave interna, la clave interna se configurará como un índice único en la tabla de la base de datos física.

Al crear una tabla personalizada, tiene dos opciones:
* Combinación de clave generada automáticamente (ID) y clave interna (personalizada). Esta opción es interesante si la clave del sistema es una clave compuesta o no un entero. Los integradores proporcionarán un rendimiento más alto en las mesas grandes y se unirán a otras tablas.
* Usar la clave principal como clave principal del sistema externo. Esta solución suele ser preferible ya que simplifica el enfoque de importar y exportar datos, con una clave coherente entre los distintos sistemas. Se debe deshabilitar la opción Autopk si la clave se denomina &quot;id&quot; y se espera que se rellene con valores externos (no generados automáticamente).

>[!IMPORTANT]
>
>No se debe utilizar una autoprueba automática como referencia en los flujos de trabajo.

## Secuencias {#sequences}

La clave principal de Adobe Campaign es una identificación generada automáticamente para todas las tablas integradas y puede ser la misma para las tablas personalizadas. For more on this, see [this section](#identifiers).

Este valor se toma de lo que se denomina una **secuencia**, que es un objeto de base de datos utilizado para generar una secuencia numérica.

Existen dos tipos de secuencias:
* **Compartido**: más de una tabla seleccionaría su ID de la misma secuencia. Significa que si una tabla utiliza una ID &#39;X&#39;, ninguna otra tabla que comparta la misma secuencia tendrá un registro con esa ID &#39;X&#39;. **XtkNewId** es la secuencia compartida predeterminada disponible en Adobe Campaign.
* **Dedicado**: sólo una tabla está eligiendo sus ID de la secuencia. El nombre de la secuencia normalmente contendría el nombre de la tabla.

La secuencia es un valor entero de 32 bits, con un número máximo finito de valores disponibles: 2.140 millones. Después de alcanzar el valor máximo, la secuencia regresa a 0 para reciclar los identificadores. Si no se han depurado los datos antiguos, el resultado será una infracción de clave única, que se convertirá en un bloqueador del estado y uso de la plataforma. Adobe Campaign no podrá enviar comunicaciones (cuando afecte a la tabla del registro de entrega) y el rendimiento se verá muy afectado.

Por lo tanto, un cliente que envía 6.000 millones de correos electrónicos anualmente con un período de retención de 180 días para sus registros se quedaría sin ID en 4 meses. Para evitar este desafío, asegúrese de tener la configuración de purga según los volúmenes. For more on this, see [this section](#data-retention).

Cuando se crea una tabla personalizada en Adobe Campaign con una clave principal como autoPK, se debe asociar sistemáticamente una secuencia dedicada personalizada con esa tabla.

De forma predeterminada, una secuencia personalizada tendrá valores que oscilarán entre +1000 y +2,1BB. Técnicamente, es posible obtener una gama completa de 4BB habilitando identificadores negativos. Debe utilizarse con cuidado y se perderá una identificación al pasar de números negativos a positivos: Adobe Campaign Classic generalmente ignora el registro 0 en las consultas SQL generadas.

**Temas relacionados:**
* Para obtener más información sobre la función de generación **automática de** secuencias, consulte este [documento](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html).
* Para obtener más información sobre el agotamiento de secuencias, vea este [vídeo](https://helpx.adobe.com/customer-care-office-hours/campaign/sequences-exhaustion-campaign-classic.html).

## Índices {#indexes}

Los índices son esenciales para el rendimiento. Cuando se declara una clave en el esquema, Adobe creará automáticamente un índice en los campos de la clave. También puede declarar más índices para las consultas que no utilicen la clave.

Adobe recomienda definir índices adicionales, ya que puede mejorar el rendimiento.

Sin embargo, tenga en cuenta lo siguiente:

* El uso del índice está vinculado al patrón de acceso. La optimización de la indexación es a menudo una parte clave en el diseño de la base de datos y debe ser manejada por expertos. La adición de índices suele ser un flujo de trabajo iterativo asociado al mantenimiento de la base de datos. Se hace con el tiempo, paso a paso, para abordar los problemas de rendimiento cuando se producen.
* Los índices aumentan el tamaño total de la tabla (para almacenar el índice mismo).
* La adición de índice en columnas puede mejorar el rendimiento del acceso de lectura de datos (SELECT), pero puede reducir el rendimiento del acceso de escritura de datos (UPDATE).
* Dado que esto afecta al rendimiento durante la inserción de datos, los índices deben tener un tamaño y un número limitados.
* No agregue índices cuando no sea necesario. Asegúrese de que es necesario y aumenta el rendimiento general de las consultas (prueba y aprendizaje).
* En términos generales, un índice es eficiente si sabe que sus consultas no devolverán más del 10% de los registros.
* Seleccione cuidadosamente los índices que deben definirse.
* No elimine los índices nativos de las tablas listas para usar.

<!--When you are performing an initial import with very high volumes of data insert in Adobe Campaign database, it is recommended to run that import without custom indexes at first. It will allow to accelerate the insertion process. Once you’ve completed this important import, it is possible to enable the index(es).-->

## Vínculos y cardinalidad {#links-and-cardinality}

### Vínculos {#links}

Tenga cuidado con la integridad &quot;propia&quot; de las tablas grandes. La eliminación de registros que tienen tablas anchas con integridad &quot;propia&quot; puede detener la instancia. La tabla está bloqueada y las eliminaciones se realizan una por una. Así que es mejor usar integridad &quot;neutral&quot; en tablas secundarias que tienen grandes volúmenes.

Declarar un vínculo como una unión externa no es bueno para el rendimiento. El registro de id cero emula la funcionalidad de unión externa. No es necesario declarar las uniones externas si el enlace utiliza la autopk.

Aunque es posible unir cualquier tabla en un flujo de trabajo, Adobe recomienda definir vínculos comunes entre los recursos directamente en la definición de la estructura de datos.

El vínculo debe definirse en consonancia con los datos reales de las tablas. Una definición incorrecta podría afectar a los datos recuperados mediante vínculos, por ejemplo duplicando registros de forma inesperada.

Asigne un nombre coherente al vínculo con el nombre de la tabla: el nombre del vínculo debe ayudar a comprender qué es la tabla distante.

No asigne un nombre a un vínculo con &quot;id&quot; como sufijo. Por ejemplo: ponle el nombre &quot;transaction&quot; en lugar de &quot;transactionId&quot;.

De forma predeterminada, Adobe Campaign creará un vínculo con la clave principal de la tabla externa. Para una mayor claridad, es preferible definir explícitamente la combinación en la definición del vínculo.

Se agregará un índice a los atributos utilizados en un vínculo.

Los vínculos creados por y modificados por última vez están presentes en muchas tablas. Es posible desactivar el índice mediante el atributo noDbIndex del vínculo, si la empresa no utiliza esta información.

### Cardinalidad {#cardinality}

Al diseñar un vínculo, asegúrese de que el registro de destino sea único cuando se haya declarado una relación 1-1. De lo contrario, la combinación puede devolver varios registros cuando solo se espera uno. Esto produce errores durante la preparación de la entrega cuando &quot;la consulta devuelve más filas de las esperadas&quot;. Establezca el nombre del vínculo en el mismo nombre que el esquema de destino.

Defina un vínculo con una cardinalidad (1-N) en el esquema del lado (1). Por ejemplo, la relación Destinatario (1) - (N) Transacción debe definirse en el esquema de transacción.

Tenga en cuenta que la cardinalidad inversa de un vínculo es (N) de forma predeterminada. Es posible definir un vínculo (1-1) agregando el atributo revCardinality=&#39;single&#39; a la definición del vínculo.

Si el vínculo inverso no debe ser visible para el usuario, puede ocultarlo con la definición del vínculo revLink=&#39;_NONE_&#39;. Un buen caso de uso para esto es definir un vínculo entre el destinatario y la última transacción completada, por ejemplo. Solo necesita ver el vínculo del destinatario a la última transacción y no se requiere que el vínculo inverso esté visible desde la tabla de transacciones.

Los vínculos que realizan una unión externa (1-0..1) deben utilizarse con cuidado, ya que afectarán al rendimiento del sistema.

## Retención de datos: limpieza y purga {#data-retention}

Adobe Campaign no es ni un almacén de datos ni una herramienta de generación de informes. Por lo tanto, para garantizar un buen rendimiento de la solución Adobe Campaign, el crecimiento de la base de datos debe mantenerse bajo control. Para lograrlo, puede ser útil seguir algunas de las prácticas recomendadas a continuación.

De forma predeterminada, los registros de entrega y seguimiento de Adobe Campaign tienen una duración de retención de 180 días. Se ejecuta un proceso de limpieza para eliminar cualquier registro anterior al anterior.

* Si desea mantener los registros más largos, esta decisión debe tomarse cuidadosamente en función del tamaño de la base de datos y del volumen de mensajes enviados. Como recordatorio, la secuencia de Adobe Campaign es un entero de 32 bits.
* Se recomienda no tener más de mil millones de registros al mismo tiempo en estas tablas (alrededor del 50% de los 2,14 mil millones de identidades disponibles) para limitar los riesgos de consumir todas las identificaciones disponibles. Esto requerirá que algunos clientes reduzcan la duración de la retención por debajo de 180 días.

>[!IMPORTANT]
>
>Las tablas personalizadas no se purgan con el proceso de limpieza estándar. Si bien esto puede no ser necesario en el primer día, no olvide crear un proceso de purga para las tablas personalizadas, ya que esto podría provocar problemas de rendimiento.

Existen algunas soluciones para minimizar la necesidad de registros en Adobe Campaign:
* Exporte los datos en un almacén de datos fuera de Adobe Campaign.
* Genere valores agregados que utilicen menos espacio mientras sean suficientes para sus prácticas de mercadotecnia. Por ejemplo, no necesita el historial completo de transacciones con clientes en Adobe Campaign para realizar un seguimiento de las últimas compras.

## Rendimiento {#performance}

Para garantizar un mejor rendimiento en cualquier momento, siga las optimizaciones a continuación.

### Recomendaciones generales {#general-recommendations}

* Evite utilizar operaciones como &quot;CONTIENE&quot; en consultas. Si sabe para qué se espera y desea que se le filtre, aplique la misma condición con un &quot;EQUAL TO&quot; u otros operadores de filtro específicos.
* Evite unirse a campos no indexados al crear datos en flujos de trabajo.
* Intente asegurarse de que los procesos como la importación y la exportación se producen fuera del horario laboral.
* Asegúrese de que hay una programación para todas las actividades diarias y cumpla con la programación.
* Si uno o algunos de los procesos diarios fallan y es obligatorio ejecutarlos ese mismo día, asegúrese de que no haya procesos en conflicto que se ejecuten cuando se inicie el proceso manual, ya que esto podría afectar al rendimiento del sistema.
* Asegúrese de que ninguna de las campañas diarias se ejecuta durante el proceso de importación o cuando se ejecuta cualquier proceso manual.
* Utilice una o varias tablas de referencia en lugar de duplicar un campo en cada fila. Al utilizar pares clave/valor, es preferible elegir una clave numérica.
* Una cadena corta sigue siendo aceptable. Si las tablas de referencias ya están colocadas en un sistema externo, reutilizar el mismo facilitará la integración de datos con Adobe Campaign.

### Relaciones uno a varios {#one-to-many-relationships}

* El diseño de datos afecta a la funcionalidad y el uso. Si diseña el modelo de datos con muchas relaciones uno a varios, a los usuarios les resultará más difícil construir una lógica significativa en la aplicación. La lógica de filtro uno a varios puede resultar difícil para los especialistas en mercadotecnia no técnicos de construir y comprender correctamente.
* Es bueno tener todos los campos esenciales en una tabla porque facilita a los usuarios la creación de consultas. A veces también es bueno para el rendimiento duplicar algunos campos en tablas si se puede evitar una unión.
* Ciertas funcionalidades integradas no podrán hacer referencia a relaciones uno a varios, por ejemplo, fórmulas de Ponderación de Ofertas y Entregas.

### Tablas grandes {#large-tables}

A continuación se detallan algunas prácticas recomendadas que deben seguirse al diseñar el modelo de datos mediante tablas grandes y combinaciones complejas.

* Cuando utilice tablas de destinatarios personalizados adicionales, asegúrese de que tiene una tabla de registro dedicada para cada asignación de entrega.
* Reduzca el número de columnas, en particular identificándolas como no utilizadas.
* Optimice las relaciones del modelo de datos evitando las uniones complejas, como las uniones en varias condiciones o en varias columnas.
* Para las claves de unión, utilice siempre datos numéricos en lugar de cadenas de caracteres.
* Reduzca al máximo la profundidad de la retención de registros. Si necesita un historial más profundo, puede agregar cálculos y/o administrar tablas de registro personalizadas para almacenar un historial más grande.

Para ver prácticas recomendadas más detalladas sobre cómo optimizar el diseño de la base de datos para volúmenes más grandes, consulte Prácticas recomendadas del modelo de datos de [Campaign Classic](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).