---
product: campaign
title: Diseño de una aplicación web
description: Diseño de una aplicación web
feature: Web Apps
exl-id: dcdf6afc-321e-4027-a350-fff6bbf22e71
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: ht
source-wordcount: '256'
ht-degree: 100%

---

# Diseño de una aplicación web{#designing-a-web-application}

![](../../assets/common.svg)

Las aplicaciones web se crean y se administran según el mismo principio que los [formularios web](about-web-forms.md).

>[!CAUTION]
>
>Utilice la subpestaña **[!UICONTROL Preview]** para comprobar los errores durante el diseño de la aplicación web.
>
>Hasta que se publique la aplicación web, los cambios no estarán expuestos a los usuarios finales.

## Inserción de gráficos en una aplicación web {#inserting-charts-in-a-web-application}

Se pueden incluir gráficos en las aplicaciones web. Para ello, utilice la lista desplegable de la barra de herramientas para seleccionar el tipo de gráfico que desea insertar.

![](assets/s_ncs_admin_webapps_bar_graph.png)

También puede seleccionar el menú **[!UICONTROL Add a chart]**.

![](assets/s_ncs_admin_webapps_graph.png)

## Inserción de tablas en una aplicación web {#inserting-tables-in-a-web-application}

Para añadir una tabla, utilice la lista desplegable de la barra de herramientas para seleccionar el tipo de tabla que desea utilizar.

![](assets/s_ncs_admin_webapps_bar_table.png)

También puede seleccionar el tipo de tabla en el menú desplegable.

![](assets/s_ncs_admin_webapps_table.png)

## Aplicaciones web de tipo “descripción general” {#overview-type-web-applications}

La interfaz de Adobe Campaign utiliza muchas aplicaciones web para acceder, gestionar e interactuar con destinatarios, envíos, campañas, inventarios, etc.

Se visualizan en la interfaz en forma de paneles con una sola página.

Las aplicaciones web listas para su uso se almacenan en el nodo **[!UICONTROL Administration > Configuration > Web applications]**.

## Edición de aplicaciones web de tipo de formulario {#edit-forms-type-web-applications}

Las aplicaciones web de edición de formularios para una extranet se caracterizan por:

* Un cuadro de precarga

   En la mayoría de los casos, los datos a visualizar deben estar precargados. Dado que los usuarios que acceden a estos formularios se han identificado (mediante un control de acceso), la precarga no tiene por qué estar cifrada.

* Un cuadro de guardado
* Adición de páginas

   Mientras que las aplicaciones web de tipo “descripción general” tienen una sola página, los formularios de edición pueden ofrecer una secuencia de páginas según criterios específicos (testeo, variables, perfil del operador conectado, etc.).

