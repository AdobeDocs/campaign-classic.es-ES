---
product: campaign
title: Definir etiqueta de seguimiento web
description: Definir etiqueta de seguimiento web
feature: Application Settings
role: Developer
exl-id: 0b5575be-57e7-4eee-9c0a-e9ef4b0931bf
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 2%

---

# Etiqueta de seguimiento web: definición{#web-tracking-tag-definition}



Una etiqueta de seguimiento web no es más que una URL construida con los parámetros adecuados y enviada al servidor de redirección a través de una consulta HTTP.

## Formato de los datos que se van a enviar {#format-of-the-data-to-be-sent}

El formato de una URL de seguimiento web es el siguiente: **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>El número aleatorio añadido a la URL evita los problemas causados por los navegadores que almacenan las páginas web en caché.

La siguiente tabla proporciona una lista de parámetros especiales admitidos por el servidor de redirección.

<table>
                     <thead>
                        <tr>
                           <th>Nombre</th>
                           <th>Tipo</th>
                           <th>Descripción</th> 
                        </tr> 
                     </thead>
                     <tbody>
                        <tr>
                           <td>
                              <p>Identidad</p> 
                           </td>
                           <td>
                              <p>Cookie de sesión</p> 
                           </td>
                           <td>
                              <p>Identificador de envío e identificador de destinatario.</p> 
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
                              <p>Identificador de destinatario (útil si falta la cookie de sesión).</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>tagid</p> 
                           </td>
                           <td>
                              <p>URL Parameter</p> 
                           </td>
                           <td>
                              <p>Identificador de la página web rastreada: este es el único parámetro obligatorio.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>trabajadora</p> 
                           </td>
                           <td>
                              <p>URL Parameter</p> 
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
                              <p>URL Parameter</p> 
                           </td>
                           <td>
                              <p>Parámetro utilizado para identificar al usuario de Internet. El formato de este parámetro es "nombre=valor",
                                 donde name es un campo del esquema recipient. Este parámetro tiene prioridad sobre
                                 el identificador contenido en la cookie de sesión.
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**Algunas URL de seguimiento web**

* Visita a una página de identificador &quot;principal&quot;

  **https://myserver.adobe.com/r/9862?tagid=home**

* Recopilación de datos de volumen empresarial

  **https://myserver.adobe.com/r/4567?tagid=command&amount=100&article=2l**

* Especificación de un campo para buscar el destinatario

  **https://myserver.adobe.com/r/2353?tagid=home&rcpid=saccount%3D10**

  Se envía a la página de inicio un destinatario cuyo número de cuenta sea 10.

* Uso de una entrega predeterminada

  **https://myserver.adobe.com/r/2456?tagid=home&jobid=e6**

  Se envía un destinatario a la página principal. Esta información se almacena en la entrega con el identificador 230 (e6 en la base de datos 16) a menos que se envíe con esta consulta una cookie de sesión que contenga un identificador de entrega.

>[!NOTE]
>
>Todos los valores enviados al servidor de redirección mediante parámetros de URL deben codificarse con URL. En los ejemplos dados, tenga en cuenta que los caracteres &#39;=&#39; y &#39;|&#39; están codificados como &#39;%3D&#39; y &#39;%7C&#39; respectivamente.

## Métodos de transmisión de datos {#data-transmission-methods}

Los siguientes métodos son posibles:

* Insertando la dirección URL en el atributo **&quot;src&quot;** de una etiqueta HTML **`<img>`** incorporada en la página web que desea rastrear.
* Llamada directa al servidor de redirección cuando se genera la página web que desea rastrear.
