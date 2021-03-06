---
title: "Необязательные параметры (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- parameters [Visual Basic], optional
- Visual Basic code, procedures
- procedures [Visual Basic], optional arguments
- optional arguments
- named arguments [Visual Basic], and optional arguments
- optional parameters
- Optional keyword [Visual Basic], optional arguments
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], and named arguments
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e57023f594cfe4cd79d59cc8541fcf18018de0ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="optional-parameters-visual-basic"></a>Необязательные параметры (Visual Basic)
Некоторые аргументы процедуры можно задать как необязательные, тем самым указывая, что их можно не задавать при вызове процедуры. *Необязательные параметры* обозначаются `Optional` ключевого слова в определении процедуры. Действуют следующие правила.  
  
-   Для каждого необязательного параметра в определении процедуры должно быть указано значение по умолчанию.  
  
-   Значение по умолчанию для необязательного параметра следует задавать в виде константного выражения.  
  
-   Каждый параметр, идущий в определении процедуры после необязательного, также должен быть необязательным.  
  
 Ниже приведен синтаксис объявления процедуры с необязательным параметром:  
  
```vb  
Sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## <a name="calling-procedures-with-optional-parameters"></a>Вызов процедур с необязательными параметрами  
 При вызове процедуры с необязательным параметром можно опускать этот аргумент. Если он не задан, процедура будет использовать значение по умолчанию, объявленное для параметра.  
  
 Можно опустить сразу несколько необязательных аргументов в списке аргументов, ставя несколько запятых подряд для обозначения их позиций. Ниже приводится пример вызова процедуры, при котором задаются первый и четвертый аргументы, а второй и третий пропускаются.  
  
```vb  
Sub name(argument 1, , , argument 4)  
```  
  
 В следующем примере происходит несколько вызовов функции `MsgBox`. У функции `MsgBox` есть один обязательный параметр и два необязательных параметра.  
  
 При первом вызове `MsgBox` указываются все три аргумента в том порядке, в котором они определены в `MsgBox`. При втором вызове указывается только обязательный аргумент. При третьем и четвертом вызове указываются первый и третий аргументы. Третий вызов указывает аргумент по позиции, а четвертый — по имени.  
  
 [!code-vb[VbVbcnProcedures#47](./codesnippet/VisualBasic/optional-parameters_1.vb)]  
  
## <a name="determining-whether-an-optional-argument-is-present"></a>Определение наличия необязательного аргумента  
 Процедура во время выполнения не может отличить пропущенный аргумент от аргумента, для которого в вызывающем коде явным образом задано значение по умолчанию. Если такое различение существенно, можно задать в качестве значения по умолчанию значение, которое вряд ли будет использоваться. В следующей процедуре определяется необязательный параметр `office`и проверяется его значение по умолчанию `QJZ`, чтобы увидеть опущен ли он в вызове:  
  
 [!code-vb[VbVbcnProcedures#46](./codesnippet/VisualBasic/optional-parameters_2.vb)]  
  
 Если необязательный параметр имеет ссылочный тип, например, `String`, то можно использовать `Nothing` в качестве значения по умолчанию, при условии, что это не является ожидаемым значением аргумента.  
  
## <a name="optional-parameters-and-overloading"></a>Необязательные параметры и перегрузка  
 Другой способ определения процедуры с необязательными параметрами состоит в использовании перегрузки. Если имеется один необязательный параметр, то можно определить две перегруженные версии процедуры, одна принимает параметр, а другая — нет. Такой подход становится более сложным с увеличением числа необязательных параметров. Однако, его преимущество заключается в том, что он позволяет точно знать, все ли необязательные аргументы заданы в вызывающей программе.  
  
## <a name="see-also"></a>См. также  
 [Процедуры](./index.md)  
 [Параметры и аргументы процедуры](./procedure-parameters-and-arguments.md)  
 [Передача аргументов по значению и по ссылке](./passing-arguments-by-value-and-by-reference.md)  
 [Передача аргументов по позиции и по имени](./passing-arguments-by-position-and-by-name.md)  
 [Массивы параметров](./parameter-arrays.md)  
 [Перегрузка процедур](./procedure-overloading.md)  
 [Необязательный](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
