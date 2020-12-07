---
solution: Campaign Classic
product: campaign
title: Glosario
description: Glosario
audience: interaction
content-type: reference
topic-tags: interaction-overview
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '1094'
ht-degree: 100%

---


# Glosario{#glossary}

A continuación, se presenta la definición de los principales elementos de interacción.

* **Environment**: define lo que incluye un catálogo de ofertas y los enlaces (espacios de oferta). Es necesario crear un entorno mediante la dimensión de segmentación. Hay dos tipos de entornos:

   * **Design environment**: entorno en el que se crean y/o se definen las reglas tipológicas (reglas que determinan las ofertas para presentarlas, o no, a una persona destinataria). También se definen en este entorno la lista de personas que reciben las ofertas y la lista de almacenamiento de todas ellas. El nodo **[!UICONTROL Design environment]** contiene subcarpetas del espacio de ofertas, filtros predefinidos y categorías de las ofertas. A cada **[!UICONTROL Design environment]**, le corresponde un **[!UICONTROL Live environment]** de solo lectura, generado a partir de este mismo **[!UICONTROL Design environment]**.
   * **Live environment**: entorno vinculado a **[!UICONTROL Design environment]**. Contiene ofertas de solo lectura cuyo contenido e idoneidad se han aprobado a través de la **[!UICONTROL Design environment]**. Se deben seleccionar para introducirlos en un sitio web o insertarlos en un mensaje.

* **Offer space**: carpeta que determina la ubicación donde se expone la oferta. La definición de un espacio permite especificar el canal utilizado, especificar si se puede utilizar en el modo unitario (de forma predeterminada: solo en modo por lotes), crear el contenido de la oferta utilizando las funciones de renderización y especificar la oferta de las ofertas presentadas. Un espacio es una interfaz entre el canal y el motor de oferta.

   >[!IMPORTANT]
   >
   >Un espacio de oferta no es un canal de comunicación, coincide con una ubicación de presentación específica del canal. Por ejemplo, las ofertas expuestas en un sitio web pueden ocupar dos espacios en la misma página. En este caso, tendrá dos espacios para el mismo canal.
   >
   >Los espacios deben definirse en las especificaciones y no deben modificarse durante el proyecto.

* **Offer catalog**: conjunto de ofertas definidas en Adobe Campaign que se puede seleccionar durante una interacción. El catálogo se organiza de forma jerárquica con cada nodo correspondiente a una categoría.
* **Category**: una carpeta relacionada con el catálogo de ofertas en un entorno, que organiza las ofertas según la naturaleza, la fecha de idoneidad y el tema de la aplicación. Una categoría puede contener subcategorías que heredan todas las características de la categoría principal. Las reglas de idoneidad se pueden definir para una categoría a fin de compartirlas en varias ofertas.
* **Application themes**: las palabras clave definidas en la categoría permiten filtrar ofertas cuando se presentan en un canal entrante o saliente y restringen la selección de ofertas a una o dos categorías.

   >[!NOTE]
   >
   >Las categorías secundarias heredan los temas identificados en la categoría principal.

* **Eligibility rules**: restricciones aplicadas a un entorno, categoría u oferta sobre el periodo de validez, el objetivo y el peso. Permiten garantizar que una oferta está en línea con el contacto de destino.

   En los entornos, las reglas de idoneidad incluyen reglas de presentación aplicadas a las ofertas y a las personas objetivo.

   En las categorías, las reglas de idoneidad permiten limitar la validez de la categoría en el tiempo, definir los temas de la aplicación y determinar las personas objetivo. También pueden recibir un peso multiplicador durante un periodo determinado. Esto le permite compartir las reglas para las ofertas en otras categorías y simplificar así la administración.

   En las ofertas, las reglas de idoneidad permiten limitar la validez de las ofertas en el tiempo y determinar las personas objetivo.

