---
title: "How to: Write a Parallel.For Loop with Thread-Local Variables | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "parallel for loops, how to use local state"
ms.assetid: 68384064-7ee7-41e2-90e3-71f00bde01bb
caps.latest.revision: 23
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 23
---
# How to: Write a Parallel.For Loop with Thread-Local Variables
В этом примере показано, как использовать локальные переменные потока для хранения и получения состояния каждой отдельной задачи, создаваемой циклом <xref:System.Threading.Tasks.Parallel.For%2A>.  Благодаря локальным переменным потока вы можете избежать дополнительной нагрузки при синхронизации большого количества доступов к общему состоянию.  Вместо записи в общий ресурс при каждой итерации вы вычисляете и сохраняете значение до тех пор, пока не будут выполнены все итерации для задачи.  После этого вы можете однократно записать итоговый результат в общий ресурс или передать его в другой метод.  
  
## Пример  
 В следующем примере выполняется вызов метода <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> для вычисления суммы значений в массиве, содержащем один миллион элементов.  Значение каждого элемента равно его индексу.  
  
 [!code-csharp[TPL_Parallel#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/forandforeach_simple.cs#05)]
 [!code-vb[TPL_Parallel#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/forwiththreadlocal.vb#05)]  
  
 Два первых параметра каждого метода <xref:System.Threading.Tasks.Parallel.For%2A> задают начальное и конечное значения итерации.  В этой перегрузке метода третий параметр используется для инициализации локального состояния.  В этом контексте локальное состояние означает переменную, время существования которой начинается непосредственно перед первой итерацией цикла в текущем потоке и заканчивается сразу же после последней итерации.  
  
 Третий параметр имеет тип <xref:System.Func%601>, где `TResult` — это тип переменной для сохранения локального состояния потока.  Этот тип определяется аргументом универсального типа, переданным во время вызова универсального метода <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29>, в данном случае он равен <xref:System.Int64>.  Этот аргумент типа сообщает компилятору тип временной переменной, которая будет использоваться для хранения локального состояния в потоке.  В этом примере выражение `() => 0` \(или `Function() 0` в Visual Basic\) инициализирует локальную переменную потока с нулевым значением.  Если бы аргумент универсального типа имел ссылочный тип или тип пользовательского значения, выражение выглядело бы следующим образом:  
  
```csharp  
() => new MyClass()  
```  
  
```vb  
Function() new MyClass()  
```  
  
 Четвертый параметр определяет логическую схему цикла.  Он должен быть делегатом или лямбда\-выражением, сигнатура которого имеет значение `Func<int, ParallelLoopState, long, long>` в C\# или `Func(Of Integer, ParallelLoopState, Long, Long)` в Visual Basic.  Первый параметр представляет собой значение счетчика цикла для данной итерации цикла.  Второй является объектом <xref:System.Threading.Tasks.ParallelLoopState>, который можно использовать для выхода из цикла; данный объект предоставляется классом <xref:System.Threading.Tasks.Parallel> каждому экземпляру цикла.  Третий параметр представляет собой локальную переменную потока.  Последний параметр является типом возвращаемого значения.  В данном случае этот тип имеет значение <xref:System.Int64>, так как именно его мы указали в аргументе типа <xref:System.Threading.Tasks.Parallel.For%2A>.  Эта переменная называется `subtotal` и возвращается лямбда\-выражением.  Возвращаемое значение используется для инициализации `subtotal` на каждой последующей итерации цикла.  Этот последний параметр также можно представить себе в виде значения, которое передается в каждую итерацию, а после выполнения последней итерации передается в делегат `localFinally`.  
  
 Пятый параметр задает метод, который вызывается один раз после выполнения всех итераций в определенном потоке.  Тип входного аргумента опять соответствует аргументу типа метода <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> и типу, возвращаемому телом лямбда\-выражения.  В данном примере это значение добавляется в переменную в области видимости класса потокобезопасным образом путем вызова метода <xref:System.Threading.Interlocked.Add%2A?displayProperty=fullName>.  Благодаря использованию локальной переменной потока нам не пришлось выполнять запись в эту переменную класса при каждой итерации цикла.  
  
 Дополнительные сведения об использовании лямбда\-выражений см. в разделе [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## См. также  
 [Data Parallelism](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)   
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)   
 [Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)   
 [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)