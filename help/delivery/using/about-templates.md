---
product: campaign
title: Acerca de las plantillas
description: Introducción a las plantillas de entrega
feature: Delivery Templates
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: ht
source-wordcount: '276'
ht-degree: 100%

---

# Acerca de las plantillas{#about-templates}

![](../../assets/common.svg)

Puede guardar una configuración de envío en una plantilla de envío para reutilizarla más tarde. La plantilla puede incluir una configuración completa o parcial de la entrega.

La plantilla de envío se puede ejecutar manualmente, tal y como se describe en este capítulo, o según un evento concreto (que se inicie a una hora determinada, cuando un archivo llegue a un servidor, etc.). Puede configurar las plantillas de envío desde el nodo **[!UICONTROL Resources > Templates > Delivery templates]** del árbol.

![](assets/s_user_template_list.png)

Hay dos tipos de plantillas:

1. Plantillas de envío nativas de Adobe Campaign

   Las plantillas nativas NO DEBEN eliminarse del sistema. Incluyen una configuración mínima para cada canal de envío. Sin embargo, el administrador puede restringir determinadas funciones u ofrecer valores predeterminados a los usuarios (seguimiento de la activación, direcciones de correo electrónico del remitente, etc.). Los escenarios nativos aparecen en negrita en la lista de las plantillas. Para poder modificarlos, es necesario duplicarlos.

1. Plantillas de envío predeterminadas

   El administrador de Adobe Campaign puede crear nuevas plantillas de envío. Pueden reutilizarlas los operadores (los que tengan los derechos de acceso correspondientes) o, de forma automática, los procesos del servidor. Por ejemplo, puede configurar una plantilla de envíos por correo electrónico. Cuando el usuario cree un envío con esta plantilla, este solo debe introducir el texto o el contenido HTML y, a continuación, enviarlo; el administrador ya ha definido el resto de las opciones.

>[!NOTE]
>
>Las plantillas disponibles dependen de los derechos de acceso, de la configuración de la instancia y del contexto. Por ejemplo, al crear un servicio informativo, puede vincular una plantilla de envío a los mensajes de confirmación: así solo puede acceder a las plantillas cuyo destino de mapeo sea la asignación de suscripción. Para obtener más información sobre esto, consulte [Selección de una asignación de destino](selecting-a-target-mapping.md) y [Servicios y suscripciones](about-services-and-subscriptions.md).
