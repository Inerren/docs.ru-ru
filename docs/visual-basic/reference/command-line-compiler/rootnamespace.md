---
title: /rootnamespace
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6b5da8e5eacacde9de5bdc54ef2d5e4d7f0d2653
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="rootnamespace"></a>/rootnamespace
Задает пространство имен для всех объявлений типов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
/rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Аргументы  
  
|Термин|Определение|  
|---|---|  
|`namespace`|Имя пространства имен, в котором находятся все объявления типов для текущего проекта.|  
  
## <a name="remarks"></a>Примечания  
 При использовании исполняемого файла Visual Studio (Devenv.exe) для компиляции в проект, созданный в среде разработки Visual Studio, используйте `/rootnamespace` для указания значения <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> свойство. В разделе [командной строки devenv](/visualstudio/ide/reference/devenv-command-line-switches) для получения дополнительной информации.  
  
 Использовать CLR дизассемблер MSIL (`Ildasm.exe`) для просмотра имен пространств имен в выходном файле.  
  
|Задание/RootNamespace в Visual Studio интегрированной среде разработки|  
|---|  
|1.  Выберите проект в **Обозревателе решений**. В меню **Проект** выберите пункт **Свойства**. Дополнительные сведения см. в разделе [Знакомство с конструктором проектов](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Перейдите на вкладку **Приложение** .<br />3.  Измените значение в **корневое пространство имен** поле.|  
  
## <a name="example"></a>Пример  
 Следующий код компилирует `In.vb` и помещает все объявления типов в пространстве имен `mynamespace`.  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>См. также  
 [Компилятор Visual Basic с интерфейсом командной строки](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Ildasm.exe (дизассемблер IL)](https://msdn.microsoft.com/library/f7dy01k1)  
 [Примеры командных строк компиляции](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
