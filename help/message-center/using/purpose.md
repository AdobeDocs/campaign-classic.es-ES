---
title: Objetivo
seo-title: Objetivo
description: Objetivo
seo-description: null
page-status-flag: never-activated
uuid: 4452d839-318a-49d8-8abb-4ba04c803e9f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: 7b8ab9d6-e47e-46d8-99df-da793486654c
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Objetivo{#purpose}

El propósito de este caso de uso es añadir archivos adjuntos de los correos electrónicos sobre la marcha a las entregas salientes.

En este escenario, veremos cómo enviar correos electrónicos de transacciones con archivos adjuntos individuales o personalizados. Los archivos adjuntos no se precargan en el servidor de mensajería transaccional sino que se generan sobre la marcha.

Al capturar las interacciones o los detalles del cliente, es posible que necesite volver a enviar esta información al cliente al final del proceso, por ejemplo, en un archivo PDF adjunto a un correo electrónico. Aquí se describen los pasos generales de este escenario.

1. El cliente introduce el sitio web y busca el producto que desea comprar.
1. El cliente selecciona el producto y personaliza algunas opciones.
1. El cliente completa la transacción.
1. Se envía un correo electrónico al cliente que confirma la transacción. No se desea enviar PII (información de identificación personal) por correo electrónico, por lo que se genera un PDF seguro y se adjunta al correo electrónico.
1. El cliente recibe el correo electrónico y el adjunto que contiene todos los datos necesarios.

En este caso, los archivos adjuntos no se generan previamente sino que se añaden sobre la marcha a los correos electrónicos salientes. Esto también permite personalizar el contenido del archivo adjunto. Asimismo, si el archivo adjunto está asociado a una transacción (como en el ejemplo anterior), puede que necesite que contenga los datos dinámicos que se generan durante el proceso de cliente. La incorporación de archivos PDF de este modo optimiza también la seguridad a medida que se pueden cifrar y se envían por HTTPS.
