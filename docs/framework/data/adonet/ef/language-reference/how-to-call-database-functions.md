---
title: "Практическое руководство. Вызов функций базы данных"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dcc8c0bd232c6e88cbfc378d1c8df4ed3b11834e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-database-functions"></a>Практическое руководство. Вызов функций базы данных
Класс <xref:System.Data.Objects.SqlClient.SqlFunctions> содержит методы среды CLR, предоставляющие доступ к функциям SQL Server для использования в запросах LINQ to Entities. При использовании методов <xref:System.Data.Objects.SqlClient.SqlFunctions> в запросах LINQ to Entities в базе данных выполняются соответствующие функции базы данных.  
  
> [!NOTE]
>  Функции базы данных, которые производят вычисление по ряду значений и возвращают одиночное значение (известные также как статистические функции баз данных), могут вызываться напрямую. Другие канонические функции могут вызываться только в составе запроса LINQ to Entities. Чтобы вызвать агрегатную функцию напрямую, ей необходимо передать экземпляр <xref:System.Data.Objects.ObjectQuery%601>. Дополнительные сведения см. в приведенном ниже втором примере.  
  
> [!NOTE]
>  Методы класса <xref:System.Data.Objects.SqlClient.SqlFunctions> поддерживаются только в функциях SQL Server. Аналогичные классы, предоставляющие функции баз данных, могут быть доступны в других поставщиках.  
  
## <a name="example"></a>Пример  
 В следующем примере используется [модели AdventureWorks Sales](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832). В примере выполняется запрос LINQ to Entities, в котором с помощью метода <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> возвращаются все контакты, в которых фамилия начинается с «Si»:  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a>Пример  
 В следующем примере используется [модели AdventureWorks Sales](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832). В примере напрямую вызывается статистический метод <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A>. Обратите внимание, что в функцию передается экземпляр <xref:System.Data.Objects.ObjectQuery%601>, что позволяет вызывать ее, хотя она и не входит в состав запроса LINQ to Entities.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a>См. также  
 [Вызов функций в запросах LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [Запросы в LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
