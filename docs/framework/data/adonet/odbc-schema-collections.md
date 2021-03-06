---
title: "Коллекции схемы ODBC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 889e84db39af1257d709ef049e18d4397ea700d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="odbc-schema-collections"></a>Коллекции схемы ODBC
В данном разделе рассматривается поддержка коллекций схем для драйверов ODBC для Microsoft SQL Server, Oracle и Microsoft Jet.  
  
## <a name="microsoft-sql-server-odbc-driver"></a>Драйвер ODBC для Microsoft SQL Server  
 Драйвер ODBC для Microsoft SQL Server поддерживает следующие специальные коллекции схем в дополнение к общим коллекциям схем.  
  
-   Таблицы  
  
-   Indexes  
  
-   Столбцы  
  
-   Процедуры  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Представления  
  
### <a name="tables-and-views"></a>Tables и Views  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CAT|Строковое|  
|TABLE_SCHEM|Строковое|  
|TABLE_NAME|Строковое|  
|TABLE_TYPE|Строковое|  
|REMARKS|Строковое|  
  
### <a name="indexes"></a>Indexes  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CAT|Строковое|  
|TABLE_SCHEM|Строковое|  
|TABLE_NAME|Строковое|  
|NON_UNIQUE|Int16|  
|INDEX_QUALIFIER|Строковое|  
|INDEX_NAME|Строковое|  
|TYPE|Int16|  
|ORDINAL_POSITION|Int16|  
|COLUMN_NAME|Строковое|  
|ASC_OR_DESC|Строковое|  
|CARDINATLITY|Int32|  
|PAGES|Int32|  
|FILTER_CONDITION|Строковое|  
|SS_TYPE_SCHEMA|Строковое|  
|SS_DATA_TYPE|Byte|  
  
### <a name="columns"></a>Столбцы  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CAT|Строковое|  
|TABLE_SCHEM|Строковое|  
|TABLE_NAME|Строковое|  
|COLUMN_NAME|Строковое|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Строковое|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Строковое|  
|COLUMN_DEF|Строковое|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|Строковое|  
|SS_TYPE_CATALOG|Строковое|  
|SS_TYPE_SCHEMA|Строковое|  
|SS_DATA_TYPE|Byte|  
  
### <a name="procedures"></a>Процедуры  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CAT|Строковое|  
|PROCEDURE_SCHEM|Строковое|  
|PROCEDURE_NAME|Строковое|  
|NUM_INPUT_PARAMS|Int32|  
|NUM_OUTPUT_PARAMS|Int32|  
|NUM_RESULT_SETS|Int32|  
|REMARKS|Строковое|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CAT|Строковое|  
|PROCEDURE_SCHEM|Строковое|  
|PROCEDURE_NAME|Строковое|  
|COLUMN_NAME|Строковое|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Строковое|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Строковое|  
|COLUMN_DEF|Строковое|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|Строковое|  
|SS_TYPE_CATALOG|Строковое|  
|SS_TYPE_SCHEMA|Строковое|  
|SS_DATA_TYPE|Byte|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CAT|Строковое|  
|PROCEDURE_SCHEM|Строковое|  
|PROCEDURE_NAME|Строковое|  
|COLUMN_NAME|Строковое|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Строковое|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Строковое|  
|COLUMN_DEF|Строковое|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|Строковое|  
|SS_TYPE_CATALOG|Строковое|  
|SS_TYPE_SCHEMA|Строковое|  
|SS_DATA_TYPE|Byte|  
  
## <a name="microsoft-oracle-odbc-driver"></a>Драйвер ODBC для Oracle (Майкрософт)  
 Microsoft SQL Server драйвер ODBC для Oracle поддерживает следующие специальные коллекции схем в дополнение к общим коллекциям схем.  
  
-   Таблицы  
  
-   Столбцы  
  
-   Процедуры  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Представления  
  
-   Indexes  
  
### <a name="tables-and-views"></a>Tables и Views  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_QUALIFIER|Строковое|  
|TABLE_OWNER|Строковое|  
|TABLE_NAME|Строковое|  
|TABLE_TYPE|Строковое|  
|REMARKS|Строковое|  
  
### <a name="columns"></a>Столбцы  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_QUALIFIER|Строковое|  
|TABLE_OWNER|Строковое|  
|TABLE_NAME|Строковое|  
|COLUMN_NAME|Строковое|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Строковое|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Строковое|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedures"></a>Процедуры  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|Строковое|  
|PROCEDURE_OWNER|Строковое|  
|PROCEDURE_NAME|Строковое|  
|NUM_INPUT_PARAMS|Int16|  
|NUM_OUTPUT_PARAMS|Int16|  
|NUM_RESULT_SETS|Int16|  
|REMARKS|Строковое|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|Строковое|  
|PROCEDURE_OWNER|Строковое|  
|PROCEDURE_NAME|Строковое|  
|COLUMN_NAME|Строковое|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Строковое|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Строковое|  
|OVERLOAD|Int32|  
|ORDINAL_POSITION|Int32|  
  
## <a name="microsoft-jet-odbc-driver"></a>Драйвер ODBC для Jet (Майкрософт)  
 Драйвер ODBC для Jet (Майкрософт) поддерживает следующие специальные коллекции схем в дополнение к общим коллекциям.  
  
-   Таблицы  
  
-   Indexes  
  
-   Столбцы  
  
-   Процедуры  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Представления  
  
### <a name="tables-and-views"></a>Tables и Views  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_QUALIFIER|Строковое|  
|TABLE_OWNER|Строковое|  
|TABLE_NAME|Строковое|  
|TABLE_TYPE|Строковое|  
|REMARKS|Строковое|  
  
### <a name="columns"></a>Столбцы  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_QUALIFIER|Строковое|  
|TABLE_OWNER|Строковое|  
|TABLE_NAME|Строковое|  
|COLUMN_NAME|Строковое|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Строковое|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Строковое|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedures"></a>Процедуры  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|Строковое|  
|PROCEDURE_OWNER|Строковое|  
|PROCEDURE_NAME|Строковое|  
|NUM_INPUT_PARAMS|Int16|  
|NUM_OUTPUT_PARAMS|Int16|  
|NUM_RESULT_SETS|Int16|  
|REMARKS|Строковое|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|Строковое|  
|PROCEDURE_OWNER|Строковое|  
|PROCEDURE_NAME|Строковое|  
|COLUMN_NAME|Строковое|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Строковое|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Строковое|  
|OVERLOAD|Int32|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CAT|Строковое|  
|PROCEDURE_SCHEM|Строковое|  
|PROCEDURE_NAME|Строковое|  
|COLUMN_NAME|Строковое|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Строковое|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Строковое|  
|COLUMN_DEF|Строковое|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|Строка|  
  
## <a name="see-also"></a>См. также  
 [Центр разработчиков наборов данных и управляемых поставщиков ADO.NET](http://go.microsoft.com/fwlink/?LinkId=217917)
