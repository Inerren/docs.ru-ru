---
title: "Переменные (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 551b6d6feab6829c9a2f6f2e89e1918acf463411
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="variables-entity-sql"></a>Переменные (Entity SQL)
## <a name="variable"></a>Переменная  
 Выражение переменной – это ссылка на именованное выражение, определенное в текущей области. Ссылка на переменную должно быть допустимым [!INCLUDE[esql](../../../../../../includes/esql-md.md)] идентификатор, как определено в [идентификаторы](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).  
  
 В следующем примере показано применение переменной в выражении. Символ `c` в предложении FROM является определением переменной. Использование символа `c` в предложении SELECT представляет ссылку на переменную.  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>См. также  
 [Идентификаторы](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [Параметры](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [Общие сведения об Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
