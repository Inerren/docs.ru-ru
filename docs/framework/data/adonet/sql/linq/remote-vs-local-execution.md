---
title: "Сравнение удаленного и локальное выполнение"
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
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2b04ba6dde572aa0a8edddc8a2a30a8e11a3e79c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="remote-vs-local-execution"></a>Сравнение удаленного и локальное выполнение
Запросы можно выполнять либо удаленно (то есть ядро базы данных выполняет запрос в базе данных) или локально ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] выполняет запрос в локальном кэше).  
  
## <a name="remote-execution"></a>Удаленное выполнение  
 Рассмотрим следующий запрос:  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 Если база данных содержит тысячи строк заказов, для обработки небольшого подмножества совсем не обязательно извлекать все строки. В [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] класс <xref:System.Data.Linq.EntitySet%601> реализует интерфейс <xref:System.Linq.IQueryable>. Этот метод гарантирует удаленное выполнение подобных запросов. Благодаря этому методу пользователь получает два существенных преимущества.  
  
-   Извлекаются только необходимые данные.  
  
-   Запросы, выполняемые ядром базы данных зачастую более эффективны благодаря индексам базы данных.  
  
## <a name="local-execution"></a>локальное выполнение  
 В других случаях бывает необходимо иметь полный набор связанных записей в локальном кэше. Для этой цели класс <xref:System.Data.Linq.EntitySet%601> предоставляет метод <xref:System.Data.Linq.EntitySet%601.Load%2A> для явной загрузки всех членов класса <xref:System.Data.Linq.EntitySet%601>.  
  
 Если класс <xref:System.Data.Linq.EntitySet%601> уже загружен, последующие запросы выполняются локально. Этот метод полезен с двух точек зрения.  
  
-   Если полный набор необходимо использовать локально или несколько раз, можно избежать удаленных запросов и связанных с ними задержек.  
  
-   Сущность можно сериализовать как полную сущность.  
  
 В следующем фрагменте кода показывается, как добиться локального выполнения.  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a>Сравнение  
 Эти две возможности предоставляют мощное сочетание параметров: удаленное выполнение для больших коллекций и локальное выполнение для малых коллекций или в тех случаях, когда требуется вся коллекция. Удаленное выполнение реализуется с помощью интерфейса <xref:System.Linq.IQueryable>, а локальное выполнение - посредством хранящейся в памяти коллекции <xref:System.Collections.Generic.IEnumerable%601>. Для принудительного выполнения локального (т. е <xref:System.Collections.Generic.IEnumerable%601>), в разделе [преобразование типа в универсальный интерфейс IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).  
  
### <a name="queries-against-unordered-sets"></a>Запросы к неупорядоченным наборам  
 Обратите внимание на важное отличие между локальной коллекцией, которая реализует <xref:System.Collections.Generic.List%601> и коллекцией, предоставляющей удаленное выполнение запросов к *неупорядоченных наборов* в реляционной базе данных. Для методов <xref:System.Collections.Generic.List%601>, например при использовании значений индексов, требуется семантика списка, которая, как правило, не реализуется посредством удаленного запроса к неупорядоченному набору. По этой причине подобные методы неявно загружают класс <xref:System.Data.Linq.EntitySet%601>, чтобы получить возможность локального выполнения.  
  
## <a name="see-also"></a>См. также  
 [Основные принципы запросов](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
