---
product: campaign
title: Seguimiento anónimo
description: Obtenga información sobre cómo configurar el seguimiento anónimo
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 5%

---

# Seguimiento anónimo{#anonymous-tracking}

Adobe Campaign permite vincular la información de seguimiento web recopilada a un destinatario cuando este navega por el sitio de forma anónima. Cuando un usuario navega por las páginas etiquetadas de su sitio web, se recopila esta información de navegación, de modo que una vez que hace clic en un correo electrónico enviado por Adobe Campaign, se identifica y la información se vincula automáticamente a ellos.

>[!IMPORTANT]
>
>La configuración del seguimiento anónimo en un sitio web puede almacenar en déclencheur la recopilación de una cantidad significativa de registros de seguimiento y, por lo tanto, afectar al funcionamiento de la base de datos. Configúrelo con cuidado.\
>Los registros de seguimiento se guardan en la base de datos hasta que se purgan los datos de seguimiento. Utilice el asistente de implementación para configurar la frecuencia de depuración. Para obtener más información, consulte [esta sección](../../installation/using/deploying-an-instance.md#purging-data).

Para habilitar el seguimiento web anónimo en la instancia, se deben configurar los siguientes elementos:

* El **trackWebVisitors** parámetro del **redirección** elemento de la **serverConf.xml** el archivo del servidor de seguimiento debe establecerse en &#39;**true**&#39;, para colocar una cookie permanente (**uuid230**) en los navegadores de usuarios desconocidos de Internet que visitan el sitio.
* El **Seguimiento web anónimo** el modo debe estar seleccionado en la pantalla tracking configuration del asistente de implementación.

   ![](assets/webtracking_anonymous_set.png)

* Los formularios web se deben publicar y ejecutar en el servidor de seguimiento. La opción de coincidencia debe estar seleccionada en el asistente de implementación.

   ![](assets/webtracking_publication_set_for_webapps.png)
