---
title: "Математические функции"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8390f1e1822d7581ab0352a8c81acbc7ce545507
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="mathematical-functions"></a>Математические функции
Поставщик данных для SQL Server платформы .NET Framework (SqlClient) предоставляет математические функции, производящие вычисления на входящих значениях, предоставляемых в качестве аргументов, и возвращающие результат в виде числовых значений. Эти функции находятся в пространстве имен SqlServer, которое доступно при использовании SqlClient. Свойство пространства имен поставщика позволяет платформе Entity Framework узнать, какой префикс используется поставщиком для конкретных конструкций, таких как типы или функции. В следующей таблице описаны математические функции SqlClient.  
  
|Функция|Описание|  
|--------------|-----------------|  
|`ABS(` `expression` `)`|Возвращает абсолютное значение.<br /><br /> **Аргументы**<br /><br /> `expression`: значение типа `Int32`, `Int64`, `Double` или `Decimal`.<br /><br /> **Возвращаемое значение**<br /><br /> Абсолютное значение заданного выражения.<br /><br /> **Пример**<br /><br /> `SqlServer.ABS(-2)`|  
|`ACOS(` `expression` `)`|Возвращает значение арккосинуса указанного выражения.<br /><br /> **Аргументы**<br /><br /> `expression`: Тип `Double`.<br /><br /> **Возвращаемое значение**<br /><br /> Объект `Double`.<br /><br /> **Пример**<br /><br /> `SqlServer.ACOS(.9)`|  
|`ASIN(` `expression` `)`|Возвращает значение арксинуса указанного выражения.<br /><br /> **Аргументы**<br /><br /> `expression`: Тип `Double`.<br /><br /> **Возвращаемое значение**<br /><br /> Объект `Double`.<br /><br /> **Пример**<br /><br /> `SqlServer.ASIN(.9)`|  
|`ATAN(` `expression` `)`|Возвращает значение арктангенса указанного числового выражения.<br /><br /> **Аргументы**<br /><br /> `expression`: Тип `Double`.<br /><br /> **Возвращаемое значение**<br /><br /> Объект `Double`.<br /><br /> **Пример**<br /><br /> `SqlServer.ATAN(9)`|  
|`ATN2(` `expression`, `expression``)`|Возвращает угол в радианах, тангенс которого находится в диапазоне между двумя заданными числовыми выражениями.<br /><br /> **Аргументы**<br /><br /> `expression`: Тип `Double`.<br /><br /> **Возвращаемое значение**<br /><br /> Объект `Double`.<br /><br /> **Пример**<br /><br /> `SqlServer.ATN2(9, 8)`|  
|`CEILING(` `expression` `)`|Преобразует указанное выражение в наименьшее целое число, большее или равное данному выражению.<br /><br /> **Аргументы**<br /><br /> `expression`: значение типа `Int32`, `Int64`, `Double` или `Decimal`.<br /><br /> **Возвращаемое значение**<br /><br /> `Int32`, `Int64`, `Double`, Или `Decimal`.<br /><br /> **Пример**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]|  
|`COS(` `expression` `)`|Вычисляет тригонометрический косинус указанного угла в радианах.<br /><br /> **Аргументы**<br /><br /> `expression`: Тип `Double`.<br /><br /> **Возвращаемое значение**<br /><br /> Объект `Double`.<br /><br /> **Пример**<br /><br /> `SqlServer.COS(45)`|  
|`COT(` `expression` `)`|Вычисляет тригонометрический котангенс указанного угла в радианах.<br /><br /> **Аргументы**<br /><br /> `expression`: Тип `Double`.<br /><br /> **Возвращаемое значение**<br /><br /> Объект `Double`.<br /><br /> **Пример**<br /><br /> `SqlServer.COT(60)`|  
|`DEGREES(` `radians` `)`|Возвращает соответствующее значение угла в градусах.<br /><br /> **Аргументы**<br /><br /> `expression`: значение типа `Int32`, `Int64`, `Double` или `Decimal`.<br /><br /> **Возвращаемое значение**<br /><br /> `Int32`, `Int64`, `Double`, Или `Decimal`.<br /><br /> **Пример**<br /><br /> `SqlServer.DEGREES(3.1)`|  
|`EXP(` `expression` `)`|Вычисляет экспоненту заданного числового выражения.<br /><br /> **Аргументы**<br /><br /> `expression`: Тип `Double`.<br /><br /> **Возвращаемое значение**<br /><br /> Объект `Double`.<br /><br /> **Пример**<br /><br /> `SqlServer.EXP(1)`|  
|`FLOOR(` `expression` `)`|Преобразует указанное выражение в наибольшее целое число, меньшее или равное данному выражению.<br /><br /> **Аргументы**<br /><br /> `expression`: Тип `Double`.<br /><br /> **Возвращаемое значение**<br /><br /> Объект `Double`.<br /><br /> **Пример**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]|  
|`LOG(` `expression` `)`|Вычисляет натуральный логарифм заданного выражения типа `float`.<br /><br /> **Аргументы**<br /><br /> `expression`: Тип `Double`.<br /><br /> **Возвращаемое значение**<br /><br /> Объект `Double`.<br /><br /> **Пример**<br /><br /> `SqlServer.LOG(100)`|  
|`LOG10(` `expression` `)`|Возвращает десятичный логарифм указанного выражения типа `Double`.<br /><br /> **Аргументы**<br /><br /> `expression`: Тип `Double`.<br /><br /> **Возвращаемое значение**<br /><br /> Объект `Double`.<br /><br /> **Пример**<br /><br /> `SqlServer.LOG10(100)`|  
|`PI()`|Возвращает константу «пи» в виде значения типа `Double`.<br /><br /> **Возвращаемое значение**<br /><br /> Объект `Double`.<br /><br /> **Пример**<br /><br /> `SqlServer.PI()`|  
|`POWER(` `numeric_expression, power_expression` `)`|Вычисляет значение указанного выражения, возведенного в заданную степень.<br /><br /> **Аргументы**<br /><br /> `numeric_expression`: значение типа `Int32`, `Int64`, `Double` или `Decimal`.<br /><br /> `power_expression`: значение типа `Double`, представляющее степень, в которую необходимо возвести выражение `numeric_expression`.<br /><br /> **Возвращаемое значение**<br /><br /> Значение заданного выражения `numeric_expression` в указанной степени `power_expression`.<br /><br /> **Пример**<br /><br /> `SqlServer.POWER(2,7)`|  
|`RADIANS(` `expression` `)`|Преобразовывает градусы в радианы.<br /><br /> **Аргументы**<br /><br /> `expression`: значение типа `Int32`, `Int64`, `Double` или `Decimal`.<br /><br /> **Возвращаемое значение**<br /><br /> `Int32`, `Int64`,<br /><br /> `Double`или<br /><br /> `Decimal`.<br /><br /> **Пример**<br /><br /> `SqlServer.RADIANS(360.0)`|  
|`RAND(`[начальное значение]`)`|Возвращает случайное значение от 0 до 1.<br /><br /> **Аргументы**<br /><br /> Возвращает начальное значение в виде значения типа `Int32`. Если начальное значение не задано, то компонент SQL Server Database Engine присваивает случайно выбранное начальное значение. Для указанного начального значения возвращаемый результат всегда будет один и тот же.<br /><br /> **Возвращаемое значение**<br /><br /> Случайное значение типа `Double` от 0 до 1.<br /><br /> **Пример**<br /><br /> `SqlServer.RAND()`|  
|`ROUND(` `numeric_expression, length` [ ,`function` ]`)`|Возвращает числовое выражение, округленное до указанной длины или точности.<br /><br /> **Аргументы**<br /><br /> `numeric_expression`: значение типа `Int32`, `Int64`, `Double` или `Decimal`.<br /><br /> `length`: значение типа `Int32`, указывающее точность, до которой должно быть округлено значение аргумента `numeric_expression`. Если аргумент `length` является положительным числом, значение `numeric_expression` округляется до числа десятичных разрядов, указанных аргументом `length`. Если аргумент `length` является отрицательным числом, значение `numeric_expression` округляется слева от десятичной запятой, как указано аргументом `length`.<br /><br /> `function`: (необязательно) `Int32` , представляющий тип выполняемой операции. Когда функция опущен или имеет значение 0 (по умолчанию), `numeric_expression` округляется. Если значение, отличное от указано значение 0, `numeric_expression` усекается.<br /><br /> **Возвращаемое значение**<br /><br /> Значение заданного выражения `numeric_expression` в указанной степени `power_expression`.<br /><br /> **Пример**<br /><br /> `SqlServer.ROUND(748.58, -3)`|  
|`SIGN(` `expression` `)`|Возвращает положительный знак (+1), ноль (0) или отрицательный знак (-1) указанного выражения.<br /><br /> **Аргументы**<br /><br /> `expression`: `Int32`, `Int64`, `Double` или `Decimal`<br /><br /> **Возвращаемое значение**<br /><br /> `Int32`, `Int64`, `Double`, Или `Decimal`.<br /><br /> **Пример**<br /><br /> `SqlServer.SIGN(-10)`|  
|`SIN(` `expression` `)`|Вычисляет тригонометрический синус заданного угла в радианах и возвращает выражение типа `Double`.<br /><br /> **Аргументы**<br /><br /> `expression`: Тип `Double`.<br /><br /> **Возвращаемое значение**<br /><br /> Объект `Double`.<br /><br /> **Пример**<br /><br /> `SqlServer.SIN(20)`|  
|`SQRT(` `expression` `)`|Возвращает квадратный корень указанного выражения.<br /><br /> **Аргументы**<br /><br /> `expression`: Тип `Double`.<br /><br /> **Возвращаемое значение**<br /><br /> Объект `Double`.<br /><br /> **Пример**<br /><br /> `SqlServer.SQRT(3600)`|  
|`SQUARE(` `expression` `)`|Возвращает значение указанного выражения в квадрате.<br /><br /> **Аргументы**<br /><br /> `expression`: Тип `Double`.<br /><br /> **Возвращаемое значение**<br /><br /> Объект `Double`.<br /><br /> **Пример**<br /><br /> `SqlServer.SQUARE(25)`|  
|`TAN(` `expression` `)`|Вычисляет тангенс заданного выражения.<br /><br /> **Аргументы**<br /><br /> `expression`: `Double`<br /><br /> **Возвращаемое значение**<br /><br /> `Double`<br /><br /> **Пример**<br /><br /> `SqlServer.TAN(45.0)`|  
  
 Дополнительные сведения о математических функциях, поддерживаемых SqlClient, см. в документации к версии SQL Server, указанной в манифесте поставщика SqlClient.  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Математические функции (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115913)|[Математические функции (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115911)|[Математические функции (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115912)|  
  
## <a name="see-also"></a>См. также  
 [Функции SqlClient для Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
