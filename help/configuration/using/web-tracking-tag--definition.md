---
title: '"Etiqueta de seguimiento web: definition"'
seo-title: '"Etiqueta de seguimiento web: definition"'
description: '"Etiqueta de seguimiento web: definition"'
seo-description: null
page-status-flag: never-activated
uuid: 915ddfd8-ad1b-41ac-96ed-f7fae687c09f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: b8996508-7173-4225-95e7-b51209aae1f1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3ad288bc983002da82b564e8ab3f4244c6324573

---


# Etiqueta de seguimiento web: definición{#web-tracking-tag-definition}

Una etiqueta de seguimiento web es simplemente una dirección URL construida con los parámetros adecuados, que se envía al servidor de redirección mediante una consulta HTTP.

## Formato de los datos que se enviarán {#format-of-the-data-to-be-sent}

El formato de una URL de seguimiento web es el siguiente: **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>El número aleatorio agregado a la dirección URL evita los problemas causados por los navegadores que almacenan en caché páginas web.

La siguiente tabla proporciona una lista de parámetros especiales admitidos por el servidor de redirección.

<table>
                     <thead>
                        <tr>
                           <th>Name</th>
                           <th>Tipo</th>
                           <th>Descripción</th> 
                        </tr> 
                     </thead>
                     <tbody>
                        <tr>
                           <td>
                              <p>ID</p> 
                           </td>
                           <td>
                              <p>Cookie de sesión</p> 
                           </td>
                           <td>
                              <p>Identificador de entrega e identificador de destinatario.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>uuid230</p> 
                           </td>
                           <td>
                              <p>Cookie permanente</p> 
                           </td>
                           <td>
                              <p>Identificador del destinatario (útil si la cookie de sesión no está presente).</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>tagid</p> 
                           </td>
                           <td>
                              <p>Parámetro de URL</p> 
                           </td>
                           <td>
                              <p>Identificador de la página web rastreada: este es el único parámetro obligatorio.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>jobid</p> 
                           </td>
                           <td>
                              <p>Parámetro de URL</p> 
                           </td>
                           <td>
                              <p>Identificador de entrega que se utilizará si no hay una cookie de sesión. Este valor se expresa en hexadecimal.
                              </p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>rcpid</p> 
                           </td>
                           <td>
                              <p>Parámetro de URL</p> 
                           </td>
                           <td>
                              <p>Parámetro utilizado para identificar al usuario de Internet. El formato de este parámetro es "name=value", donde el nombre es un campo del esquema del destinatario. Este parámetro tiene prioridad sobre el identificador contenido en la cookie de sesión.
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**Algunas direcciones URL de seguimiento web**

* Visita a una página de identificador &#39;principal&#39;

   **https://myserver.adobe.com/r/9862?tagid=home**

* Recopilación de datos del volumen del negocio

   **https://myserver.adobe.com/r/4567?tagid=command&amp;amount=100&amp;article=2l**

* Especificación de un campo para encontrar el destinatario

   **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

   Un destinatario cuyo número de cuenta sea 10 se envía a la página principal.

* Uso de una entrega predeterminada

   **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

   Se envía un destinatario a la página principal. Esta información se almacenará en la entrega con el identificador 230 (e6 en la base de datos 16) a menos que se envíe una cookie de sesión que contenga un identificador de entrega con esta consulta.

>[!NOTE]
>
>Todos los valores enviados al servidor de redirección mediante parámetros de URL deben tener codificación de URL. En los ejemplos dados, tenga en cuenta que los caracteres &#39;=&#39; y &#39;|&#39; están codificados como &#39;%3D&#39; y &#39;%7C&#39; respectivamente.

## Métodos de transmisión de datos {#data-transmission-methods}

Los siguientes métodos son posibles:

* Inserción de la URL en el atributo **&quot;src&quot;** de una **`<img>`** etiqueta HTML incorporada en la página web que desea rastrear.
* Llamada directa al servidor de redirección cuando se genera la página web que desea rastrear.

