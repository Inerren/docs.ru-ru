---
title: /keycontainer
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f7c5ffa255ba9ac2f062ea52eb3471659e0192b
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2017
---
# <a name="keycontainer"></a>/keycontainer
Указывает имя контейнера для пары ключей, чтобы задать для сборки строгое имя.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
/keycontainer:container  
```  
  
## <a name="arguments"></a>Аргументы  
  
|Термин|Определение|  
|---|---|  
|`container`|Обязательный. Файл контейнера, содержащий ключ. Заключите имя файла в кавычки ("»), если имя содержит пробелы.|  
  
## <a name="remarks"></a>Примечания  
 Компилятор создает совместно используемый компонент путем вставки открытого ключа в манифест сборки и подписывая окончательную сборку закрытым ключом. Чтобы создать файл ключа, введите `sn -k``file` из командной строки. `-i` Параметр устанавливает пару ключей в контейнер. Дополнительные сведения см. на странице [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) (Sn.exe: средство строгих имен).  
  
 Если компиляция выполняется с `/target:module`, имя файла ключа сохраняется в модуле и включается в сборку, которая создается при компиляции с параметром [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Этот параметр можно также указать в исходном коде любого модуля MSIL в качестве настраиваемого атрибута (<xref:System.Reflection.AssemblyKeyNameAttribute>).  
  
 Также можно передать сведения о шифровании компилятору с помощью параметра [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md). Если необходимо использовать частично подписанную сборку, применяйте параметр [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md).  
  
 В разделе [Создание и использование сборок](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md) Дополнительные сведения о подписи сборки.  
  
> [!NOTE]
>  `/keycontainer` Параметр недоступен в среде разработки Visual Studio; она доступна только при компиляции из командной строки.  
  
## <a name="example"></a>Пример  
 Следующий код компилирует исходный файл `Input.vb` и указывает контейнер ключей.  
  
```  
vbc /keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>См. также  
 [Сборки и глобальный кэш сборок](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Компилятор Visual Basic с интерфейсом командной строки](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [Примеры командных строк компиляции](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
