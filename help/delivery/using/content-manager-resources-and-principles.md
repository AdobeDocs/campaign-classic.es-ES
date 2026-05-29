---
product: campaign
title: Recursos y principios del gestor de contenido
description: Recursos y principio del gestor de contenido
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Templates
role: User, Developer
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
TQID: https://experienceleague.adobe.com/xWBOrnm4v7N3XOVvOcPNqngz0cDvvT39tI3xJVKdFZg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: ce44533e-8ec8-4e11-a9e9-78b0fe561832
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 247
ht-degree: 100%

---

# Recursos y principios del gestor de contenido{#content-manager-resources-and-principles}


Se debe definir una plantilla de publicación que contenga plantillas de transformación para cada contenido.

Un bloque de contenido se estructura en un documento XML para el almacenamiento de datos. Se utiliza una interfaz de edición para introducir el contenido de la consola del cliente de Adobe Campaign o mediante un explorador Web. El contenido también se puede introducir automáticamente mediante la captura de flujo XML o datos recopilados en una base de datos.

Al combinar el documento XML y las hojas de estilo de plantilla XSL o JavaScript, se genera automáticamente la proyección de la plantilla de publicación en los distintos formatos (HTML, texto).

![](assets/d_ncs_content_process.png)

Se requieren los siguientes recursos para la configuración del contenido:

* Esquemas de datos: descripción de la estructura de contenido XML. Para obtener más información, consulte [Esquemas de datos](data-schemas.md).
* Formularios de entrada de datos: construcción de pantallas de entrada de datos. Para obtener más información, consulte [Formularios de entrada](input-forms.md).
* Imágenes: imágenes utilizadas en los formularios de entrada de datos. Para obtener más información, consulte [Administración de imágenes](formatting.md#image-management).
* Hojas de estilo: formato de documentos de salida con lenguaje XSLT. Para obtener más información, consulte [Formato](formatting.md).
* Plantillas JavaScript: formato de documentos de salida con lenguaje JavaScript. Para obtener más información, consulte [Plantillas de publicación](publication-templates.md).
* Códigos JavaScript: Códigos JavaScript para la adición de datos. Para obtener más información, consulte [Acumulador](publication-templates.md#aggregator).
* Plantillas de publicación: definición de plantillas de publicación. Para obtener más información, consulte [Plantillas de publicación](publication-templates.md).
* Contenido: instancias de contenido para crear y publicar. Para más información, consulte [Uso de una plantilla de contenido](using-a-content-template.md).
