---
title: Traducción de una aplicación web
seo-title: Traducción de una aplicación web
description: Traducción de una aplicación web
seo-description: null
page-status-flag: never-activated
uuid: 7b24a872-d3d1-4473-a6f9-96ba2a0eee8b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 328e5b2f-8596-4eda-8ac5-57cb29bfb691
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Traducción de una aplicación web{#translating-a-web-application}

Puede traducir páginas de aplicaciones web creadas con el editor de contenido digital (DCE) de Adobe Campaign.

If you select at least one additional language via the **[!UICONTROL Localization]** tab in the **[!UICONTROL Properties]** of a Web application, a new option becomes available when adding an HTML content block in a page edited with DCE.

Esta opción le permite indicar si el contenido del bloque debe traducirse o no.

Strings to be translated are collected the same way as the other strings of the Web application, via the **[!UICONTROL Translations]** tab of the application. Para obtener más información, consulte [esta página](../../web/using/translating-a-web-form.md).

Para marcar las cadenas que se deben traducir:

1. Abra una página de contenido editada con DCE en una aplicación web.

   ![](assets/dce_translation_3.png)

1. Seleccione un bloque HTML.
1. In the parameters block on the right, the **[!UICONTROL Localization]** option lets you flag the content of the selected block. De forma predeterminada, solo se debe traducir el título de la página.

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >Las cadenas no deben superar los 1023 caracteres.

   Existen tres casos específicos:

   * Cuando el bloque seleccionado contiene varias cadenas o bloques, se marca como una sola cadena que se debe traducir. Entonces, la cadena contiene el código HTML de los elementos de este bloque.
   * Cuando se desea marcar un bloque que contiene varias cadenas y al menos una de ellas está marcada, se muestra un mensaje de advertencia. A continuación, se puede eliminar la marca de la cadena aislada y añadir el bloque completo.

      ![](assets/dce_translation_4.png)

   * Si desea eliminar la marca de una cadena contenida en un bloque que ya está marcado, no se puede modificar directamente la opción de traducción de la cadena. Sin embargo, puede acceder al bloque que contiene la cadena para cambiarla.

      ![](assets/dce_translation_2.png)

1. Once you have finished flagging the strings, go back to the Web application and select the **[!UICONTROL Translations]** tab.
1. Select **[!UICONTROL Collect the strings to translate]**. Las cadenas marcadas en el DCE se añaden a las cadenas de la aplicación web.

   >[!NOTE]
   >
   >Una vez que estén recopiladas las cadenas, estas no se quitan de la lista si se elimina la marca de traducción en el DCE. Esto permite mantenerlos en la memoria de traducción.

1. Traducción y aprobación de las cadenas.

   You can then preview the translations by selecting the desired language from the **[!UICONTROL Preview]** tab in the Web application.

