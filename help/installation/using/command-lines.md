---
product: campaign
title: Líneas de comandos
description: Líneas de comandos
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
TQID: 'https://experienceleague.adobe.com/e85vFL0iZ586ICGGH1CP6fgqGU717W1aPDWqmj40-3s'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 4%
---
# Líneas de comandos{#command-lines}



Las siguientes líneas de comandos requieren la capacidad de acceder al servidor de aplicaciones. Para implementaciones alojadas en Adobe, estos comandos solo se pueden ejecutar en Adobe.

## Creación de una instancia {#creating-an-instance}

La creación de instancias se puede ejecutar mediante líneas de comandos con la sintaxis:

```sql
nlserver config -addinstance:instance/masques DNS[/lang]
```

(donde **eng** y **fra** son valores posibles para el parámetro `[lang]`)

El comando **nlserver config -addinstance:instance1/demo&#42;/eng** le permite crear una instancia llamada **instance1** en inglés con la máscara DNS demo&#42;.

## Declarar una base de datos {#declaring-a-database}

Puede asociar una base de datos existente con una instancia desde la línea de comandos mediante la siguiente sintaxis:

```sql
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Los siguientes valores son posibles para el parámetro **`[rdbms]`**:

* **postgresql**: para PostgreSQL,
* **oracle**: para Oracle,
* **mssql**: para Microsoft SQL Server,

El siguiente comando configura la instancia **demo** con el servidor de tipo SQL conocido como **base6**, vinculado a la cuenta **campaign** y su **contraseña** en el servidor **dbsrv**:

```sql
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
