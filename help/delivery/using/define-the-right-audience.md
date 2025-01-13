---
product: campaign
title: Definición de la audiencia correcta
description: Conozca las prácticas recomendadas al seleccionar su audiencia
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Audiences
role: User
hide: true
hidefromtoc: true
exl-id: c0533148-b027-4158-9b95-8d2df769e963
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: ht
source-wordcount: '496'
ht-degree: 100%

---

# Definición de la audiencia correcta {#define-the-right-audience}

La población objetivo es clave: cree sus listas con cuidado, pruebe sus correos electrónicos con clientes de correo electrónico y dispositivos móviles populares, y asegúrese de que sus listas de correos electrónicos estén actualizadas (sin direcciones desconocidas u obsoletas). También puede enviar pruebas que ayuden a configurar un ciclo de validación completo.

Aprenda más sobre las poblaciones objetivo [en esta sección](steps-defining-the-target-population.md)

## Selección de la audiencia de destino correcta {#target-the-right-audience}

Cuando tenga preparado el contenido, debe definir cuidadosamente quién recibirá el mensaje.

Para que su envío se realice correctamente, envíe el contenido personalizado más relevante a los destinatarios adecuados. Adobe Campaign le permite crear la población más adecuada: puede seleccionar destinatarios según su edad, ubicación, lo que compraron, si hicieron clic en un vínculo en un envío anterior, etc. Con Adobe Campaign, también puede definir perfiles, grupos de control y direcciones semilla de prueba para asegurarse de que el destinatario es correcto.

## Asignaciones de destino {#target-mappings}

En Campaign Classic, de forma predeterminada, las plantillas de envíos se dirigen a **Destinatarios**. Adobe Campaign ofrece otras asignaciones de destino para los envíos, que puede cambiar según sus necesidades.

Por ejemplo, puede enviar a visitantes cuyos perfiles se hayan recopilado a través de redes sociales o a visitantes suscritos a un servicio informativo.

Estas asignaciones se presentan [en esta sección](steps-defining-the-target-population.md#select-a-target-mapping).

También puede crear y utilizar una asignación de destino personalizada. Para obtener más información, consulte [esta sección](../../configuration/using/target-mapping.md).

## Destinatarios externos {#external-recipients}

Puede enviar a destinatarios que estén almacenados en un archivo externo en lugar de guardarlos en la base de datos. Obtenga más información [en esta sección](steps-defining-the-target-population.md#selecting-external-recipients).

## Envíos a suscriptores {#send-to-subscribers}

Para enviar mensajes a los suscriptores de una newsletter, puede enviar directamente a los destinatarios de los suscriptores al servicio informativo correspondiente. Obtenga más información [en esta sección](managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## Destinatarios y direcciones semilla de prueba {#test-recipients-seed-addresses}

Para probar el envío, utilice pruebas antes de enviar al destinatario principal.

Asegúrese de seleccionar los destinatarios de prueba adecuados, ya que validan el formulario y el contenido del mensaje. Los pasos para definir los destinatarios de prueba se presentan [en esta sección](steps-defining-the-target-population.md#selecting-the-proof-target).

Las direcciones semilla se utilizan para dirigirse a los destinatarios que no coinciden con los criterios de destino definidos para probar un envío antes de enviarlo al destinatario principal. Se muestran [en esta sección](about-seed-addresses.md).

## Deduplicación de direcciones {#deduplicate-addresses}

Es importante evitar tener direcciones de correo electrónico duplicadas, ya que esto puede perjudicar al destinatario:

* El mismo mensaje se puede enviar más de una vez cuando se divide un destinatario.

* Si un destinatario cancela la suscripción después de recibir un mensaje, su perfil duplicado seguirá recibiendo mensajes futuros.

Las direcciones duplicadas protegen su reputación de envío y garantizan una buena gestión de cuarentena.

**Temas relacionados:**

* [Actividad de anulación de duplicación](../../workflow/using/deduplication.md).
* [Caso de uso: Uso de la funcionalidad de combinación de la actividad de anulación de duplicación](../../workflow/using/deduplication-merge.md)

## Indexación de direcciones de correo electrónico {#index-addresses}

Para optimizar el rendimiento de las consultas SQL utilizadas en la aplicación, se puede declarar un índice a partir del elemento principal del esquema de datos.

Los pasos para agregar un índice a la dirección de correo electrónico se presentan [en esta sección](../../configuration/using/database-mapping.md#indexed-fields).
