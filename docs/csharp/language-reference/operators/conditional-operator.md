---
title: "Оператор ?: (справочник по C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9abfe4ca6be29b54edd591b503069c15e02c3532
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>Оператор ?: (справочник по C#)
Условный оператор (`?:`) возвращает одно из двух значений в зависимости от значения логического выражения. Для условного оператора используется следующий синтаксис.  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a>Примечания  
 Параметр `condition` должен иметь значение `true` или `false`. Если параметр `condition` имеет значение `true`, вычисляется выражение `first_expression` и итог этого вычисления становится результатом. Если параметр `condition` имеет значение `false`, вычисляется выражение `second_expression` и итог этого вычисления становится результатом. В любом случае вычисляется только одно из двух выражений.  
  
 Параметры `first_expression` и `second_expression` должны быть одинакового типа или должно существовать неявное преобразование из одного типа в другой.  
  
 Расчеты, которые в другом случае требовали бы уточнения конструкции `if-else`, можно выражать с помощью условного оператора. Например, в следующем коде сначала используется оператор `if`, а затем — условный оператор для классификации целого числа как положительного или отрицательного.  
  
```csharp
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```  
  
 Условный оператор имеет правую ассоциативность. Выражение `a ? b : c ? d : e` вычисляется как `a ? b : (c ? d : e)`, а не как `(a ? b : c) ? d : e`.  
  
 Условный оператор не может быть перегружен.  
  
## <a name="example"></a>Пример  
 [!code-csharp[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a>См. также  
 [Справочник по C#](../../../csharp/language-reference/index.md)  
 [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)  
 [Операторы в C#](../../../csharp/language-reference/operators/index.md)  
 [if-else](../../../csharp/language-reference/keywords/if-else.md)  
 [?. и? Операторы](../../../csharp/language-reference/operators/null-conditional-operators.md)  
 [?? Оператор](../../../csharp/language-reference/operators/null-conditional-operator.md)
