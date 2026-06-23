---
product: campaign
title: Datos adicionales
description: Datos adicionales
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 01adb584-5308-4d41-a6f1-223a97efa10f
TQID: https://experienceleague.adobe.com/OU8fQxcH3HXoSJbG-N-9DplMjkDVAT6tLXY-FWzPuwE
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 711
ht-degree: 100%

---

# Datos adicionales{#additional-data}



Durante una llamada al motor de interacción, se puede transferir información adicional contextual. Estos datos pueden proceder de los datos de destino almacenados en la tabla de trabajo de un flujo de trabajo (canal saliente) o de los datos de llamada enviados mediante el sitio web durante la llamada (canal entrante). Se puede utilizar estos datos adicionales en las reglas de elegibilidad, en la personalización de ofertas, y también almacenarlos en una tabla de propuestas.

Para el canal entrante, puede resultar útil recuperar información como el idioma del explorador de la persona que consulta la oferta o el nombre del agente del centro de llamadas, por ejemplo. Se puede utilizar estos datos de llamada en las reglas de elegibilidad para presentar una oferta solo a aquellas personas que vean la página web en francés o en inglés.

En un flujo de trabajo de destino (canal saliente), se pueden utilizar los datos de destino durante una llamada al motor. Por ejemplo, se puede enriquecer el destino con datos de una transacción vinculada de destinatario o con una base de datos externa, a través de FDA.

## Configuraciones de datos adicionales {#additional-data-configuration}

Debe ampliar el esquema **nms:interaction** vinculado al entorno y declarar la lista de campos adicionales que se utilizarán durante una llamada al motor de interacción. Al crear la regla de elegibilidad o al personalizar una oferta, estos campos van a ser accesibles desde el nodo **Interaction** (consulte [Usar datos adicionales](#using-additional-data)).

Para el canal entrante, se deben añadir los campos de datos de llamada al nodo **Interaction**.

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

>[!NOTE]
>
>Las colecciones XML se admiten en el canal entrante, pero los vínculos a otros esquemas no.

Para el canal saliente, se debe añadir un elemento **targetData** que contenga los campos adicionales al nodo **Interaction**.

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <element name="targetData">
    <attribute label="Date of last transaction" name="lastTransactionDate" type="datetime"/>
  </element>
</element>
```

>[!NOTE]
>
>Las colecciones no son compatibles con el canal saliente. Sin embargo, se pueden crear vínculos con otros esquemas.

Si desea almacenar estos datos en la tabla de propuestas, también debe ampliar el esquema **nms:propositionRcp** y declarar estos campos.

```
<element label="Recipient offer propositions" labelSingular="Recipient offer proposition" name="propositionRcp">
  <attribute label="Last transaction date" name="lastTransactionDate" type="datetime"/>
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

## Implementación de datos adicionales {#additional-data-implementation}

### Canal de entrada (página web) {#input-channel--web-page-}

Para transferir datos adicionales al llamar al motor, se debe añadir la variable **interactionGlobalCtx** al código JavaScript de la página web. Inserte el nodo **Interaction** que contiene los datos de llamada en esta variable. Debe respetar la misma estructura xml que se hay en el esquema **nms:interaction**. Consulte: [Configuración de datos adicional](#additional-data-configuration).

```
interactionGlobalCtx = "<interaction navigationLanguage='"+myLanguage+"'/>";
```

### Canal de salida {#output-channel}

Debe crear un flujo de trabajo de segmentación que carga datos adicionales en la tabla de trabajo respetando la misma estructura xml y los mismos nombres internos que hay en el esquema **nms:interaction**. Consulte: [Configuración de datos adicional](#additional-data-configuration).

## Uso de datos adicionales {#using-additional-data}

### Reglas de elegibilidad {#eligibility-rules}

Se pueden utilizar los datos adicionales en las reglas de elegibilidad para ofertas, categorías y ponderaciones.

Por ejemplo, se puede elegir que la oferta se muestre únicamente a las personas que ven la página en inglés.

![](assets/ita_calldata_query.png)

>[!NOTE]
>
>Se debe limitar la regla en los canales para los que se definen los datos. En este ejemplo, se limita la regla en el canal web entrante (campo **[!UICONTROL Taken into account if]**).

### Personalización {#personalization}

Asimismo, se pueden utilizar estos datos adicionales al personalizar una oferta. Por ejemplo, se puede agregar una condición para el idioma de navegación.

![](assets/ita_calldata_perso.png)

>[!NOTE]
>
>Se debe limitar la personalización en los canales para los que se definen los datos. En este ejemplo, se limita la regla en el canal web entrante.

Si se ha personalizado una oferta con datos adicionales, estos datos no van a aparecer en la vista previa de manera predeterminada ya que no está disponible en la base de datos. En la pestaña **[!UICONTROL Example of call data]** del entorno, se deben añadir muestras de valor para utilizarlas en la vista previa. Respete la misma estructura xml que hay en la extensión del esquema **nms:interaction**. Para obtener más información, consulte [Configuración de datos adicional](#additional-data-configuration).

![](assets/ita_calldata_preview.png)

Al obtener una vista previa, haga clic en **[!UICONTROL Content personalization options for the preview]** y seleccione un valor en el campo **[!UICONTROL Call data]**.

![](assets/ita_calldata_preview2.png)

### Almacenamiento {#storage}

Durante una llamada al motor, se pueden almacenar datos adicionales en la tabla de propuestas para enriquecer la base de datos. Estos datos se pueden utilizar, por ejemplo, en los informes, en los cálculos de ROI o en los procesos posteriores.

>[!NOTE]
>
>Debe haber ampliado el esquema **nms:propositionRcp** y declarado los campos que contendrán los datos que se van a almacenar. Para más información sobre esto: [Configuración de datos adicional](#additional-data-configuration).

En el espacio de oferta, vaya a la pestaña **[!UICONTROL Storage]** y haga clic en el botón **[!UICONTROL Add]**.

En la columna **[!UICONTROL Storage path]**, seleccione el campo de almacenamiento en la tabla de propuestas. En la columna **[!UICONTROL Expression]**, seleccione el campo adicional del nodo **[!UICONTROL Interaction]**.

Se puede recuperar los datos de llamada cuando la propuesta se genere o cuando se acepte (cuando la persona haga clic en la oferta).

![](assets/ita_calldata_storage.png)
