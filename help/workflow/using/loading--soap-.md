---
solution: Campaign Classic
product: campaign
title: Carga (SOAP)
description: Carga (SOAP)
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: ht
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: ht
source-wordcount: '251'
ht-degree: 100%

---


# Carga (SOAP){#loading-soap}

>[!CAUTION]
>
>La actividad **Loading (SOAP)** solo está disponible si tiene instalado el módulo **FDA (Federated Data Access)**. Compruebe el acuerdo de licencia.

La actividad **Load (SOAP)** se utiliza además de la actividad de **data loading (RDBMS)** cuando no es posible recopilar datos directamente mediante el FDA en una base de datos externa.

La operación es la siguiente:

1. Seleccione entre utilizar un ejemplo XML o un WSDL.

   El siguiente ejemplo proviene de un flujo de trabajo técnico del módulo Centro de mensajes.

   ![](assets/load_soap_002.png)

1. Para un ejemplo XML, seleccione un archivo de muestra. El archivo se analiza para establecer un ejemplo del resultado.

   Para un WSDL, introduzca la URL de acceso coincidente y, a continuación, genere el código esquemático. El servicio y la llamada seleccionados se actualizan y se muestran automáticamente.

   ![](assets/soap_load_003.png)

1. Seleccione **[!UICONTROL Click here to view and edit analysis results]** para especificar cada columna identificada.

   ![](assets/soap_load_001.png)

   Si desea actualizar el ejemplo, seleccione **[!UICONTROL Re-analyze the example]**.

   También puede personalizar el formato de los datos de la columna a través del vínculo **[!UICONTROL Advanced parameters]**. Para obtener más información sobre formatear datos importados, consulte esta [sección](../../platform/using/executing-import-jobs.md).

1. Puede utilizar el número de línea como identificador o especificar que la llamada SOAP devuelva varios elementos.
1. Introduzca los siguientes scripts de pestañas según su función:

   * **[!UICONTROL Initialization]**: establece una conexión SOAP.
   * **[!UICONTROL Iteration]**: realiza la llamada al servicio SOAP. El retorno de esta función debe ser un objeto XML compatible con la descripción del ejemplo o el WSDL.

      Adobe Campaign llama al código de esta pestaña hasta que devuelva un objeto XML nulo.

   * **[!UICONTROL Finalization]**: cierra la conexión o libera otros recursos creados durante el procesamiento.

