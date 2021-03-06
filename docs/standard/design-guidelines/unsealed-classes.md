---
title: "Незапечатанные классы"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f950d8de2681868fe28e09e4b51bd8156cd12e94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="unsealed-classes"></a>Незапечатанные классы
Невозможно наследовать запечатанные классы и не позволяют расширяемости. В противоположность этому классы, которые могут наследоваться от называются незапечатанных классов.  
  
 **✓ Попробуйте** использование незапечатанных классов с нет добавить виртуальный или защищенных членов, так как это отличный способ недорогого еще очень полезного расширяемость для платформу.  
  
 Разработчики часто требуется наследовать от незапечатанных классов таким образом, чтобы добавить членов удобства, например пользовательских конструкторов, новые методы или перегруженных версий метода. Например `System.Messaging.MessageQueue` не запечатан, и таким образом позволяет пользователям создавать пользовательские очереди это значение по умолчанию для определенной очереди путь или добавить пользовательские методы, которые упрощают API для конкретных сценариев.  
  
 Являются незапечатанных классов по умолчанию в большей части языков программирования, а кроме того, это рекомендуемое значение по умолчанию для большинства классов платформы. Расширяемость, обеспечиваемая незапечатанных типов намного пользователями framework с благодарностью довольно легко создать из-за сравнительно мало тестов затраты, связанные с незапечатанные типы.  
  
 *Фрагменты © 2005, 2009 корпорации Майкрософт. Все права защищены.*  
  
 *Перепечатываются разрешении Пирсона для образовательных учреждений, Inc. из [Framework рекомендации по проектированию: условные обозначения, стили и шаблоны для библиотеки .NET для повторного использования, 2-е издание](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina и Брэд Абрамс, опубликованные 22 октября 2008 г., Addison-Wesley Professional в составе ряда разработки Microsoft Windows.*  
  
## <a name="see-also"></a>См. также  
 [Рекомендации по проектированию на основе Framework](../../../docs/standard/design-guidelines/index.md)  
 [Разработка для расширяемости](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [Запечатывание](../../../docs/standard/design-guidelines/sealing.md)
