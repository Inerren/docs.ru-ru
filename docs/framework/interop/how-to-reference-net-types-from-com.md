---
title: "Практическое руководство. Создание ссылки на типы .NET из COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f58225e41d7e09471685395dd6e2194ee5de123c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reference-net-types-from-com"></a>Практическое руководство. Создание ссылки на типы .NET из COM
С точки зрения кода клиента и сервера различия между COM и .NET Framework практически незаметны. Клиенты Microsoft Visual Basic могут просматривать объект .NET в обозревателе объектов, который позволяет просмотреть методы, синтаксис, свойства и поля объекта точно так же, как если бы это был объект COM.  
  
 Процесс импорта библиотеки типов для клиентов C++ несколько сложнее, хотя для экспорта метаданных в библиотеку типов COM можно использовать те же средства. Чтобы получить доступ к элементам объекта .NET из неуправляемого клиента C++, укажите ссылку на TLB-файл (файл, созданный с помощью программы Tlbexp.exe) в директиве **#import**. При указании ссылки на библиотеку типов из C++ необходимо указать параметр **raw_interfaces_only** или импортировать определения из библиотеки базовых классов Mscorlib.tlb.  
  
### <a name="to-import-a-library"></a>Импорт библиотеки  
  
-   Укажите параметр **raw_interfaces_only** в диалоговом окне директивы **#import**. Пример:  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     -или-  
  
-   Включите директиву #import для Mscorlib.tlb. Пример:  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a>См. также  
 [Предоставление компонентов .NET Framework клиентам COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Регистрация сборок в COM](../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Вызов объекта .NET](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33)  
 [Развертывание приложения для доступа к COM](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce)
