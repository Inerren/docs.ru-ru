---
title: pInvokeStackImbalance MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b33a3edc5780ecf07e7809ca327a304d748110f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="pinvokestackimbalance-mda"></a>pInvokeStackImbalance MDA
Управляемый помощник по отладке (MDA) `pInvokeStackImbalance` активируется, когда среда CLR обнаруживает, что глубина стека после вызова неуправляемого кода не соответствует ожидаемой глубине стека, учитывая соглашение о вызовах, указанное в атрибуте <xref:System.Runtime.InteropServices.DllImportAttribute>, а также объявление параметров в управляемой сигнатуре.  
  
> [!NOTE]
>  MDA `pInvokeStackImbalance` реализован только для 32-разрядных платформ x86.  
  
> [!NOTE]
>  В .NET Framework версии 3.5 MDA `pInvokeStackImbalance` отключен по умолчанию. При использовании .NET Framework версии 3.5 с Visual Studio 2005 MDA `pInvokeStackImbalance` будет отображаться в списке **Помощники по отладке управляемого кода** диалогового окна **Исключения** (которое отображается при выборе пункта **Исключения** в меню **Отладка**). Однако установка или снятие флажка **Вызванное** для `pInvokeStackImbalance` не включает и не отключает MDA. Этот флажок управляет только тем, вызывает ли Visual Studio исключение, когда MDA активирован.  
  
## <a name="symptoms"></a>Симптомы  
 В приложении обнаружено нарушение прав доступа или повреждение памяти при выполнении или отслеживании вызова неуправляемого кода.  
  
## <a name="cause"></a>Причина  
 Управляемая сигнатура вызова неуправляемого кода может не соответствовать неуправляемой сигнатуре вызываемого метода.  Это несоответствие может быть вызвано тем, что управляемая сигнатура не объявляет правильное количество параметров или не задает соответствующий размер для этих параметров.  MDA также может активироваться, поскольку соглашение о вызовах, возможно указанное атрибутом <xref:System.Runtime.InteropServices.DllImportAttribute>, не соответствует соглашению о вызовах неуправляемого кода.  
  
## <a name="resolution"></a>Решение  
 Просмотрите сигнатуру вызова неуправляемого кода и соглашение о вызовах, чтобы убедиться, что они соответствуют сигнатуре и соглашению о вызовах исходного целевого объекта.  Попробуйте явным образом задать соглашение о вызовах для управляемой и неуправляемой сторон. Также возможно, хотя и маловероятно, что неуправляемая функция внесла дисбаланс в стек по какой-либо другой причине, например из-за ошибки в неуправляемом компиляторе.  
  
## <a name="effect-on-the-runtime"></a>Влияние на среду выполнения  
 Заставляет все вызовы неуправляемого кода принимать неоптимизированный путь в среде CLR.  
  
## <a name="output"></a>Вывод  
 Сообщение MDA предоставляет имя вызова метода вызова неуправляемого кода, который привел к несбалансированности стека вызова.  Пример сообщения вызова неуправляемого кода в методе `SampleMethod`:  
  
```  
A call to PInvoke function 'SampleMethod' has unbalanced the stack.   
This is likely because the managed PInvoke signature does not match   
the unmanaged target signature. Check that the calling convention and   
parameters of the PInvoke signature match the target unmanaged signature.  
```  
  
## <a name="configuration"></a>Конфигурация  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeStackImbalance />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>См. также  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Диагностика ошибок посредством помощников по отладке управляемого кода](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Маршалинг взаимодействия](../../../docs/framework/interop/interop-marshaling.md)
