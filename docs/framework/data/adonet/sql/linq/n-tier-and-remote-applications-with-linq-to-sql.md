---
title: "N-уровневые и удаленные приложения и LINQ to SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f44b6da8ecc8d036a9550856f71b2981770e9478
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a>N-уровневые и удаленные приложения и LINQ to SQL
Существует возможность создания многоуровневых приложений, использующих [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Как правило [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] контекст данных, классы сущностей и логики конструкций запросов расположены на среднем уровне доступа к данным (DAL). Бизнес-логика и непостоянные данные могут быть полностью реализованы в разделяемых классах, методах сущностей, контексте данных либо в отдельных классах.  
  
 Уровень клиента или представления вызывает методы в удаленном интерфейсе среднего уровня; DAL в этом интерфейсе выполнит запросы или хранимые процедуры, сопоставленные методам <xref:System.Data.Linq.DataContext>. Обычно средний уровень возвращает данные клиентам в виде XML-представлений сущностей или прокси-объектов.  
  
 На среднем уровне сущности создаются при помощи контекста данных, который отслеживает их состояние и управляет отложенной загрузкой из базы данных и передачей изменений в базу данных. Эти сущности присоединены к `DataContext`. Однако после отправки сущностей на другой уровень с помощью сериализации происходит их отсоединение, означающее, что `DataContext` больше не отслеживает их состояние. Сущности, отправляемые клиентом обратно для обновлений, следует повторно присоединить к контексту данных, прежде чем [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] сможет отправить изменения в базу данных. Если для проверок оптимистической блокировки требуются исходные значения и/или метки времени, клиент должен предоставить их обратно на средний уровень.  
  
 В приложениях ASP.NET <xref:System.Web.UI.WebControls.LinqDataSource> управляет большей частью данного сложного процесса. Дополнительные сведения см. в разделе [NIB: Обзор элемента управления веб-сервера LinqDataSource](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).  
  
## <a name="additional-resources"></a>Дополнительные ресурсы  
 Дополнительные сведения о развертывании многоуровневого приложения, использующего [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], см. в следующих разделах.  
  
-   [LINQ to SQL N-уровневые с ASP.NET](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-aspnet.md)  
  
-   [LINQ to SQL N-уровневые веб-службы](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
  
-   [LINQ to SQL и тесно связанные клиентские / серверные приложения](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-with-tightly-coupled-client-server-applications.md)  
  
-   [Реализация N-уровневой бизнес-логики](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)  
  
-   [Извлечение данных и операции CUD в N-уровневых приложениях (LINQ to SQL)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)  
  
 Дополнительные сведения о многоуровневых приложениях, см. в разделе [работы с наборами данных в n уровневых приложениях](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20).  
  
## <a name="see-also"></a>См. также  
 [Общие сведения](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
