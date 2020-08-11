---
title: Definir la audiencia correcta
seo-title: Definir la audiencia correcta
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 6%

---


# Definir la audiencia correcta {#define-the-right-audience}

La población objetivo es clave: cree sus listas con cuidado, pruebe sus correos electrónicos en clientes de correo electrónico y dispositivos móviles populares y asegúrese de que sus listas de correo electrónico estén actualizadas (sin direcciones desconocidas u obsoletas). También puede enviar pruebas que ayuden a configurar un ciclo de validación completo.

Más información sobre las poblaciones de destinatarios [en esta sección](../../delivery/using/steps-defining-the-target-population.md)

## Destinatario de la audiencia correcta {#target-the-right-audience}

Cuando tenga preparado el contenido, debe definir cuidadosamente quién recibirá el mensaje.

Para que su envío tenga éxito, desea enviar el contenido personalizado más relevante a los destinatarios adecuados. Adobe Campaign le permite crear el destinatario más preciso: puede seleccionar destinatarios según su edad, localización, lo que compraron, si hicieron clic en un vínculo en un envío anterior, etc. Con Adobe Campaign, también puede definir perfiles, grupos de control y direcciones semilla de prueba para asegurarse de que el destinatario es correcto.

## Asignaciones de destino {#target-mappings}

En Campaign Classic, de forma predeterminada, Plantilla de envíos **Destinatarios** de destinatario. Adobe Campaign oferta otras asignaciones de destino para sus envíos, que puede cambiar según sus necesidades.

Por ejemplo, puede entregar a visitantes cuyos perfiles se hayan recopilado a través de las redes sociales o a visitantes suscritos a un servicio informativo.

Estas asignaciones se presentan [en esta sección](../../delivery/using/selecting-a-target-mapping.md).

También puede crear y utilizar una asignación de destino personalizada. Para obtener más información, consulte [esta sección](../../configuration/using/target-mapping.md).

## Destinatarios externos {#external-recipients}

Puede enviar a destinatarios que estén almacenados en un archivo externo en lugar de guardarlos en la base de datos. Learn more [in this section](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

## Enviar a sus suscriptores {#send-to-subscribers}

Para enviar mensajes a los suscriptores de una newsletter, puede enviar directamente el destinatario de los suscriptores al servicio informativo correspondiente. Learn more [in this section](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## Destinatarios y direcciones semilla de prueba {#test-recipients-seed-addresses}

Para probar el envío, utilice pruebas antes de enviar al destinatario principal.

Asegúrese de seleccionar los destinatarios de prueba adecuados, ya que validan el formulario y el contenido del mensaje. Los pasos para definir los destinatarios de prueba se presentan [en esta sección](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target).

Las direcciones semilla se utilizan para destinatario de destinatarios que no coinciden con los criterios de destinatario definidos para probar un envío antes de enviarlo al destinatario principal. They are presented [in this section](../../delivery/using/about-seed-addresses.md).

## Desduplicar direcciones {#deduplicate-addresses}

Es importante evitar tener direcciones de correo electrónico de duplicado, ya que esto puede tener un impacto en el destinatario:

* El mismo mensaje se puede enviar más de una vez cuando se divide un destinatario.

* Si un destinatario deja de suscribirse después de recibir un mensaje, su perfil de duplicado seguirá recibiendo mensajes futuros.

La desduplicación de direcciones protege su reputación de envío y garantiza una buena administración de cuarentenas.

Obtenga más información [en este caso](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery)de uso.

## Indizar direcciones de correo electrónico {#index-addresses}

Para optimizar el rendimiento de las consultas SQL utilizadas en la aplicación, se puede declarar un índice a partir del elemento principal del esquema de datos.

Los pasos para agregar un índice a la dirección de correo electrónico se presentan [en esta sección](../../configuration/using/database-mapping.md#indexed-fields).
