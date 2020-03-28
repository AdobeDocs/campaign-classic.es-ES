---
title: Carga (SOAP)
seo-title: Carga (SOAP)
description: Carga (SOAP)
seo-description: null
page-status-flag: never-activated
uuid: 80597892-e363-48f6-8633-faad161064a4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 94178104-f8ba-4c17-8ff9-928c5d2df1b7
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

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

   También puede personalizar el formato de los datos de la columna a través del vínculo **[!UICONTROL Advanced parameters]**. Para obtener más información sobre formatear datos importados, consulte esta [sección](../../platform/using/importing-data.md#import-wizard).

1. Puede utilizar el número de línea como identificador o especificar que la llamada SOAP devuelva varios elementos.
1. Introduzca los siguientes scripts de pestañas según su función:

   * **[!UICONTROL Initialization]**: establece una conexión SOAP.
   * **[!UICONTROL Iteration]**: realiza la llamada al servicio SOAP. El retorno de esta función debe ser un objeto XML compatible con la descripción del ejemplo o el WSDL.

      Adobe Campaign llama al código de esta pestaña hasta que devuelva un objeto XML nulo.

   * **[!UICONTROL Finalization]**: cierra la conexión o libera otros recursos creados durante el procesamiento.

