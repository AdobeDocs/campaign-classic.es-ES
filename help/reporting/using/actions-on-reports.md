---
product: campaign
title: Acciones sobre los informes
description: Acciones sobre los informes
feature: Reporting, Monitoring
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
exl-id: b30cdeaf-4ad6-473d-bdbc-91984755b609
TQID: https://experienceleague.adobe.com/ds9tKPie-3bcx7H-4tyN2Naq4SgX1ZXJavXvMTYVu8A
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
  - id: cfda811a-e413-43a4-adf0-7370888f5cfc
  - id: afe938ea-bc18-44a4-a3fb-03e1031466cb
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 554
ht-degree: 100%

---

# Acciones sobre los informes{#actions-on-reports}



Al visualizar un informe, la barra de herramientas permite realizar diversas acciones. A continuación se detallan dichas acciones.

![](assets/s_ncs_advuser_report_wizard_2.png)

Por ejemplo, la barra de herramientas permite exportar, imprimir, archivar o mostrar el informe en un navegador web.

![](assets/s_ncs_advuser_report_wizard_04.png)

## Exportación de un informe {#exporting-a-report}

Seleccione el formato en el que desee exportar el informe desde la lista desplegable. (.xls, .pdf, .ods).

![](assets/s_ncs_advuser_report_wizard_06.png)

Cuando un informe contiene varias páginas, se debe repetir la operación con cada página.

Se puede configurar el informe con el fin de exportarlo en formato PDF, Excel u OpenOffice. Abra Adobe Campaign Explorer y seleccione el informe correspondiente.

En la pestaña **[!UICONTROL Page]**, se accede a las opciones de exportación a través de las actividades **[!UICONTROL Advanced]** del informe.

Cambie la configuración de **[!UICONTROL Paper]** y **[!UICONTROL Margins]** para adaptarla a sus necesidades. También se puede autorizar la exportación de una página solo en formato PDF. Para ello, desmarque la opción **[!UICONTROL Activate OpenOffice/Microsoft Excel export]**.

![](assets/s_ncs_advuser_report_wizard_021.png)

### Exportación a Microsoft Excel {#exporting-into-microsoft-excel}

Para informes de tipo **[!UICONTROL List with group]** que se van a exportar a Excel, se aplican las siguientes recomendaciones y limitaciones:

* Estos informes no deben contener ninguna línea vacía.

  ![](assets/export_limitations_remove_empty_line.png)

* El pie de la lista debe estar oculto.

  ![](assets/export_limitations_hide_label.png)

* Los informes no deben utilizar un formato específico definido al nivel de celda. Es preferible utilizar **[!UICONTROL Form rendering]** para definir el formato de las celdas de la tabla. Se puede acceder a **[!UICONTROL Form rendering]** a través de **[!UICONTROL Administration > Configuration > Form rendering]**.
* No se recomienda insertar contenido HTML.
* Si un informe contiene varios elementos de tipo tabla, gráfico, etc., se exportan uno debajo del otro.
* Se puede forzar el retorno de carro en las celdas: esta configuración se conserva en Excel. Para obtener más información, consulte [esta sección](../../reporting/using/creating-a-table.md#defining-cell-format).

### Aplazamiento de la exportación {#postpone-the-export}

Se puede aplazar la exportación de un informe, por ejemplo para esperar las llamadas asíncronas. Para ello, introduzca el siguiente parámetro en la secuencia de comandos de inicialización de la página:

```
document.nl_waitBeforeRender = true;
```

Para activar la exportación e iniciar la conversión en un archivo PDF, utilice la función **document.nl_renderToPdf()** sin ningún parámetro.

### Asignación de memoria {#memory-allocation}

Al exportar ciertos informes de gran tamaño, pueden producirse errores de asignación de memoria.

En algunos casos, el valor predeterminado **maxMB** (**SKMS** para instancias alojadas) de JavaScript indicado en el archivo de configuración **serverConf.xml** se establece en 64 MB. Si se producen errores de memoria insuficiente al exportar un informe, se recomienda aumentar esta cifra a 512 MB:

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

Para aplicar los cambios realizados en la configuración, es necesario reiniciar el servicio **nlserver**.

Para obtener más información sobre el archivo **serverConf.xml**, consulte [esta sección](../../production/using/configuration-principle.md).

Para obtener más información sobre el servicio **nlserver**, consulte [esta sección](../../production/using/administration.md).

## Impresión de un informe {#printing-a-report}

Se puede imprimir el informe. Para ello, haga clic en el icono de impresora: esto abre el cuadro de diálogo correspondiente.

Para obtener un mejor resultado, edite las opciones de impresión de Explorer y seleccione **[!UICONTROL Print background colors and images]**.

![](assets/s_ncs_advuser_report_print_options.png)

## Creación de archivos de informes {#creating-report-archives}

El archivado de un informe permite crear una vista del informe en varios periodos, por ejemplo para mostrar las estadísticas de un periodo determinado.

Para crear un archivo, abra el informe correspondiente y haga clic en el icono adecuado.

![](assets/s_ncs_advuser_report_wizard_07.png)

Para mostrar u ocultar los archivos existentes, haga clic en el icono mostrar/ocultar.

![](assets/s_ncs_advuser_report_history_06.png)

Las fechas de archivo se muestran bajo el icono mostrar/ocultar. Haga clic en el archivo para verlo.

![](assets/s_ncs_advuser_report_history_04.png)

Es posible eliminar un archivo de informes. Para ello, vaya al nodo de Adobe Campaign donde se almacenan los informes. Haga clic en la pestaña **[!UICONTROL Archives]**, seleccione el que desee eliminar y haga clic en **[!UICONTROL Delete]**.

![](assets/s_ncs_advuser_report_history_01.png)