* **Arbitrage**: seleccionar ofertas que se mostrarán en un entorno (ofertas aptas). El principio de arbitraje clasifica las ofertas por prioridad según los criterios definidos en las categorías, ofertas y ofertas de contexto.
* **Contact**: un contacto de una interacción entrante. Durante el procesamiento de visualización del motor, el contacto se asocia a una dimensión objetivo. Hay dos tipos de contactos:

   * **[!UICONTROL Identified contact]** : un contacto que se ha identificado voluntariamente en el canal. En las interacciones de salida, el contacto se identifica automáticamente.
   * **[!UICONTROL Anonymous contact]** : contacto que no se ha suscrito oficialmente a través del canal, pero que puede identificarse implícitamente mediante una cookie. Esta terminología solo se utiliza para interacciones entrantes.

      >[!NOTE]
      >
      >Los contactos no identificados y anónimos se atribuyen a la dimensión objetivo del visitante.

* **Outbound interaction**: visualizar el motor de interacción desde una lista de contactos (utilizada para enviar correos electrónicos, correo postal, etc.). Se aplican las mismas reglas y procesos a cada contacto. Este tipo de interacción se procesa generalmente en modo por lotes.
* **Inbound interaction**: interacción después de una llamada entrante generada por la acción de un contacto en el canal. Este tipo de interacción se procesa generalmente en modo unitario.
* **Batch mode**: el modo por lotes permite seleccionar la mejor oferta para un conjunto de contactos. Las reglas de idoneidad/priorización se aplican a todos los contactos del conjunto. Este modo se utiliza generalmente para interacciones salientes.
* **Unitary mode**: se procesa un solo contacto cada vez. Este modo se utiliza generalmente para interacciones entrantes y mensajes transaccionales.
* **Identification mode**: hace referencia al estado de un contacto.

   * **[!UICONTROL explicit]** : el contacto se identifica siguiendo su inicio de sesión en la interfaz del canal.
   * **[!UICONTROL implicit]** : el contacto se ha identificado mediante una cookie (permanente o por sesión). Puede procesarse como contacto anónimo o identificado.
   * **[!UICONTROL anonymous]** : el contacto no se puede identificar.

* **Eligible offer**: ofrece a las reuniones las restricciones definidas por adelantado que pueden ofrecerse de forma coherente a un objetivo.
* **Presentation rules**: reglas de tipología a las que se hace referencia en el entorno de la oferta, que le permiten excluir algunas ofertas tomando en cuenta el historial de propuestas.
* **Weight**: las fórmulas que permiten calcular con precisión la importancia de una oferta, para poder seleccionar la oferta más relevante. Los pesos se definen en las ofertas. Las ofertas elegibles se tienen en cuenta en orden de peso reducido.
* **Rendering function**: función definida en el espacio de oferta para crear su representación de oferta basada en los atributos definidos en la oferta. Existen tres modos de función de renderización diferentes: HTML, XML y texto.
* **Offer proposition**: resultado de la acción que consiste en presentar una o varias ofertas a un contacto en un espacio determinado (titular de un sitio web, correo electrónico o SMS, por ejemplo). Este resultado se almacena en la tabla de ofertas propuestas. No obstante, no es obligatorio guardar las propuestas.
* **Simulation**: módulo que permite probar la presentación de las ofertas en los destinatarios objetivo antes de enviar las ofertas.
* **Preview**: previsualización de la oferta tal y como se muestra en su carpeta. Es accesible desde la ventana de configuración de la oferta o el perfil de contacto.
* **Predefined filters**: las reglas de filtrado predefinidas pueden tener en cuenta los parámetros de oferta (por ejemplo, un código de oferta). Se pueden reutilizar una vez creadas las ofertas.
* **Offer representation**: información utilizada por el canal para mostrar la oferta. La representación de la oferta puede crearse a partir de la función de procesamiento del espacio en el que la oferta se representa o se introduce directamente en la interfaz (por ejemplo, en el bloque HTML). Una oferta puede representarse por el espacio.
* **Changeover process**: un proceso activado en un entorno identificado, responsable de dirigir la llamada a un entorno anónimo si el contacto no se ha identificado explícitamente o está identificado de forma implícita.

