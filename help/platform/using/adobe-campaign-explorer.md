---
solution: Campaign Classic
product: campaign
title: Uso del explorador de Adobe Campaign
description: Aprenda a utilizar el explorador de Campaign
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 21656cc2-15a1-4156-8897-ea4fe3e9b97f,f91d69a4-b794-40f0-b450-de862d7333e2
translation-type: ht
source-git-commit: 8405eefb2e79deeeca07e0c8231bdfa5200ec185
workflow-type: ht
source-wordcount: '441'
ht-degree: 100%

---

# Uso del explorador de Adobe Campaign {#using-adobe-campaign-explorer}

Es posible acceder al explorador de Adobe Campaign mediante el icono de la barra de herramientas. Le permite acceder a todas las funcionalidades de Adobe Campaign, a las pantallas de configuración y a una vista más detallada de algunos de los elementos de la plataforma.

El espacio de trabajo de **[!UICONTROL Explorer]** se divide en tres zonas:

![](assets/s_ncs_user_navigation.png)

**1 - Árbol**: Puede personalizar el contenido del árbol (añadir, mover o eliminar nodos). Este procedimiento está diseñado para usuarios expertos. Para obtener más información, consulte [esta sección](#about-navigation-hierarchy)).

**2 - Lista**: Puede filtrar esta lista, ejecutar búsquedas, añadir información u ordenar datos. [Más información](adobe-campaign-ui-lists.md).

**3 - Detalles**: Puede mostrar los detalles del elemento seleccionado. El icono de la sección superior derecha le permite mostrar esta información en formato de pantalla completa.

## Carpetas y árbol de navegación{#about-navigation-hierarchy}

El árbol de navegación funciona como un explorador de archivos (por ejemplo, el Explorador de Windows). Las carpetas pueden contener subcarpetas. Al seleccionar un nodo, se muestra la vista correspondiente al nodo.

La vista mostrada es una lista asociada con un esquema y un formulario de entrada para editar la línea seleccionada.

![](assets/d_ncs_integration_navigation.png)

Para añadir una carpeta nueva al árbol, haga clic con el botón derecho en la carpeta de la rama en la que desea insertar una carpeta y seleccione **[!UICONTROL Add new folder]**. En el menú contextual, seleccione el tipo de archivo que desea crear.

![](assets/d_ncs_integration_navigation_create.png)

Aprenda a configurar el árbol de navegación de Campaign [en esta sección](../../configuration/using/configuration.md).

Aprenda a configurar permisos en carpetas [en esta sección](access-management-folders.md).

## Prácticas recomendadas para la configuración de carpetas

* **Uso de carpetas integradas**

   El uso de las carpetas integradas facilita a las personas que no participan en el proyecto el uso, el mantenimiento y la resolución de problemas de la aplicación. No debe crear estructuras de carpetas personalizadas para destinatarios, listas, envíos, etc., sino utilizar las carpetas estándar como Administración, Perfiles y Objetivos, y Administración de campaña.

* **Creación de subcarpetas**

   Coloque los flujos de trabajo técnicos en la carpeta estándar: Administración/Producción/Flujos de trabajo técnicos y cree subdirectorios por tipo de flujo de trabajo.

* **Definición de una convención de nombres**

   Por ejemplo, puede asignar un nombre a los flujos de trabajo en orden alfabético, de modo que aparezcan ordenados en orden de ejecución.

   Por ejemplo:

   * A1 – importar destinatarios, comienza a las 10:00;
   * A2 – importar tickets, empieza a las 11:00.

* **Creación de plantillas para que los usuarios empiecen con ellas**

   Cree plantillas de envío, plantillas de flujo de trabajo y plantillas de campaña específicas para los usuarios. Esta estructura puede ahorrar tiempo y garantizar que se utilicen la asignación de envíos y las tipologías adecuadas para cada usuario.

## Resolución de la pantalla {#screen-resolution}

Para conseguir la mejor navegación y una gran facilidad de uso, Adobe recomienda utilizar una resolución de pantalla mínima de 1600x900 píxeles.

>[!CAUTION]
>
>Adobe Campaign admite resoluciones inferiores a 1600x900 píxeles.

En el espacio de trabajo de **[!UICONTROL Explorer]**, si algunas partes de la zona de **[!UICONTROL Details]** aparecen truncadas, puede expandirlas utilizando la flecha situada en la parte superior de la zona o haciendo clic en el botón **[!UICONTROL Enlarge]**.

![](assets/s_ncs_user_resolution.png)

## Examen y personalización de listas {#browsing-lists}

Aprenda a examinar, administrar y personalizar listas [en esta sección](adobe-campaign-ui-lists.md).
