---
title: Gestión de datos SQL
seo-title: Gestión de datos SQL
description: Gestión de datos SQL
seo-description: null
page-status-flag: never-activated
uuid: b6057496-2dd5-4289-96df-98378e4f0ae7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 18d6f5e1-308f-4080-b7c4-ebf836f74842
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Gestión de datos SQL{#sql-data-management}

La actividad de **SQL Data Management** permite escribir sus propios scripts SQL para crear y rellenar tablas de trabajo.

## Requisitos previos {#prerequisites}

Antes de configurar la actividad, asegúrese de que se cumplan los siguientes requisitos previos:

* La actividad solo está disponible para fuentes de datos remotos. The **[!UICONTROL FDA]** (Federated Data Access) package must therefore be installed on your instance (see [this section](../../platform/using/accessing-an-external-database.md)).
* El esquema saliente debe existir en la base de datos y estar vinculado a una base de datos FDA (para más información sobre esquemas de datos, consulte [esta sección](../../configuration/using/about-schema-reference.md)).
* The operator executing the workflow must have the **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]** named right. Para obtener más información sobre derechos asignados, consulte [esta sección](../../platform/using/access-management.md#named-rights).

## Configuración de la actividad de gestión de datos SQL {#configuring-the-sql-data-management-activity}

1. Specify the activity **[!UICONTROL Label]**.
1. Select the **[!UICONTROL External account]** to use, then select the **[!UICONTROL Outbound schema]** linked to this external account.

   >[!CAUTION]
   >
   >El esquema saliente es fijo y no se puede editar.

1. Agregue el script SQL.

   >[!CAUTION]
   >
   >Es responsabilidad del escritor del script de SQL asegurarse de que el script SQL funcione y que sus referencias (nombres de campos, etc.) estén en conformidad con el esquema saliente.

   Si desea cargar un código SQL existente, seleccione la **[!UICONTROL The SQL script is contained in an entity stored in the database]** opción. Las secuencias de comandos SQL deben crearse y almacenarse en el menú **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]** .

   De lo contrario, escriba o copie y pegue el script SQL en el área dedicada.

   ![](assets/sql_datamanagement.png)

   La actividad permite utilizar las siguientes variables en el script:

   * **activity.tableName**: Nombre SQL de la tabla de trabajo saliente.
   * **task.importingTransitionByName(‘name’).tableName**: Nombre SQL de la tabla de trabajo que lleva la transición entrante para utilizar (la transición se identifica por su nombre).

      >[!NOTE]
      >
      >The (&#39;name&#39;) value corresponds to the **[!UICONTROL Name]** field from the transition properties.

1. If the SQL script already contains commands to create an outbound work table, unselect the **[!UICONTROL Automatically create work table]** option. De lo contrario, se crea una tabla de trabajo una vez que se ejecute el flujo de trabajo.
1. Click **[!UICONTROL Ok]** to confirm the activity configuration.

La actividad está configurada. Está listo para ejecutarse en el flujo de trabajo.

>[!CAUTION]
>
>Una vez que se ejecuta la actividad, la transición de salida registra solo el recuento. Puede variar según el nivel de complejidad de la secuencia de comandos SQL.
>  
>Si se reinicia la actividad, se ejecuta todo el script desde el principio, independientemente del estado de ejecución.

## Ejemplos de script SQL:{#sql-script-samples}

>[!NOTE]
>
>Los ejemplos de script de esta sección están pensados para ejecutarse en PostgreSQL.

El siguiente script permite crear una tabla de trabajo e insertar datos en esta misma tabla de trabajo:

```
CREATE UNLOGGED TABLE <%= activity.tableName %> (
  iRecipientId INTEGER DEFAULT 0,
  sFirstName VARCHAR(100),
  sMiddleName VARCHAR(100),
  sLastName VARCHAR(100),
  sEmail VARCHAR(100)
);

INSERT INTO <%= activity.tableName %>
SELECT iRecipientId, sFirstName, sMiddleName, sLastName, sEmail
FROM nmsRecipient
GROUP BY iRecipientId, sFirstName, sMiddleName, sLastName, sEmail;
```

El siguiente script permite realizar una operación CTAS (CREATE TABLE AS SELECT) y crear un índice de tabla de trabajo:

```
CREATE TABLE <%= activity.tableName %>
AS SELECT iRecipientId, sEmail, sFirstName, sLastName, sMiddleName
FROM nmsRecipient
WHERE sEmail IS NOT NULL
GROUP BY iRecipientId, sEmail, sFirstName, sLastName, sMiddleName;

CREATE INDEX ON <%= activity.tableName %> (sEmail);

ANALYZE <%= activity.tableName %> (sEmail);
```

El siguiente script permite combinar dos tablas de trabajo:

```
CREATE TABLE <%= activity.tableName %>
AS SELECT i1.sFirstName, i1.sLastName, i2.sEmail
FROM <%= task.incomingTransitionByName('input1').tableName %> i1
JOIN <%= task.incomingTransitionByName('input2').tableName %> i2 ON (i1.id = i2.id)
```

