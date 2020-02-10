---
title: Sobre las direcciones sembradas
seo-title: Sobre las direcciones sembradas
description: Sobre las direcciones sembradas
seo-description: null
page-status-flag: never-activated
uuid: 80ab5abc-3ae0-484d-88c0-be039aac360d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: b49acfd0-b601-4694-88e3-cc0a169cb866
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0ce6e5277c32bc18c20dca62e5b276f654d1ace5

---


# Sobre las direcciones sembradas{#about-seed-addresses}

Las direcciones sembradas se utilizan para dirigirse a los destinatarios que no coinciden con los criterios de destino definidos. De este modo, los destinatarios que estén fuera del alcance del envío pueden recibirlo como lo haría cualquier otro destinatario.

Una de las razones principales para utilizarlas es **la protección de su lista de correo**. La inclusión de direcciones sembradas en la lista de correo permite comprobar si la está utilizando un tercero, ya que las direcciones que contiene reciben los envíos enviados a la misma.

Moreover, seed addresses let you **preview and test the deliveries personalization and rendering** before their sending, by sending them proofs (see [Using seed addresses as proof](../../delivery/using/steps-validating-the-delivery.md#using-seed-addresses-as-proof)).

La función de direcciones sembradas tiene las siguientes ventajas:

* Random substitution of fields with data taken from recipient profiles: this lets you enter only the email address, for instance in the seed address section, and let Campaign automatically fill in the other fields form the profile (see [Use case: configuring the field substitution](../../delivery/using/use-case--configuring-the-field-substitution.md)).
* Al utilizar un flujo de trabajo con funciones de gestión de datos, los datos adicionales procesados en los envíos se pueden introducir a nivel de la dirección sembrada para forzar los valores, esto evita la sustitución de valores aleatorios.
* Las direcciones sembradas se excluyen automáticamente de los informes en las siguientes estadísticas de envío: **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

Las direcciones sembradas se añaden al destino de los envíos mediante su importación o su creación directamente en el envío o la campaña.

>[!NOTE]
>
>Las direcciones sembradas no pertenecen a la lista de distribución, sino que se crean en una lista independiente. Si se amplía la lista de distribución con nuevos datos, debe ampliar la lista de direcciones sembradas con los mismos datos. De lo contrario, los campos ampliados no tienen en cuenta las direcciones sembradas.
>
>En esta sección se presenta un ejemplo de cómo extender la tabla de direcciones de inicio: Caso [de uso: seleccionar direcciones de raíz en los criterios](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)

En los envíos por correo postal, las direcciones sembradas se añaden durante la extracción y se mezclan en el documento de salida.

>[!CAUTION]
>
>En los envíos por correo postal, el formato del archivo de extracción debe cumplir con las siguientes limitaciones:
>
>* No debe utilizar la opción **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* If element collections are extracted, these fields will have an empty value for the seed addresses, unless the **[!UICONTROL Single row (expert user)]** option is selected. Para obtener más información, consulte [esta sección](../../platform/using/exporting-data.md#step-7---data-formatting).
>


