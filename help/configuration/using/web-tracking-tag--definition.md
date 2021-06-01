---
product: campaign
title: '"Etiqueta de seguimiento web: definición"'
description: '"Etiqueta de seguimiento web: definición"'
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: 0b5575be-57e7-4eee-9c0a-e9ef4b0931bf
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 4%

---

# Etiqueta de seguimiento web: definición{#web-tracking-tag-definition}

Una etiqueta de seguimiento web es simplemente una URL construida con los parámetros apropiados, enviada al servidor de redirección a través de una consulta HTTP.

## Formato de los datos a enviar {#format-of-the-data-to-be-sent}

El formato de una URL de seguimiento web es el siguiente: **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>El número aleatorio añadido a la dirección URL evita problemas causados por el almacenamiento en caché de las páginas web de los exploradores.

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
                              <p>Identificador de destinatario (útil si no hay cookie de sesión).</p> 
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
                              <p>Identificador de envío que se utilizará si no hay ninguna cookie de sesión. Este valor debe ser
                                 expresado en hexadecimal.
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
                              <p>Parámetro utilizado para identificar al usuario de Internet. El formato de este parámetro es "name=value",
                                 donde el nombre es un campo del esquema de destinatario. Este parámetro tiene prioridad sobre
                                 el identificador contenido en la cookie de sesión.
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**Algunas URL de seguimiento web**

* Visita a una página de identificador &quot;principal&quot;

   **https://myserver.adobe.com/r/9862?tagid=home**

* Recopilación de datos del volumen del negocio

   **https://myserver.adobe.com/r/4567?tagid=command&amp;amount=100&amp;article=2l**

* Especificación de un campo para encontrar el destinatario

   **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

   Se envía a la página principal un destinatario cuyo número de cuenta sea 10.

* Uso de una entrega predeterminado

   **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

   Se envía un destinatario a la página principal. Esta información se almacena en el envío con el identificador 230 (e6 en la base de datos 16) a menos que se envíe una cookie de sesión que contenga un identificador de envío con esta consulta.

>[!NOTE]
>
>Todos los valores enviados al servidor de redirección mediante parámetros de URL deben codificarse con URL. En los ejemplos dados, tenga en cuenta que los caracteres &#39;=&#39; y &#39;|&#39; están codificados como &#39;%3D&#39; y &#39;%7C&#39; respectivamente.

## Métodos de transmisión de datos {#data-transmission-methods}

Los siguientes métodos son posibles:

* Inserción de la URL en el atributo **&quot;src&quot;** de una etiqueta HTML **`<img>`** incorporada en la página web que desea rastrear.
* Llamada directa al servidor de redirección cuando se genera la página web que desea rastrear.
