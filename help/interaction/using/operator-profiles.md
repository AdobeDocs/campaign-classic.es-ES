---
solution: Campaign Classic
product: campaign
title: Perfiles de operador
description: Perfiles de operador
audience: interaction
content-type: reference
topic-tags: managing-environments
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 100%

---


# Perfiles de operador{#operator-profiles}

Existen dos tipos de operadores que utilizan interacción: gestores de oferta y gestores de envío. Cada una tiene derechos específicos que solo les proporcionan acceso a algunas partes del árbol y a la plataforma.

* **[!UICONTROL Offer manager]** : crea y mantiene ofertas. Tenga en cuenta que si se utilizan ofertas en el flujo de trabajo, el operador deberá estar en el grupo de operadores **[!UICONTROL Administrator]** o **[!UICONTROL Offer managers]** para ejecutar el flujo de trabajo.
* **[!UICONTROL Delivery manager]** : aprueba y utiliza ofertas

Los pasos para crear operadores específicos de interacción son idénticos a los utilizados para crear todos los demás operadores en la plataforma. Para obtener más información, consulte [esta sección](../../platform/using/access-management.md#creating-an-operator). Los derechos se configuran durante la creación del operador.

## Gestor de ofertas {#offer-manager}

1. Creación de un nuevo operador.
1. Vaya a la ventana **[!UICONTROL Groups and named rights]**, haga clic en **[!UICONTROL Add]** y seleccione el grupo **[!UICONTROL Offer manager]**.

   ![](assets/offer_operators_create_001.png)

Los derechos asignados al gestor de ofertas permiten realizar las siguientes tareas:

* Modificar entornos **[!UICONTROL Design]**.
* Ver entornos **[!UICONTROL Live]**.
* Configurar funciones de administración (espacios predefinidos y filtros).
* Cree y modifique categorías.
* Cree ofertas.
* Configurar la idoneidad de la oferta.
* Aprobar ofertas.

   >[!NOTE]
   >
   >El gestor de ofertas solo puede aprobar una oferta en dos casos determinados. El primero es si se especifica a alguien en particular como revisor y el segundo si el operador a cargo de la creación de plantillas (con derecho a asignar revisores) lo especificó como revisor en la plantilla de oferta en la que se basa la oferta.

## Gestor de envíos {#delivery-manager}

1. Creación de un nuevo operador.
1. Vaya a la ventana **[!UICONTROL Groups and named rights]**, haga clic en **[!UICONTROL Add]** y seleccione el grupo **[!UICONTROL Delivery manager]**.

   ![](assets/offer_operators_create_002.png)

Los derechos asignados al gestor de envíos son/permiten realizar las siguientes tareas:

* Mostrar entornos **[!UICONTROL Live]**.
* Mostrar y modificar las categorías de oferta.
* Aprobación de ofertas si se especifica como uno/a de sus revisores.

   >[!NOTE]
   >
   >El gestor de envíos solo puede aprobar una oferta si se ha definido como revisor durante la configuración de la oferta.

## Resumen de derechos según el operador {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Gestor de ofertas (edición)</strong><br /> </td> 
   <td> <strong>Gestor de ofertas (en directo)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Nivel de estructura de árbol</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Ofertas editadas/Ofertas en directo<br /> </td> 
   <td> Lectura/Escritura<br /> </td> 
   <td> Lectura<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinatario - Entorno<br /> </td> 
   <td> Lectura/Escritura<br /> </td> 
   <td> Lectura<br /> </td> 
  </tr> 
  <tr> 
   <td> Administración<br /> </td> 
   <td> Lectura/Escritura<br /> </td> 
   <td> Lectura<br /> </td> 
  </tr> 
  <tr> 
   <td> Espacios<br /> </td> 
   <td> Lectura/Escritura<br /> </td> 
   <td> Lectura<br /> </td> 
  </tr> 
  <tr> 
   <td> Filtros de oferta predefinidos<br /> </td> 
   <td> Lectura/Escritura<br /> </td> 
   <td> Lectura<br /> </td> 
  </tr> 
  <tr> 
   <td> Tipología<br /> </td> 
   <td> Lectura/Escritura<br /> </td> 
   <td> Lectura<br /> </td> 
  </tr> 
  <tr> 
   <td> Reglas de tipología<br /> </td> 
   <td> Lectura/Escritura<br /> </td> 
   <td> Lectura<br /> </td> 
  </tr> 
  <tr> 
   <td> Catálogo de ofertas<br /> </td> 
   <td> Lectura/Escritura<br /> </td> 
   <td> Lectura<br /> </td> 
  </tr> 
  <tr> 
   <td> Categoría de oferta<br /> </td> 
   <td> Lectura/Escritura<br /> </td> 
   <td> Lectura<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Gestor de envíos (edición)</strong><br /> </td> 
   <td> <strong>Gestor de envíos (en directo)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Nivel de estructura de árbol</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Ofertas editadas/Ofertas en directo<br /> </td> 
   <td> </td> 
   <td> Lectura<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinatario - Entorno<br /> </td> 
   <td> </td> 
   <td> Lectura<br /> </td> 
  </tr> 
  <tr> 
   <td> Administración<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Espacios<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Filtros de oferta predefinidos<br /> </td> 
   <td> Lectura<br /> </td> 
   <td> Lectura<br /> </td> 
  </tr> 
  <tr> 
   <td> Tipología<br /> </td> 
   <td> Lectura<br /> </td> 
   <td> Lectura<br /> </td> 
  </tr> 
  <tr> 
   <td> Reglas de tipología<br /> </td> 
   <td> </td> 
   <td> Lectura<br /> </td> 
  </tr> 
  <tr> 
   <td> Catálogo de ofertas<br /> </td> 
   <td> Lectura<br /> </td> 
   <td> Lectura<br /> </td> 
  </tr> 
  <tr> 
   <td> Categoría de oferta<br /> </td> 
   <td> </td> 
   <td> Lectura<br /> </td> 
  </tr> 
 </tbody> 
</table>

