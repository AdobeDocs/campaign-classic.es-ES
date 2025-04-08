---
product: campaign
title: Nuevas funciones basadas en GCM
description: Nuevas funciones basadas en GCM
feature: Technote
source-git-commit: b8a6a0db27826309456c285c08d4f1d85de70283
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 2%

---

# Funciones basadas en GCM {#new-functions}

Para mejorar la seguridad, hemos desaprobado el uso del algoritmo AES (Estándar de Cifrado Avanzado) con el modo CBC (Encadenamiento de Bloques Cifrados) para operaciones criptográficas. Se han introducido nuevas funciones de cifrado. Estas funciones utilizan AES con Galois/Modo contador (AES-GCM), lo que proporciona una alternativa más segura. Estas funciones están disponibles en JavaScript, JSP, API de SOAP y esquemas XML, lo que permite a los clientes realizar la transición de CBC a GCM para el cifrado y descifrado.

En esta documentación se enumeran las funciones de AES-GCM recién introducidas y las funciones basadas en CBC que están en desuso.

Nuevas funciones:

* [Función API EncryptString](#encryptString-api-xtk)
* [Función de API EncryptStringWithServerPassword](#EncryptStringWithServerPassword-api-xtk)
* [función cryptString de JavaScript](#encryptString-javascript)

Funciones heredadas que se pueden utilizar para GCM:

* [Función JavaScript DecryptString](#decryptString-javascript)
* [Función JavaScript DecryptPassword](#decryptPassword-javascript)

[Funciones obsoletas](#depracated-functions)

## Funciones de API

### EncryptString {#encryptString-api-xtk}

Codifica la cadena de caracteres con la clave de instancia mediante el algoritmo AES con modo GCM.

```
            String 
            encrypted = Encrypt (
            String       
            decrypted
            

      )
         
```

**Parámetros**: Texto descifrado

**Valores devueltos**: cifrados

**Esquema**: xtk:session

**Estático**: Sí

## EncryptStringWithServerPassword {#EncryptStringWithServerPassword-api-xtk}

Codifica la cadena de caracteres con la clave del servidor mediante el algoritmo AES con el modo GCM.


```
            String 
            encrypted = EncryptStringWithServerPassword (
            String       
            decrypted
            

      )
         
```

**Parámetros**: Descifrado

**Valores devueltos**: cifrados

**Esquema**: xtk:session

**Estático**: Sí

## Funciones de JavaScript

### encryptString() {#encryptString-javascript}

Codifica una cadena de caracteres con la clave de la instancia o con cualquier otra clave.

```
            cryptString (str [, key
      ] [, useSalt ])
         
```

**Parámetros**:

* str: Cadena de caracteres que se va a cifrar.
* clave: La clave de cifrado AES se codifica en base 64: 256 bits si la longitud de la clave es 32; 192 bits si la longitud de la clave es 24; 128 bits si la longitud de la clave es 16 o si no se especifica ninguna clave.
* useSalt: Utilice una sal de los datos para cifrar. True de forma predeterminada.

**Valor devuelto**: Devuelve la cadena de caracteres cifrada.

**Comentarios**

El cifrado se realiza según el método siguiente:

* La cadena de caracteres Unicode se transforma en una cadena UTF-8.
* Se agrega un carácter de verificación en el texto cifrado al final.
* Esta cadena se cifra utilizando el algoritmo AES en el modo Galois/Counter Mode (GCM) con una sal con un vector de inicialización de 12 bytes y una etiqueta de 16 bytes. Si no se proporciona ninguna clave como parámetro, se utiliza la clave de instancia.
* El texto cifrado contendrá la etiqueta y el vector de inicialización.
* El bloque cifrado se convierte en base 64.

El descifrado se realiza mediante la función decryptString.

**Funciones**

Disponible en:

* Gestión de contenido
* Propiedades de envío
* Envío del mensaje
* Regla de tipología
* Importación
* JSSP
* Método SOAP
* WebApp
* Flujo de trabajo

### decryptString() {#decryptString-javascript}

Codifica una cadena de caracteres con la clave de la instancia o con cualquier otra clave. Esta función heredada se puede utilizar con GCM. Está obsoleto para el descifrado de texto cifrado cifrado que se cifra mediante el modo AES-CBC.

```
            decryptString (str [, key
      ] [, useSalt ])
         
```

**Parámetros**:

* str: La cadena de caracteres que se va a descifrar.
* clave: La clave de cifrado AES se codifica en base 64: 256 bits si la longitud de la clave es 32; 192 bits si la longitud de la clave es 24; 128 bits si la longitud de la clave es 16 o si no se especifica ninguna clave.
* useSalt: Utilice una sal de los datos para descifrar. True de forma predeterminada.

**Valor devuelto**: Devuelve la cadena de caracteres descifrada.

**Advertencia**: las contraseñas almacenadas en la base de datos (opciones / cuentas externas) ya no se pueden descifrar con este método. Para ello, use [decryptPassword](#decryptPassword-javascript).

### decryptPassword() {#decryptPassword-javascript}

Descifra una contraseña almacenada en una cuenta externa. Esta función heredada se puede utilizar con GCM. Está obsoleto para el descifrado de texto cifrado cifrado que se cifra mediante el modo AES-CBC.

```
            decryptPassword (str)
         
```

**Parámetros**:

* str: La cadena de caracteres que se va a descifrar.

**Valor devuelto**: Devuelve la contraseña de texto sin formato.

**Comentarios**

Esta función no se puede invocar en flujos de trabajo, aplicaciones web, informes o envíos. Se puede llamar en implementaciones de llamadas JSSP o SOAP. Ejemplo:

```
        function nms_extAccount_LogonToRemoteInstance(remoteInstanceUrl, login, encryptedPassword) {
        var cnx = null, sessionService = null;
        try
            {
                var cnx = new HttpSoapConnection(remoteInstanceUrl + '/nl/jsp/soaprouter.jsp', 'utf-8', 0);
                sessionService = new SoapService(cnx, 'xtk:session');
                sessionService.addMethod("Logon", "xtk:session#Logon",
                    ["token", "string", "login", "string", "password", "string", "parameters", "NLElement"],
                    ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
                return sessionService.Logon("", login, decryptPassword(encryptedPassword), <parameters/>);
            }
        catch( e ) {
        logError(e);
        }
        finally {
        if( sessionService ) sessionService.dispose();
        if( cnx ) cnx.dispose();
        }
        })
      
```

## Funciones obsoletas {#depracated-functions}

Las siguientes funciones están totalmente obsoletas:

* cryptString
* Cifrar
* EncryptServerPassword
