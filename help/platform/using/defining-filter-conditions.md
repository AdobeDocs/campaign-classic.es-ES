---
solution: Campaign Classic
product: campaign
title: Definición de condiciones de filtro
description: Definición de condiciones de filtro
audience: platform
content-type: reference
topic-tags: creating-queries
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '3229'
ht-degree: 99%

---


# Definir condiciones de filtro{#defining-filter-conditions}

## Seleccione el operador {#choosing-the-operator}

Dentro de las condiciones de filtrado, es necesario vincular dos valores mediante un operador.

![](assets/query_editor_nveau_96.png)

A continuación se muestra una lista de los operadores disponibles:

<table> 
 <thead> 
  <tr> 
   <th> Operador<br /> </th> 
   <th> Objetivo<br /> </th> 
   <th> Ejemplo<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Equal to</span> <br /> </td> 
   <td> Devuelve un resultado idéntico a los datos introducidos en la segunda columna Valor.<br /> </td> 
   <td> <strong>Apellido (@lastName) igual a “Jones”</strong>, solo devuelve como resultado los destinatarios cuyo apellido sea Jones.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Greater than</span> <br /> </td> 
   <td> El resultado es un valor mayor que el valor introducido.<br /> </td> 
   <td> <strong>Edad (@age) mayor que 50</strong> devuelve como resultado todos los valores mayores que 50, es decir 51, 52, etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Less than</span> <br /> </td> 
   <td> El resultado es un valor menor que el valor introducido.<br /> </td> 
   <td> <strong>Fecha de creación (@created) antes de “DaysAgo(100)”</strong> devuelve como resultado todos los destinatarios creados hace menos de 100 días.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Greater than or equal to</span> <br /> </td> 
   <td> El resultado son todos los valores iguales o mayores que el valor introducido.<br /> </td> 
   <td> <strong>Edad (@age) mayor o igual que “30”</strong>, devuelve como resultado todos los destinatarios de 30 años o más.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Less than or equal to</span> <br /> </td> 
   <td> El resultado son todos los valores iguales o inferiores al valor introducido.<br /> </td> 
   <td> <strong>Edad (@age) menor o igual que “60”</strong>, devuelve como resultado todos los destinatarios de 60 años o menos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Not equal to</span> <br /> </td> 
   <td> El resultado son todos los valores que no son idénticos al valor ingresado.<br /> </td> 
   <td> <strong>Idioma (@language) igual a “inglés”</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Starts with</span> <br /> </td> 
   <td> Devuelve los resultados que comienzan con el valor ingresado.<br /> </td> 
   <td> <strong>N.º cuenta (@account) comienza con “32010”.</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Does not start with</span> <br /> </td> 
   <td> Devuelve los resultados que no empiezan con el valor introducido.<br /> </td> 
   <td> <strong>N.º cuenta (@account) no comienza con “20”</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Contains</span> <br /> </td> 
   <td> Devuelve los resultados que contienen al menos el valor ingresado.<br /> </td> 
   <td> <strong>Dominio de correo electrónico (@domain) incluye “mail”</strong> devuelve todos los nombres de dominio que contengan “mail”. Por lo tanto, también devuelve el dominio “gmail.com”.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Does not contain</span> <br /> </td> 
   <td> Devuelve los resultados que no contienen el valor introducido.<br /> </td> 
   <td> <strong>Dominio de correo electrónico (@domain) no incluye “vo”</strong>. En este caso, no devuelve como resultado los nombres de dominio que contengan “vo”. El nombre de dominio “voila.fr” no aparece en los resultados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Like</span> <br /> </td> 
   <td> <span class="uicontrol">Like</span> es muy similar al operador <span class="uicontrol">Contains</span>. Permite insertar <span class="uicontrol">%</span> wild card character in the value.<br /> </td> 
   <td> <strong>Apellido (@lastName) como “Jon%s”</strong>. En este caso, el carácter comodín se utiliza para encontrar el nombre “Jones”, en el caso de que el operador haya olvidado la letra que falta entre la “n” y la “s”.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Not like</span> <br /> </td> 
   <td> Es similar a <span class="uicontrol">Like</span> . Permite no recuperar el valor introducido. En este caso, el valor introducido debe contener <span class="uicontrol">%</span> wild card character.<br /> </td> 
   <td> <strong>Apellido (@lastName) como “Smi%h”</strong>. En este caso, no devuelve los destinatarios cuyo apellido sea “Smi%h”.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Is empty</span> <br /> </td> 
   <td> En este caso, el resultado que estamos buscando coincide con un valor vacío en la segunda columna Valor.<br /> </td> 
   <td> <strong>Móvil (@mobilePhone) está vacío</strong> devuelve todos los destinatarios que no tienen un número de móvil.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Is not empty</span> <br /> </td> 
   <td> Funciona de forma inversa al operador <span class="uicontrol">Is empty</span>. No es necesario introducir datos en la segunda columna Valor.<br /> </td> 
   <td> <strong>Correo electrónico (@email) no está vacío</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Is included in</span> <br /> </td> 
   <td> Devuelve los resultados incluidos entre los valores indicados. Estos valores deben separarse con una coma.<br /> </td> 
   <td> <strong>Fecha de nacimiento (@birthDate) incluida en “12/10/1979,12/10/1984”</strong>, devuelve como resultado los destinatarios que nacieran entre esas fechas. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Is not included in</span> <br /> </td> 
   <td> Funciona como el operador <span class="uicontrol">Is included in</span>. Aquí queremos excluir los destinatarios según los valores ingresados.<br /> </td> 
   <td> <strong>Fecha de nacimiento (@birthDate) no incluida en “12/10/1979,12/10/1984”</strong>. A diferencia del ejemplo anterior, no se recuperan los destinatarios nacidos entre esas fechas.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Utilice AND, OR, EXCEPT {#using-and--or--except}

Para consultas que utilizan varias condiciones de filtro, debe definir los vínculos entre las condiciones. Hay tres vínculos posibles:

* **[!UICONTROL And]** permite combinar dos condiciones de filtrado,
* **[!UICONTROL Or]** permite ofrecer una alternativa,
* **[!UICONTROL Except]** permite definir una excepción.

Haga clic en **[!UICONTROL And]** (de forma predeterminada) y seleccione en la lista desplegable.

![](assets/query_condition_modif_01.png)

* **[!UICONTROL And]**: añade una condición y activa el sobrefiltrado.
* **[!UICONTROL Or]**: añade una condición y activa el sobrefiltrado.

   El siguiente ejemplo permite encontrar destinatarios cuyo dominio de correo electrónico contiene “orange.co.uk” o cuyo código de envío comienza por “NW”.

   ![](assets/query_condition_modif_02.png)

* **[!UICONTROL Except]**: si tiene dos filtros y el primero no devuelve un valor, este tipo de vínculo crea una excepción.

   En el siguiente ejemplo, deseamos devolver los destinatarios cuyo dominio de correo electrónico contiene “orange.co.uk” excepto si el apellido del destinatario es “Smith”.

   ![](assets/query_condition_modif_03.png)

Este ejemplo muestra un filtro que le permite mostrar: los destinatarios que hablen español, O que son mujeres con teléfono móvil, O los destinatarios sin número de cuenta y cuyo nombre de empresa comienza con la letra “n”.

![](assets/query_editor_nveau_31.png)

## Condiciones de prioridad {#prioritizing-conditions}

Esta sección explica cómo priorizar las condiciones gracias a las flechas azules de la barra de herramientas.

* La flecha que señala a la derecha permite añadir un nivel de paréntesis al filtro.
* La flecha que señala a la izquierda permite eliminar un nivel de paréntesis seleccionado del filtro.

   ![](assets/query_condition_modif_04.png)

* Las flechas verticales permiten mover una condición, cambiando así su secuencia de ejecución.

Este ejemplo muestra cómo utilizar la flecha para eliminar un nivel de paréntesis. Comience desde la siguiente condición de filtrado: **[!UICONTROL City equal to London OR gender equal to male and mobile not indicated OR account # starts with "95" and company name starts with "A"]**.

Sitúe el cursor en la condición de filtrado **[!UICONTROL Gender (@gender) equal to Male]** y haga clic en la flecha **[!UICONTROL Remove a parenthesis level]**.

![](assets/query_editor_nveau_32.png)

Ahora la condición **[!UICONTROL Gender (@gender) equal to Male]** está fuera de su paréntesis. Se ha movido al mismo nivel que la condición “Ciudad igual a Londres”. Estas condiciones se vinculan entre sí (**[!UICONTROL And]**).

## Seleccionar datos para extraer {#selecting-data-to-extract}

Los campos disponibles varían de una tabla a otra. Todos los campos se almacenan en un nodo principal denominado **[!UICONTROL Main element]**. En el siguiente ejemplo, los campos disponibles se encuentran en la tabla de destinatarios. Los campos siempre se muestran por orden alfabético.

El campo seleccionado se puede ver en la parte inferior de la ventana. Por ejemplo, el campo **[!UICONTROL Email domain]** es un **[!UICONTROL Calculated SQL field]** y su extensión es **[!UICONTROL (@domain)]**.

![](assets/query_editor_nveau_59.png)

>[!NOTE]
>
>Utilice la herramienta **[!UICONTROL Search]** para buscar un campo disponible.

Haga doble clic en un campo disponible para añadirlo a las columnas de salida. Al final de la consulta, cada campo seleccionado crea una columna en la ventana **[!UICONTROL Data preview]**.

![](assets/query_editor_nveau_01.png)

Los campos avanzados no se muestran de forma predeterminada. Haga clic en **[!UICONTROL Display advanced fields]** en la esquina inferior derecha de los campos disponibles para mostrar todo. Haga clic de nuevo para volver a la vista anterior.

Por ejemplo, en la tabla de destinatarios, los campos avanzados son **Boolean 1**, **[!UICONTROL Boolean 2]**, **[!UICONTROL Boolean 3]**, **[!UICONTROL Foreign key of "Folder" link]**, etc.

El ejemplo siguiente muestra los campos avanzados de la tabla de destinatarios.

![](assets/query_editor_nveau_53.png)

Las distintas categorías de campos:

<table> 
 <thead> 
  <tr> 
   <th> Icono<br /> </th> 
   <th> Descripción<br /> </th> 
   <th> Ejemplos<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_47.png" /> </td> 
   <td> Campo sencillo<br /> </td> 
   <td> Correo electrónico, sexo, etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_48.png" /> </td> 
   <td> Clave principal. Este campo SQL es una forma de identificar un registro de una tabla.<br /> </td> 
   <td> Los destinatarios de identificador son claves principales y los identificadores son exclusivos de definición.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_02.png" /> </td> 
   <td> Clave externa. Se utiliza como enlace a otra tabla.<br /> </td> 
   <td> Clave externa del destinatario, clave externa del servicio, etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_46.png" /> </td> 
   <td> Campo calculado. Este tipo de campo se calcula al solicitarlo utilizando los valores de la base de datos.<br /> </td> 
   <td> Edad, dominio de email, etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_49.png" /> </td> 
   <td> Campo que contiene textos largos.<br /> </td> 
   <td> Comentario, dirección completa, etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_50.png" /> </td> 
   <td> Campo SQL indexado. <br /> </td> 
   <td> Nombre completo, código ISO, etc. <br /> </td> 
  </tr> 
 </tbody> 
</table>

Enlace a una tabla y elemento de colección:

<table> 
 <thead> 
  <tr> 
   <th> Icono<br /> </th> 
   <th> Descripción<br /> </th> 
   <th> Ejemplo<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_51.png" /> </td> 
   <td> Enlaza a una tabla en particular. Estas coinciden con las asociaciones de tipo 1-1. Una aparición de la tabla de origen puede coincidir con una única aparición de la tabla de destino. Por ejemplo, solo se puede vincular un destinatario a un país.<br /> </td> 
   <td> Carpeta, estado, país, etc. <br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_52.png" /> </td> 
   <td> Elemento de colección en una tabla específica. Estos coinciden con asociaciones de tipo 1-N. Una tabla de origen puede coincidir con varias apariciones de la tabla de destino, pero una aparición de la tabla de destino solo puede coincidir con una aparición de la tabla de origen. Por ejemplo, un destinatario puede suscribirse a “n” letras de suscripción.<br /> </td> 
   <td> Suscripciones, listas, registros de exclusión, etc.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* Utilice el botón **[!UICONTROL Add]** (encima de la barra de iconos laterales) para añadir una columna de salida en la que deseamos editar la expresión. Para obtener más información sobre la edición de una expresión, consulte [esta sección](#building-expressions).
>* Elimine una columna de salida haciendo clic en la “x” roja (**Eliminar**).
>* Cambie el orden de las columnas de salida mediante las flechas.
>* La **[!UICONTROL Distribution of values]** sirve para ver la distribución de los valores del campo seleccionado (por ejemplo, las distribuciones vinculadas a las ciudades de los destinatarios, los lenguajes de los destinatarios, etc.).


## Crear campos calculados {#creating-calculated-fields}

Si es necesario, agregue una columna durante el formato de datos. Un campo calculado añade una columna a la sección de previsualización de datos. Haga clic **[!UICONTROL Add a calculated field]**.

![](assets/query_editor_nveau_43.png)

Existen cuatro tipos de campos calculados:

* **[!UICONTROL Fixed string]**: permite añadir una cadena de caracteres.

   ![](assets/query_editor_nveau_60.png)

* **[!UICONTROL String with JavaScript tags]**: el valor del campo calculado combina una cadena de caracteres y directivas de JavaScript.

   ![](assets/query_editor_nveau_61.png)

* **[!UICONTROL JavaScript expression]**: el valor del campo calculado es el resultado de una evaluación de función de JavaScript. Se puede escribir el valor devuelto (número, fecha, etc.).

   ![](assets/query_editor_nveau_62.png)

* **[!UICONTROL Enumerations]**: este tipo de campo permite utilizar o modificar el contenido de una de las columnas de salida en una nueva columna.

   Es posible utilizar el valor de origen de una columna y asignarle un valor de destino. Este valor de destino se muestra en la nueva columna de salida.

   Puede encontrar un ejemplo de adición del tipo de campo calculado **[!UICONTROL Enumerations]** si consulta [esta sección](../../workflow/using/adding-enumeration-type-calculated-field.md).

   ![](assets/query_editor_nveau_63.png)

   El campo calculado de tipo **[!UICONTROL Enumerations]** puede incluir 4 condiciones:

   * **[!UICONTROL Keep the source value]** restaura el valor de origen en el destino sin cambiarlo.
   * **[!UICONTROL Use the following value]** permite introducir un valor de destino predeterminado para valores de origen no definidos.
   * **[!UICONTROL Generate a warning and continue]** advierte al usuario de que el valor de origen no puede modificarse.
   * **[!UICONTROL Generate an error and reject the line]** evita el cálculo e importación de la línea.

Haga clic en **[!UICONTROL Detail of calculated field]** para ver los detalles del campo insertado.

Para eliminar este campo calculado, haga clic en **[!UICONTROL Remove the calculated field]**.

![](assets/query_editor_nveau_58.png)

## Generar expresiones {#building-expressions}

La herramienta de edición de expresiones permite calcular acumulaciones, generar funciones o editar una fórmula con una expresión.

El ejemplo siguiente muestra cómo ejecutar un recuento en una clave principal.

Siga estos pasos:

1. Haga clic **[!UICONTROL Add]** en la **[!UICONTROL Data to extract]** ventana. En la ventana **[!UICONTROL Formula type]**, seleccione un tipo de fórmula para introducir la expresión.

   Hay varios tipos de fórmulas disponibles: **[!UICONTROL Field only]**, **[!UICONTROL Aggregate]**, **[!UICONTROL Expression]**.

   Seleccione **[!UICONTROL Process on an aggregate function]**, y **[!UICONTROL Count]**. Haga clic en **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_54.png)

1. La clave principal se calcula.

   ![](assets/query_editor_nveau_88.png)

A continuación, se muestra una vista detallada de las opciones disponibles en la ventana **[!UICONTROL Formula types]**:

![](assets/query_editor_nveau_05.png)

1. **[!UICONTROL Field only]** permite volver a la ventana **[!UICONTROL Field to select]**.
1. **[!UICONTROL Aggregate (Process on an aggregate function)]**. A continuación se muestran algunos ejemplos de uso de acumulaciones:

   * **[!UICONTROL Count]** permite ejecutar un recuento de claves principales.
   * **[!UICONTROL Sum]** permite añadir todas las compras realizadas por un cliente durante un año.
   * **[!UICONTROL Maximum value]** permite encontrar los clientes que han adquirido los productos más “n”.
   * **[!UICONTROL Minimum value]** permite revisar los clientes y encontrar los que se han suscrito a una oferta más recientemente.
   * **[!UICONTROL Average]**. Esta función permite calcular la edad promedio de los destinatarios.

      La casilla **[!UICONTROL Distinct]** permite recuperar valores únicos y distintos de cero de una columna. Por ejemplo, puede recuperar todos los registros de seguimiento de un destinatario y estos registros de seguimiento se cambian al valor 1, ya que todos afectan al mismo destinatario.

1. **[!UICONTROL Expression]** abre la ventana **[!UICONTROL Edit the expression]**. Esto permite detectar números de teléfono con demasiadas cifras, probablemente como errores de entrada.

   ![](assets/query_editor_nveau_71.png)

   Para obtener una lista de todas las funciones disponibles, consulte [Lista de funciones](#list-of-functions).

## Lista de funciones {#list-of-functions}

Si se elige una fórmula de tipo **[!UICONTROL Expression]**, se accede a la ventana &quot;editar la expresión&quot;. Se pueden asociar varias categorías de funciones a los campos disponibles: **[!UICONTROL Aggregates]**,**[!UICONTROL String]**, **[!UICONTROL Date]**, **[!UICONTROL Numerical]**, **[!UICONTROL Currency]**, **[!UICONTROL Geomarketing]**, **[!UICONTROL Windowing function]** y **[!UICONTROL Others]**.

El editor de expresiones tiene este aspecto:

![](assets/s_ncs_user_filter_define_expression.png)

Permite seleccionar campos en las tablas de la base de datos y añadir funciones avanzadas. Estas son las funciones disponibles:

**Acumulados**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nombre</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Avg</strong><br /> </td> 
   <td> Devuelve el promedio de una columna de tipo numérico<br /> </td> 
   <td> Avg(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Recuento</strong><br /> </td> 
   <td> Cuenta los valores no nulos de una columna<br /> </td> 
   <td> Count(&lt;value&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>CountAll</strong><br /> </td> 
   <td> Cuenta los valores devueltos (todos los campos)<br /> </td> 
   <td> CountAll()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Countdistinct</strong><br /> </td> 
   <td> Cuenta los distintos valores no nulos de una columna<br /> </td> 
   <td> Countdistinct(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Max</strong><br /> </td> 
   <td> Devuelve el valor máximo de una columna numérica, cadena o tipo de fecha<br /> </td> 
   <td> Max(&lt;value&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Min</strong><br /> </td> 
   <td> Devuelve el valor mínimo de un número, una cadena o una columna de tipo de fecha<br /> </td> 
   <td> Min(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>StdDev</strong><br /> </td> 
   <td> Devuelve la desviación estándar de una columna de número, cadena o fecha.<br /> </td> 
   <td> StdDev(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Sum</strong><br /> </td> 
   <td> Devuelve la suma de los valores de una columna de número, cadena o fecha.<br /> </td> 
   <td> Sum(&lt;value&gt;)<br /></td> 
  </tr> 
 </tbody> 
</table>

**Cadena**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nombre</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
   <td> <strong>Sintaxis</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull2</strong><br /> </td> 
   <td> Indica si todos los parámetros no son nulos y no están vacíos.<br /> </td> 
   <td> AllNonNull2(&lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull3</strong><br /> </td> 
   <td> Indica si todos los parámetros no son nulos y no están vacíos.<br /> </td> 
   <td> AllNonNull3(&lt;string&gt;, &lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ascii</strong><br /> </td> 
   <td> Devuelve el valor ASCII del primer carácter de la cadena.<br /> </td> 
   <td> Ascii(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Char</strong><br /> </td> 
   <td> Devuelve el carácter correspondiente al código ASCII “n”.<br /> </td> 
   <td> Char(&lt;number&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Charindex</strong><br /> </td> 
   <td> Devuelve la posición de la cadena 2 en la cadena 1.<br /> </td> 
   <td> Charindex(&lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>GetLine</strong><br /> </td> 
   <td> Muestra la línea nth (de 1 a n) de la cadena.<br /> </td> 
   <td> GetLine(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IfEquals</strong><br /> </td> 
   <td> Devuelve el tercer parámetro si los dos primeros parámetros son iguales. Si no es así, devuelve el último parámetro<br /> </td> 
   <td> IfEquals(&lt;string&gt;, &lt;string&gt;, &lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IsMemoNull</strong><br /> </td> 
   <td> Indica si la nota transferida como parámetro es nula<br /> </td> 
   <td> IsMemoNull(&lt;memo&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords</strong><br /> </td> 
   <td> Concatena las cadenas transferidas como parámetros. Añade espacios entre las cadenas si es necesario.<br /> </td> 
   <td> JuxtWords(&lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords3</strong><br /> </td> 
   <td> Concatena las cadenas transferidas como parámetros. Añade espacios entre las cadenas si es necesario<br /> </td> 
   <td> JuxtWords3(&lt;string&gt;, &lt;string&gt;, &lt;string&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>LPad</strong><br /> </td> 
   <td> Devuelve la cadena completa a la izquierda<br /> </td> 
   <td> LPad(&lt;string&gt;, &lt;number&gt;, &lt;character&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Left</strong><br /> </td> 
   <td> Devuelve los primeros “n” caracteres de la cadena<br /> </td> 
   <td> Left(&lt;string&gt;, &lt;number&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Length</strong><br /> </td> 
   <td> Devuelve la longitud de la cadena<br /> </td> 
   <td> Length(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Lower</strong><br /> </td> 
   <td> Devuelve la cadena en minúscula<br /> </td> 
   <td> Lower(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ltrim</strong><br /> </td> 
   <td> Elimina los espacios a la izquierda de la cadena<br /> </td> 
   <td> Ltrim(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Md5Digest</strong><br /> </td> 
   <td> Devuelve una representación hexadecimal de la clave MD5 de una cadena<br /> </td> 
   <td> Md5Digest(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>MemoContains</strong><br /> </td> 
   <td> Especifica si la nota contiene la cadena transferida como parámetro<br /> </td> 
   <td> MemoContains(&lt;memo&gt;, &lt;cadena&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>RPad</strong><br /> </td> 
   <td> Devuelve la cadena completa a la derecha<br /> </td> 
   <td> RPad(&lt;string&gt;, &lt;number&gt;, &lt;character&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Right</strong><br /> </td> 
   <td> Devuelve los últimos “n” caracteres de la cadena<br /> </td> 
   <td> Right(&lt;cadena&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Rtrim</strong><br /> </td> 
   <td> Elimina los espacios a la derecha de la cadena<br /> </td> 
   <td> Rtrim(&lt;string&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Smart</strong><br /> </td> 
   <td> Devuelve la cadena con la primera letra de cada palabra en mayúscula<br /> </td> 
   <td> Smart(&lt;cadena&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Substring</strong><br /> </td> 
   <td> Extrae la subcadena que comienza en el carácter “n1” de la cadena y de longitud “n2”<br /> </td> 
   <td> Substring(&lt;string&gt;, &lt;offset&gt;, &lt;length&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToString</strong><br /> </td> 
   <td> Convierte el número en una cadena<br /> </td> 
   <td> ToString(&lt;number&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Upper</strong><br /> </td> 
   <td> Devuelve la cadena en mayúsculas<br /> </td> 
   <td> Upper(&lt;cadena&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLink</strong><br /> </td> 
   <td> Devuelve la clave externa de un vínculo transferido como parámetro si los otros dos parámetros son iguales<br /> </td> 
   <td> VirtualLink(&lt;número&gt;, &lt;número&gt;, &lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLinkStr</strong><br /> </td> 
   <td> Devuelve la clave externa (texto) de un enlace transferido como parámetro si los otros dos parámetros son iguales<br /> </td> 
   <td> VirtualLinkStr(&lt;string&gt;, &lt;number&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>dataLength</strong><br /> </td> 
   <td> Devuelve el tamaño de la cadena<br /> </td> 
   <td> dataLength(&lt;string&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Fecha**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nombre</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
   <td> <strong>Sintaxis</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AddDays</strong><br /> </td> 
   <td> Agrega un número de días a una fecha<br /> </td> 
   <td> AddDays(&lt;fecha&gt;, &lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddHours</strong><br /> </td> 
   <td> Agrega un número de horas a una fecha<br /> </td> 
   <td> AddHours(&lt;fecha&gt;, &lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMinutes</strong><br /> </td> 
   <td> Añade un número de minutos a una fecha<br /> </td> 
   <td> AddMinutes(&lt;fecha&gt;, &lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMonths</strong><br /> </td> 
   <td> Añade un número de meses a una fecha<br /> </td> 
   <td> AddMonths(&lt;fecha&gt;, &lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddSeconds</strong><br /> </td> 
   <td> Añade un número de segundos a una fecha<br /> </td> 
   <td> AddSeconds(&lt;fecha&gt;, &lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddYears</strong><br /> </td> 
   <td> Agrega un número de años a una fecha<br /> </td> 
   <td> AddYears(&lt;fecha&gt;, &lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DateOnly</strong><br /> </td> 
   <td> Devuelve solo la fecha (con hora 00:00)*<br /> </td> 
   <td> DateOnly(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Day</strong><br /> </td> 
   <td> Devuelve el número que representa el día de la fecha.<br /> </td> 
   <td> Day(&lt;fecha&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DayOfYear</strong><br /> </td> 
   <td> Devuelve el número de día del año de la fecha<br /> </td> 
   <td> DayOfYear(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgo</strong><br /> </td> 
   <td> Devuelve la fecha correspondiente a la fecha actual menos “n” días<br /> </td> 
   <td> DaysAgo(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgoInt</strong><br /> </td> 
   <td> Devuelve la fecha (entero aaaammdd) correspondiente a la fecha actual menos “n” días<br /> </td> 
   <td> DaysAgoInt(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysDiff</strong><br /> </td> 
   <td> Número de días entre dos fechas<br /> </td> 
   <td> DaysDiff(&lt;fecha de finalización&gt;, &lt;fecha de inicio&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysOld</strong><br /> </td> 
   <td> Devuelve la edad en días de una fecha<br /> </td> 
   <td> DaysOld(&lt;fecha&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetDate</strong><br /> </td> 
   <td> Devuelve la fecha del sistema actual del servidor<br /> </td> 
   <td> GetDate()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Hour</strong><br /> </td> 
   <td> Devuelve la hora de la fecha<br /> </td> 
   <td> Hour(&lt;fecha&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>HoursDiff</strong><br /> </td> 
   <td> Devuelve el número de horas entre dos fechas<br /> </td> 
   <td> HoursDiff(&lt;end date&gt;, &lt;start date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Minute</strong><br /> </td> 
   <td> Devuelve los minutos de la fecha<br /> </td> 
   <td> Minute(&lt;fecha&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MinutesDiff</strong><br /> </td> 
   <td> Devuelve el número de minutos entre dos fechas<br /> </td> 
   <td> MinutesDiff(&lt;fecha de finalización&gt;, &lt;fecha de inicio&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Month</strong><br /> </td> 
   <td> Devuelve el número que representa el mes de la fecha<br /> </td> 
   <td> Month(&lt;fecha&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsAgo</strong><br /> </td> 
   <td> Devuelve la fecha correspondiente a la fecha actual menos n meses<br /> </td> 
   <td> MonthsAgo(&lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsDiff</strong><br /> </td> 
   <td> Devuelve el número de meses entre dos fechas<br /> </td> 
   <td> MonthsDiff(&lt;fecha de finalización&gt;, &lt;fecha de inicio&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsOld</strong><br /> </td> 
   <td> Devuelve la edad en meses de una fecha<br /> </td> 
   <td> MonthsOld(&lt;fecha&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Second</strong><br /> </td> 
   <td> Devuelve los segundos de la fecha<br /> </td> 
   <td> Second(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SecondsDiff</strong><br /> </td> 
   <td> Devuelve el número de segundos entre dos fechas<br /> </td> 
   <td> SecondsDiff(&lt;fecha de finalización&gt;, &lt;fecha de inicio&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubDays</strong><br /> </td> 
   <td> Resta un número de días a partir de una fecha<br /> </td> 
   <td> SubDays(&lt;fecha&gt;, &lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubHours</strong><br /> </td> 
   <td> Resta un número de horas a partir de una fecha<br /> </td> 
   <td> SubHours(&lt;fecha&gt;, &lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMinutes</strong><br /> </td> 
   <td> Resta un número de minutos desde una fecha<br /> </td> 
   <td> SubMinutes(&lt;fecha&gt;, &lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMonths</strong><br /> </td> 
   <td> Resta un número de meses desde una fecha<br /> </td> 
   <td> SubMonths(&lt;fecha&gt;, &lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubSeconds</strong><br /> </td> 
   <td> Resta un número de segundos desde una fecha<br /> </td> 
   <td> SubSeconds(&lt;fecha&gt;, &lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubYears</strong><br /> </td> 
   <td> Resta un número de años a partir de una fecha<br /> </td> 
   <td> SubYears(&lt;fecha&gt;, &lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDate</strong><br /> </td> 
   <td> Convierte una fecha y hora como fecha<br /> </td> 
   <td> ToDate(&lt;fecha + hora&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDateTime</strong><br /> </td> 
   <td> Convierte una cadena en una fecha + hora.<br /> </td> 
   <td> ToDateTime(&lt;string&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncDate</strong><br /> </td> 
   <td> Redondea una fecha y hora hacia el segundo más cercano<br /> </td> 
   <td> TruncDate(@lastModified, &lt;número de segundos&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncDateTZ</strong><br /> </td> 
   <td> Redondea una fecha y hora con una precisión determinada expresada en segundos<br /> </td> 
   <td> TruncDateTZ(&lt;fecha&gt;, &lt;número de segundos&gt;, &lt;zona horaria&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncQuarter</strong><br /> </td> 
   <td> Redondea una fecha al trimestre<br /> </td> 
   <td> TruncQuarter(&lt;fecha&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncTime</strong><br /> </td> 
   <td> Redondea la parte de tiempo hasta el segundo más cercano<br /> </td> 
   <td> TruncTim(e&lt;date&gt;, &lt;number of seconds&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> Redondea una fecha a la semana<br /> </td> 
   <td> TruncWeek(&lt;fecha&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncYear</strong><br /> </td> 
   <td> Redondea una fecha y hora al 1 de enero del año<br /> </td> 
   <td> TruncYear(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> Devuelve el número que representa el día de la semana de la fecha<br /> </td> 
   <td> WeekDay(&lt;fecha&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Year</strong><br /> </td> 
   <td> Devuelve el número que representa el año de la fecha<br /> </td> 
   <td> Year(&lt;fecha&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearAndMonth</strong><br /> </td> 
   <td> Devuelve el número que representa el año y el mes de la fecha<br /> </td> 
   <td> YearAndMonth(&lt;fecha&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsDiff</strong><br /> </td> 
   <td> Devuelve el número de años entre las dos fechas<br /> </td> 
   <td> YearsDiff(&lt;fecha de finalización&gt;, &lt;fecha de inicio&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsOld</strong><br /> </td> 
   <td> Devuelve la edad en años de una fecha<br /> </td> 
   <td> YearsOld(&lt;date&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Tenga en cuenta que la función **Dateonly** tiene en cuenta la zona horaria del servidor, no la del operador.

**Numérico**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nombre</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
   <td> <strong>Sintaxis</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Abs</strong><br /> </td> 
   <td> Devuelve el valor absoluto de un número<br /> </td> 
   <td> Abs(&lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Ceil</strong><br /> </td> 
   <td> Devuelve el menor entero que sea mayor o igual que un número<br /> </td> 
   <td> Ceil(&lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Floor</strong><br /> </td> 
   <td> Devuelve el mayor entero que sea mayor o igual que un número<br /> </td> 
   <td> Floor(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Greatest</strong><br /> </td> 
   <td> Devuelve el número mayor de dos números<br /> </td> 
   <td> Greatest(&lt;número 1&gt;, &lt;número 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Least</strong><br /> </td> 
   <td> Devuelve el número menor de dos números<br /> </td> 
   <td> Least(&lt;número 1&gt;, &lt;número 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Mod</strong><br /> </td> 
   <td> Devuelve el resto de la división del entero “n1” entre “n2”<br /> </td> 
   <td> Mod(&lt;number 1&gt;, &lt;number 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Percent</strong><br /> </td> 
   <td> Devuelve la proporción de dos números expresado como un porcentaje<br /> </td> 
   <td> Percent(&lt;número 1&gt;, &lt;número 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Aleatorio</strong><br /> </td> 
   <td> Devuelve un valor aleatorio<br /> </td> 
   <td> Aleatorio()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Round</strong><br /> </td> 
   <td> Redondea un número a “n” decimales<br /> </td> 
   <td> Redondeo(&lt;número&gt;, &lt;número de decimales&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Sign</strong><br /> </td> 
   <td> Devuelve el signo del número<br /> </td> 
   <td> Sign(&lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDouble</strong><br /> </td> 
   <td> Convierte un entero en flotante<br /> </td> 
   <td> ToDouble(&lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInt64</strong><br /> </td> 
   <td> Convierte un flotante en un entero de 64 bits<br /> </td> 
   <td> ToInt64(&lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInteger</strong><br /> </td> 
   <td> Convierte un flotante en un entero<br /> </td> 
   <td> ToInteger(&lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Trunc</strong><br /> </td> 
   <td> Trunca decimales de “n1” a “n2”<br /> </td> 
   <td> Trunc(&lt;n1&gt;, &lt;n2&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

1. Moneda

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nombre</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
   <td> <strong>Sintaxis</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ConvertCurrency</strong><br /> </td> 
   <td> Convierte una cantidad de una moneda de origen en una cantidad de una moneda de destino<br /> </td> 
   <td> ConvertCurrency(&lt;amount&gt;, &lt;source currency&gt;, &lt;target currency&gt;, &lt;conversion date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>FormatCurrency</strong><br /> </td> 
   <td> Da formato a la cantidad mostrada según la configuración de moneda seleccionada<br /> </td> 
   <td> FormatCurrency(&lt;amount&gt;, &lt;currency&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Geomarketing**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nombre</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
   <td> <strong>Sintaxis</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Distance</strong><br /> </td> 
   <td> Devuelve la distancia entre dos puntos definidos por su longitud y latitud, expresada en grados<br /> </td> 
   <td> Distance(&lt;Longitude A&gt;, &lt;Latitude A&gt;, &lt;Longitude B&gt;, &lt;Latitude B&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Otros**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nombre</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
   <td> <strong>Sintaxis</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Case</strong><br /> </td> 
   <td> Devuelve el valor 1 si la condición es verdadera. Si no es así, devuelve el valor 2.<br /> </td> 
   <td> Case(When(&lt;condition&gt;, &lt;value 1&gt;), Else(&lt;value 2&gt;))<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ClearBit</strong><br /> </td> 
   <td> Elimina el indicador del valor<br /> </td> 
   <td> ClearBit(&lt;identificador&gt;, &lt;indicador&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Coalesce</strong><br /> </td> 
   <td> Devuelve el valor 2 si el valor 1 es cero o nulo, de lo contrario devuelve el valor 1<br /> </td> 
   <td> Coalesce(&lt;valor 1&gt;, &lt;valor 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Decode</strong><br /> </td> 
   <td> Devuelve el valor 3 si el valor 1 = valor 2. Si no devuelve el valor 4.<br /> </td> 
   <td> Decode(&lt;value 1&gt;, &lt;value 2&gt;, &lt;value 3&gt;, &lt;value 4&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Else</strong><br /> </td> 
   <td> Devuelve el valor 1 (solo puede utilizarse como parámetro de la función case)<br /> </td> 
   <td> Else(&lt;value 1&gt;, &lt;value 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetEmailDomain</strong><br /> </td> 
   <td> Extrae el dominio de una dirección de correo electrónico<br /> </td> 
   <td> GetEmailDomain(&lt;value&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetMirrorURL</strong><br /> </td> 
   <td> Recupera la URL del servidor de la página espejo<br /> </td> 
   <td> GetMirrorURL(&lt;valor&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Iif</strong><br /> </td> 
   <td> Devuelve el valor 1 si la expresión es verdadera. Si no es así, devuelve el valor 2<br /> </td> 
   <td> Iif(&lt;condition&gt;, &lt;value 1&gt;, &lt;value 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsBitSet</strong><br /> </td> 
   <td> Indica si el indicador se encuentra en el valor<br /> </td> 
   <td> IsBitSet(&lt;identificador&gt;, &lt;indicador&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsEmptyString</strong><br /> </td> 
   <td> Devuelve el valor 2 si la cadena 1 está vacía; en caso contrario, devuelve el valor 3<br /> </td> 
   <td> IsEmptyString(&lt;value 1&gt;, &lt;value 2&gt;, &lt;value 3&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>NoNull</strong><br /> </td> 
   <td> Devuelve la cadena vacía si el argumento es NULL<br /> </td> 
   <td> NoNull(&lt;valor&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>RowId</strong><br /> </td> 
   <td> Devuelve el número de línea<br /> </td> 
   <td> RowId<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>SetBit</strong><br /> </td> 
   <td> Fuerza la marca en el valor<br /> </td> 
   <td> SetBit(&lt;identificador&gt;, &lt;indicador&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToBoolean</strong><br /> </td> 
   <td> Convierte un número en Boolean<br /> </td> 
   <td> ToBoolean(&lt;número&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>When</strong><br /> </td> 
   <td> Devuelve el valor 1 si la expresión es verdadera. Si no es así, devuelve el valor 2 (solo puede utilizarse como parámetro de la función case)<br /> </td> 
   <td> When(&lt;condition&gt;, &lt;value 1&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Funciones de ventana**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nombre</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
   <td> <strong>Sintaxis</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Desc</strong><br /> </td> 
   <td> Aplica un orden descendente<br /> </td> 
   <td> Desc(&lt;valor 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>OrderBy</strong><br /> </td> 
   <td> Ordena el resultado dentro de la partición<br /> </td> 
   <td> OrderBy(&lt;valor 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>PartitionBy</strong><br /> </td> 
   <td> Particiona el resultado de una consulta en una tabla<br /> </td> 
   <td> PartitionBy(&lt;valor 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>RowNum</strong><br /> </td> 
   <td> Genera un número de línea basado en la partición de tabla y en una secuencia de ordenación.<br /> </td> 
   <td> RowNum(PartitionBy(&lt;value 1&gt;), OrderBy(&lt;value 1&gt;))<br /> </td> 
  </tr> 
 </tbody> 
</table>