---
title: "Практическое руководство. Удаление сборки из глобального кэша сборок"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- global assembly cache, removing assemblies
- strong-named assemblies, global assembly cache
- removing assemblies from global assembly cache
- deleting assemblies in global assembly cache
- Global Assembly Cache tool
- GAC (global assembly cache), removing assemblies
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a17478c350d789d320e97d6b50d6f5f9daaf6db3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a>Практическое руководство. Удаление сборки из глобального кэша сборок
Существует два способа удаления сборки из глобального кэша сборок.  
  
-   С помощью [средства глобального кэша сборок (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md). Этот вариант можно использовать для удаления сборок, помещенных в глобальный кэш сборок во время разработки и тестирования.  
  
-   С помощью [установщика Windows](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx). Этот вариант следует использовать для удаления сборок при тестировании пакетов установки и для рабочих систем.  
  
### <a name="removing-an-assembly-with-gacutilexe"></a>Удаление сборки с помощью Gacutil.exe  
  
1.  В командной строке введите следующую команду:  
  
     **gacutil –u** \<*имя_сборки*>  
  
     В этой команде *имя_сборки* представляет собой имя сборки, удаляемой из глобального кэша сборок.  
  
    > [!WARNING]
    >  Не следует использовать Gacutil.exe для удаления сборок в рабочих системах, так как есть вероятность того, что некоторым приложениям эта сборка все еще нужна. Вместо этого следует использовать установщик Windows, который ведет счетчик ссылок для каждой сборки, устанавливаемой в глобальном кэше сборок.  
  
 В примере ниже из глобального кэша сборок удаляется сборка с именем `hello.dll`.  
  
```  
gacutil -u hello  
```  
  
### <a name="removing-an-assembly-with-windows-installer"></a>Удаление сборки с помощью установщика Windows  
  
1.  В разделе **Программы и компоненты** на **панели управления** выберите приложение, которое нужно удалить. Если пакет установки разместил сборки в глобальном кэше сборок, установщик Windows удалит их, если они не используются другим приложением.  
  
    > [!NOTE]
    >  Установщик Windows ведет счетчик ссылок для сборок, установленных в глобальном кэше сборок. Сборка удаляется из глобального кэша сборок только в том случае, если число ссылок на нее достигает нуля, то есть если она не используется ни одним приложением, установленным с помощью пакета установщика Windows.  
  
## <a name="see-also"></a>См. также  
 [Работа со сборками и глобальным кэшем сборок](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Практическое руководство. Установка сборки в глобальный кэш сборок](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [Gacutil.exe (программа глобального кэша сборок)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
