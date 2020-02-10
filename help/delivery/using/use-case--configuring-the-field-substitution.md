---
title: '"Ejemplo de uso: Configuración de la sustitución de campos"'
seo-title: '"Ejemplo de uso: Configuración de la sustitución de campos"'
description: '"Ejemplo de uso: Configuración de la sustitución de campos"'
seo-description: null
page-status-flag: never-activated
uuid: 7f083dc6-e6d7-4eea-ac66-87674716515c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: a104fcab-75e6-4d73-bc3d-88570de6df7f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 003bac4c5d89290b9d3653d6ddfab7284b68642d

---


# Ejemplo de uso: Configuración de la sustitución de campos{#use-case-configuring-the-field-substitution}

La sustitución aleatoria de campos permite atribuir un valor de la lista de distribución a las direcciones sembradas que están vacías cuando el usuario utiliza este valor en un envío (por ejemplo: nombre, ciudad, etc.).

Esta sustitución le permite ahorrar tiempo al crear el envío: en lugar de añadir manualmente el valor deseado a las direcciones sembradas, la sustitución recupera aleatoriamente este valor en la lista de destinatarios del envío y la aplica a las direcciones sembradas.

## Contexto {#context}

En este ejemplo de uso, **My online library** quiere enviar un descuento a sus clientes en función de su género literario favorito.

El administrador del envío ha integrado un campo personalizado vinculado con el género favorito en su correo electrónico. Le gustaría utilizar algunas direcciones sembradas. Estas direcciones sembradas tienen el campo personalizado en su tabla, pero no tiene guardado ningún valor en él.

Para utilizar la sustitución de campos aleatoria debe tener:

* un envío con uno o varios campos personalizados,
* direcciones sembradas cuyo **esquema de datos** se modifique según los campos personalizados utilizados en el envío.

## Creación de envíos {#step-1---creating-a-delivery}

Los pasos para crear una entrega se detallan en la sección [Creación de una entrega](../../delivery/using/creating-an-email-delivery.md) por correo electrónico.

En este ejemplo, el administrador de envíos ha creado el boletín informativo.

![](assets/dlv_seeds_usecase_24.png)

## Edición del esquema de datos de las direcciones sembradas {#editing-the-seed-addresses-data-schema}

Las instrucciones para la modificación de un esquema de datos se detallan en la sección .

En este ejemplo, el esquema de datos de las direcciones sembradas toma un valor creado a partir del esquema de datos de los destinatarios:

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

Esta enumeración permite al usuario especificar el género literario favorito de sus clientes.

Para que esta modificación del esquema de datos pueda verse en el **formulario de entrada** de las direcciones sembradas, debe actualizarlo. Consulte la sección [Actualización del formulario](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md#updating-the-input-form) de entrada.

## Configuración de personalización {#configuring-personalization}

1. Abra un envío.

   En este ejemplo, el envío tiene dos campos personalizados: **el nombre** y el **género literario favorito** del destinatario.

   ![](assets/dlv_seeds_usecase_25.png)

1. Configure la lista de envío y las direcciones sembradas. Consulte [Identificación de poblaciones](../../delivery/using/steps-defining-the-target-population.md)objetivo.

   En este ejemplo, el usuario selecciona a los usuarios cuyo **género literario favorito** sea ciencia ficción como población objetivo principal.

   ![](assets/dlv_seeds_usecase_26.png)

   El usuario añade las direcciones sembradas al envío.

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >Para obtener más información sobre el **[!UICONTROL Edit the dynamic condition...]** vínculo, consulte Caso de [uso: seleccionar direcciones de raíz en los criterios](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

1. Click the **[!UICONTROL Preview]** tab then select a seed address to test the personalization.

   ![](assets/dlv_seeds_usecase_28.png)

   Se puede ver que uno de los campos personalizados está vacío. Ya que la dirección sembrada no tiene datos para este campo, la vista previa del contenido HTML no puede mostrar un valor.

   La sustitución aleatoria de campos se realiza **en el momento del envío**.

1. Haga clic en el botón **[!UICONTROL Send]**.
1. Analice su envío y **confirme el envío**.

   Las direcciones sembradas reciben el envío en la bandeja de entrada.

   La personalización de campos ha funcionado correctamente.

   ![](assets/dlv_seeds_usecase_08.png)
