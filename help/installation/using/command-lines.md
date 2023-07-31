---
product: campaign
title: Líneas de comandos
description: Líneas de comandos
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Solo se aplica a Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 4%

---

# Líneas de comandos{#command-lines}



Las siguientes líneas de comandos requieren la capacidad de acceder al servidor de aplicaciones. Para implementaciones alojadas por el Adobe, estos comandos solo se pueden ejecutar por el Adobe.

## Creación de una instancia {#creating-an-instance}

La creación de instancias se puede ejecutar mediante líneas de comandos con la sintaxis:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(donde **eng** y **fra** son valores posibles para `[lang]` parameter)

El comando **nlserver config -addinstance:instance1/demo&#42;/eng** permite crear una instancia de llamada **instance1** en inglés con la demostración de máscara DNS&#42;.

## Declarar una base de datos {#declaring-a-database}

Puede asociar una base de datos existente con una instancia desde la línea de comandos mediante la siguiente sintaxis:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Los siguientes valores son posibles para **`[rdbms]`** parámetro:

* **postgresql**: para PostgreSQL,
* **oracle**: para el Oracle,
* **mssql**: para Microsoft SQL Server,
* **DB2**: para el motor DB2.

El siguiente comando configura el **demostración** con el servidor de tipo SQL conocido como **base6**, vinculado a **campaña** cuenta y su **contraseña** en el **dbsrv** servidor:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
