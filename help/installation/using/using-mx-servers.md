---
product: campaign
title: Uso de servidores MX con Campaign
description: Descubra cómo funcionan los servidores MX con Adobe Campaign Classic
feature: Installation, Instance Settings
badge-v7-prem: label="On-Premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 3%

---

# Uso de servidores MX con Campaign {#using-mx-servers}



Descubra cómo funcionan los servidores MX con Adobe Campaign Classic.

## Servidores MX {#mx-servers}

### Qué es un servidor MX?

Un registro de intercambio de correo (registro MX) es un tipo de registro de recursos del Sistema de nombres de dominio (DNS) que especifica un servidor de correo responsable de aceptar mensajes de correo electrónico en nombre de un dominio.

### ¿Cómo funciona un servidor MX?

Cuando envía un correo electrónico, el servidor de software establece una conexión con el servidor de dominio del destinatario. La comunicación entre los dos servidores utiliza el idioma SMTP y un dominio puede tener más de un servidor MX. La conexión a este dominio comenzará desde la prioridad más alta (cifra más pequeña) y otros servidores se denominan servidores de &quot;copia de seguridad&quot;. Se debe respetar el protocolo de conexión.

### ¿Cómo funciona un servidor MX con Adobe Campaign?

En el protocolo de conexión, deben respetarse las reglas para evitar el spam y el monopolio de los servidores. Los más importantes son los siguientes:

* **Número máximo de conexiones permitidas**: Cuando se respeta este número, las direcciones IP no están en la lista de bloqueados de la y los correos electrónicos no se rechazan debido a conexiones adicionales.
* **Número máximo de mensajes**: Durante la conexión, se debe definir el número de mensajes que se pueden enviar. Si no se define este número, el servidor enviará tantos como sea posible. Esto hace que se identifique como correo no deseado y el ISP lo añada a la lista de bloqueados de la.
* **Mensajes por hora**: Para que coincida con su reputación de correo electrónico, Adobe Campaign controlará el número de correos electrónicos que sus IP pueden enviar por hora. Este sistema le protegerá contra la denegación o/y la lista de bloqueados de correo electrónico por parte del usuario.

## Correos electrónicos entrantes

### ¿Qué es un correo electrónico de entrada?

Es el proceso que utiliza Adobe Campaign para procesar errores durante las comunicaciones con el servidor.

### ¿Cómo funciona un correo electrónico de entrada?

La dirección de error procesará las devoluciones enviadas por los ISP. El proceso analizará diferentes códigos de error SMTP y aplicará la acción correcta según el estándar de RegEx.

Por ejemplo, una dirección de correo electrónico tiene un comentario &quot;550 Usuario desconocido&quot; enviado por un ISP. Este código de error lo procesa la dirección de error de Adobe Campaign (dirección de la ruta de retorno). Este error se compara con el estándar de RegEx y se aplica la regla correcta. El correo electrónico se considera un *Rechazo duro* (que coincida con el tipo ) y, a continuación, *Usuario desconocido* (que coincida con el motivo) y se envía a cuarentena después del primer bucle en el sistema.

### ¿Cómo lo gestiona Adobe Campaign?

Adobe Campaign administra este proceso con una coincidencia entre un tipo de error y un motivo:

* **[!UICONTROL User Unknown]**: Dirección que es sintácticamente correcta, pero no existe. Este error se clasifica como una devolución grave y se envía a cuarentena dentro del primer error.
* **[!UICONTROL Mailbox full]**: Buzón que ha alcanzado la capacidad máxima. Este error también puede indicar que el usuario ya no está usando este buzón. Este error se clasifica como una devolución suave y se envía a cuarentena dentro del tercer error y se elimina de la cuarentena después de un periodo de 30 días.
* **[!UICONTROL Inactive User]**: el ISP ha desactivado el buzón debido a un usuario inactivo en los últimos 6 meses. Este error se clasifica como una devolución suave y se envía a cuarentena dentro del tercer error.
* **[!UICONTROL Invalid domain]**: el dominio de la dirección de correo electrónico no existe. Este error se clasifica como una devolución suave y se envía a cuarentena dentro del tercer error.
* **[!UICONTROL Refused]**: el ISP se negó a entregar el correo electrónico a sus usuarios. Este error se clasifica como una devolución suave y no se envía a cuarentena, ya que el error no está vinculado a la dirección de correo electrónico, sino a la IP o a una reputación de dominio.

>[!NOTE]
>
>Para obtener más información sobre los tipos y motivos de los errores de entrega, consulte esta sección [sección](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

## Instancia de entrega {#deliveratbility-env}

Una actualización diaria de las reglas MX y las reglas de devoluciones se administran mediante un flujo de trabajo específico en la instancia del cliente que está conectada al propietario de la instancia de entrega de estas reglas.

Esta actualización diaria se está ejecutando para todos los clientes que desean mantener su instancia actualizada a través de un proceso de transparencia.

Las reglas MX tienen 6 niveles diferentes de rendimiento que se utilizan principalmente durante el proceso de aceleración:

![](assets/mx-rules-throughput.png)

El modo personalizado es para clientes avanzados que desean establecer sus propias reglas MX. Cuando se activa el modo personalizado, la instancia de Deliverability no actualiza el cliente, ya que la sincronización se desactiva.

## Ejemplos de rechazos

* **Usuario desconocido** (mensajes devueltos no válidos): 550 5.1.1 ... Usuario desconocido {mx003}
* **Buzón lleno** (rebote suave): 550 5.2.2 Se ha superado la cuota de usuario
* **Buzón inactivo** (rebote suave): 550 5.7.1 : Dirección del destinatario rechazada: buzón inactivo, no reaparecido durante más de 6 meses
* **Dominio no válido** (devolución suave): Error de consulta DNS para &#39;ourdan.com&#39;
* **Rechazado** (devolución suave): La devolución del correo electrónico entrante (regla &#39;Feedback_loop_Hotmail&#39; ha coincidido con esta devolución)
* **Inaccesible** (rebote suave): 421 4.16.55 [TS01] Mensajes de x.x.x.x diferidos temporalmente debido a quejas excesivas del usuario

**Temas relacionados:**
* [Configuración MX](../../installation/using/email-deliverability.md#mx-configuration)
* [Configuración técnica de correo electrónico](../../installation/using/email-deliverability.md)
* [Comprensión de los errores de entrega](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic - Recommendations técnico](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html)
