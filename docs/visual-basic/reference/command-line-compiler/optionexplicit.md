---
title: /optionexplicit
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1cfdb94ebafa7d6a14253aeb59ab98b3a953fe4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="optionexplicit"></a>/optionexplicit
Указывает компилятору на отправку отчетов об ошибках, если переменная не объявлена до их использования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Аргументы  
 `+` &#124; `-`  
 Необязательно. Укажите `/optionexplicit+` явного объявления переменных. `/optionexplicit+` Параметр используется по умолчанию и совпадает со значением `/optionexplicit`. `/optionexplicit-` Режим обеспечивает неявное объявление переменных.  
  
## <a name="remarks"></a>Примечания  
 Если файл исходного кода содержит [оператор Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), переопределяет инструкцию `/optionexplicit` параметр компилятора командной строки.  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a>Задание/optionexplicit в Интегрированной среде разработки Visual Studio  
  
1.  Выберите проект в **Обозревателе решений**. В меню **Проект** выберите пункт **Свойства**. Дополнительные сведения см. в разделе [Знакомство с конструктором проектов](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Откройте вкладку **Компиляция**.  
  
3.  Измените значение в **Option Explicit** поле.  
  
## <a name="example"></a>Пример  
 Следующий код компилируется при `/optionexplicit-` используется.  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a>См. также  
 [Компилятор Visual Basic с интерфейсом командной строки](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Примеры командных строк компиляции](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Оператор Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Страница "Параметры Visual Basic по умолчанию", папка "Проекты", диалоговое окно "Параметры"](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
