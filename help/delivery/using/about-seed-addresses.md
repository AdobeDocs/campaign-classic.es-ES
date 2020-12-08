---
solution: Campaign Classic
product: campaign
title: Sobre las direcciones semilla
description: Sobre las direcciones semilla
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '376'
ht-degree: 100%

---


# Sobre las direcciones semilla{#about-seed-addresses}

Las direcciones semilla se utilizan para dirigirse a los destinatarios que no coinciden con los criterios de destino definidos. De este modo, los destinatarios que estén fuera del alcance de la entrega pueden recibirlo como lo haría cualquier otro destinatario.

Una de las razones principales para utilizarlas es **la protección de su lista de correo**. La inclusión de direcciones semilla en la lista de correo permite comprobar si la está utilizando un tercero, ya que las direcciones que contiene reciben las entregas enviados a la misma.

Además, las direcciones semilla permiten **previsualizar y probar la personalización y la renderización de las entregas** antes de la entrega mediante la entrega de pruebas (consulte [Uso de direcciones semilla como prueba](../../delivery/using/steps-defining-the-target-population.md#using-seed-addresses-as-proof).

![](assets/do-not-localize/how-to-video.png) [Descubra esta función en vídeo](../../delivery/using/steps-defining-the-target-population.md#seeds-and-proofs-video)

La función de direcciones semilla tiene las siguientes ventajas:

* Sustitución aleatoria de campos con datos tomados de perfiles de destinatarios: esto permite introducir únicamente la dirección de correo electrónico, por ejemplo, en la sección de la dirección semilla; además, permite que Campaign rellene automáticamente los demás campos de formulario del perfil (consulte [Caso de uso: configuración del reemplazo de campo](../../delivery/using/use-case--configuring-the-field-substitution.md)).
* Al utilizar un flujo de trabajo con funciones de gestión de datos, los datos adicionales procesados en las entregas se pueden introducir a nivel de la dirección semilla para forzar los valores, esto evita la sustitución de valores aleatorios.
* Las direcciones sembradas se excluyen automáticamente de los informes en las siguientes estadísticas de envío: **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

Las direcciones semilla se añaden al destino de las entregas mediante su importación o su creación directamente en la entrega o la campaña.

>[!NOTE]
>
>Las direcciones semilla no pertenecen a la lista de distribución, sino que se crean en una lista independiente. Si se amplía la lista de distribución con nuevos datos, debe ampliar la lista de direcciones semilla con los mismos datos. De lo contrario, los campos ampliados no tienen en cuenta las direcciones semilla.
>
>En esta sección se presenta un ejemplo de cómo ampliar la tabla de direcciones semilla: [Caso de uso: selección de direcciones semilla en base a criterios](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

En las entregas por correo postal, las direcciones semilla se añaden durante la extracción y se mezclan en el documento de salida.

>[!IMPORTANT]
>
>En las entregas por correo postal, el formato del archivo de extracción debe cumplir con las siguientes limitaciones:
>
>* No se debe utilizar la opción **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* Si se extraen colecciones de datos, estos campos deben tener un valor vacío para las direcciones semilla, a menos que se seleccione la opción **[!UICONTROL Single row (expert user)]**. Para obtener más información, consulte [esta sección](../../platform/using/exporting-data.md#step-7---data-formatting).
>


