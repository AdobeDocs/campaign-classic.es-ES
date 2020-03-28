---
title: Administración de direcciones semilla en mensajes transaccionales
seo-title: Administración de direcciones semilla en mensajes transaccionales
description: Administración de direcciones semilla en mensajes transaccionales
seo-description: null
page-status-flag: never-activated
uuid: 51c4e79d-53bb-4d46-9c7d-e90066f5317d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 12e7043e-e8b5-48a9-8a2f-99e2e6040c3c
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Administración de direcciones semilla en mensajes transaccionales{#managing-seed-addresses-in-transactional-messages}

Una dirección semilla permite mostrar una vista previa del mensaje, enviar una prueba y probar la personalización del mensaje antes de enviarlo por correo electrónico o SMS. Las direcciones semilla están vinculadas a la entrega y no se pueden utilizar para otros envíos.

## Creación de una dirección semilla {#creating-a-seed-address}

1. En la plantilla de mensaje transaccional, haga clic en la pestaña **[!UICONTROL Dirección de semilla]**.

   ![](assets/messagecenter_create_seedaddr_001.png)

1. Asigne una etiqueta para facilitar la selección posterior.

   ![](assets/messagecenter_create_seedaddr_002.png)

1. Introduzca la dirección semilla (correo electrónico o teléfono móvil en función del canal de comunicación).

   ![](assets/messagecenter_create_seedaddr_003.png)

1. Introduzca el identificador externo: este campo opcional permite introducir una clave comercial (ID única, nombre + correo electrónico, etc.) que es común a todas las aplicaciones del sitio web y es utilizada para identificar los perfiles. Si este campo también está presente en la base de datos de marketing de Adobe Campaign, puede conciliar un evento con un perfil de la base de datos.

   ![](assets/messagecenter_create_seedaddr_003bis.png)

1. Inserte datos de prueba (consulte [Datos de personalización](../../message-center/using/personalization-data.md)).

   ![](assets/messagecenter_create_custo_001.png)

## Creación de varias direcciones semilla {#creating-several-seed-addresses}

1. Haga clic en el vínculo **[!UICONTROL Añadir otras direcciones semilla]** y, a continuación, en el botón **[!UICONTROL Añadir]**.

   ![](assets/messagecenter_create_seedaddr_004.png)

1. Siga los pasos de configuración para una dirección semilla detallados en la sección [Crear una dirección semilla](#creating-a-seed-address).
1. Repita el proceso para crear todas las direcciones que sean necesarias.

   ![](assets/messagecenter_create_seedaddr_008.png)

Una vez creadas las direcciones, puede mostrar su vista previa y personalización. Consulte [Vista previa de mensajes transaccionales](../../message-center/using/transactional-message-preview.md).
