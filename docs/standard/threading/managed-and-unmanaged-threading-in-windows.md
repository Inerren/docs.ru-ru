---
title: "Управляемые и неуправляемые потоки в Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], unmanaged
- threading [.NET Framework], managed
- managed threading
ms.assetid: 4fb6452f-c071-420d-9e71-da16dee7a1eb
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c55caaff3fd96b2791e75a392a9522abfceb22e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="managed-and-unmanaged-threading-in-windows"></a>Управляемые и неуправляемые потоки в Windows
Управление всеми потоками осуществляется посредством класса <xref:System.Threading.Thread> , включая потоки, созданные средой CLR или созданные за пределами среды выполнения и входящие в управляемую среду для выполнения кода. Среда выполнения отслеживает в своем процессе все потоки, которые когда-либо выполняли код в управляемой среде. Другие потоки она не отслеживает. Потоки могут входить в управляемую среду выполнения посредством COM-взаимодействия (так как среда выполнения предоставляет управляемые объекты неуправляемой среде в качестве COM-объектов), функции COM [DllGetClassObject](https://msdn.microsoft.com/en-us/library/ms680760.aspx) и вызова неуправляемого кода.  
  
 Когда неуправляемый поток входит в среду выполнения, например, посредством вызываемой оболочки COM, система проверяет локальное хранилище потока данного потока для поиска внутреннего управляемого объекта <xref:System.Threading.Thread> . Если он найден, среда выполнения уже оповещена об этом потоке. Если найти объект не удается, среда выполнения создает новый объект <xref:System.Threading.Thread> и устанавливает его в локальном хранилище потока данного потока.  
  
 При использовании управляемых потоков <xref:System.Threading.Thread.GetHashCode%2A?displayProperty=nameWithType> является идентификация управляемого потока. В течение времени существования вашего потока он не будет конфликтовать со значением из любого другого потока независимо от того, из какого домена приложения вы получили это значение.  
  
> [!NOTE]
>  **ThreadId** операционной системы не имеет фиксированного отношения с управляемым потоком, так как неуправляемый узел может управлять отношением между управляемым и неуправляемым потоками. В частности, более сложный узел может использовать Fiber API, чтобы спланировать нескольких управляемых потоков для одного потока операционной системы или перемещать управляемый поток по разным потокам операционной системы.  
  
## <a name="mapping-from-win32-threading-to-managed-threading"></a>Сопоставление потоков Win32 с управляемыми потоками  
 В следующей таблице элементы потоков Win32 сопоставляются со своими ближайшими аналогами из среды выполнения. Обратите внимание, что такое сопоставление не означает идентичную функциональность. Например, **TerminateThread** не выполняет предложения **finally** , не освобождает ресурсы и не может быть запрещен. Однако <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> выполняет весь ваш код отката, освобождает все ресурсы и может быть отменен с помощью <xref:System.Threading.Thread.ResetAbort%2A>. Прежде чем делать предположения о функциональности, тщательно изучите документацию.  
  
|В Win32|В среде CLR|  
|--------------|------------------------------------|  
|**CreateThread**|Сочетание **Thread** и <xref:System.Threading.ThreadStart>|  
|**TerminateThread**|<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>|  
|**SuspendThread**|<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>|  
|**ResumeThread**|<xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>|  
|**Sleep**|<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>|  
|**WaitForSingleObject** в дескрипторе потока|<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>|  
|**ExitThread**|Эквивалент отсутствует|  
|**GetCurrentThread**|<xref:System.Threading.Thread.CurrentThread%2A?displayProperty=nameWithType>|  
|**SetThreadPriority**|<xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType>|  
|Эквивалент отсутствует|<xref:System.Threading.Thread.Name%2A?displayProperty=nameWithType>|  
|Эквивалент отсутствует|<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>|  
|Близко к **CoInitializeEx** (OLE32.DLL)|<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>|  
  
## <a name="managed-threads-and-com-apartments"></a>Управляемые потоки и подразделения COM  
 Управляемый поток может быть отмечен для указания того, что в нем будет размещаться [однопотоковое](http://msdn.microsoft.com/library/windows/desktop/ms680112.aspx) или [многопотоковое](http://msdn.microsoft.com/library/windows/desktop/ms693421.aspx) подразделение. (Дополнительные сведения об архитектуре потоков COM см. в разделе [Процессы, потоки и подразделения](http://msdn.microsoft.com/library/windows/desktop/ms693344.aspx).) Методы <xref:System.Threading.Thread.GetApartmentState%2A>, <xref:System.Threading.Thread.SetApartmentState%2A> и <xref:System.Threading.Thread.TrySetApartmentState%2A> класса <xref:System.Threading.Thread> возвращают и назначают состояние подразделения потока. Если состояние не было задано, <xref:System.Threading.Thread.GetApartmentState%2A> возвращает <xref:System.Threading.ApartmentState.Unknown?displayProperty=nameWithType>.  
  
 Свойство может быть задано только в том случае, если поток находится в <xref:System.Threading.ThreadState.Unstarted?displayProperty=nameWithType> состояние; его можно задать только один раз для потока.  
  
 Если состояние подразделения не задано до запуска потока, этот поток инициализируется в качестве многопотокового подразделения (MTA). Поток метода завершения и все потоки, управляемые <xref:System.Threading.ThreadPool> , являются многопотоковыми подразделениями.  
  
> [!IMPORTANT]
>  Для кода запуска приложения единственный способ управления состоянием подразделения заключается в применении <xref:System.MTAThreadAttribute> или <xref:System.STAThreadAttribute> к процедуре точки входа. В .NET Framework 1.0 и 1.1 свойство <xref:System.Threading.Thread.ApartmentState%2A> можно задать в качестве первой строки кода. В .NET Framework 2.0 это запрещено.  
  
 Управляемые объекты, предоставляемые интерфейсу COM, работают так, как если бы они агрегировали упаковщик в режиме свободного потока. Другими словами, их можно вызвать из любого подразделения COM в режиме свободного потока. В таком режиме не работают только управляемые объекты, производные от <xref:System.EnterpriseServices.ServicedComponent> или <xref:System.Runtime.InteropServices.StandardOleMarshalObject>.  
  
 В управляемом коде отсутствует поддержка <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> , если только вы не используете контексты и контекстно-привязанные управляемые экземпляры. Если вы используете Enterprise Services, то объект должен быть производным от <xref:System.EnterpriseServices.ServicedComponent> (который сам является производным от <xref:System.ContextBoundObject>).  
  
 Когда управляемый код вызывает COM-объекты, он всегда следует правилам COM. Другими словами, он выполняет вызов через прокси-серверы подразделения COM и оболочки контекста COM+ 1.0, как того требует OLE32.  
  
## <a name="blocking-issues"></a>Блокировка неполадок  
 Если поток выполняет неуправляемый вызов для операционной системы, которая заблокировала этот поток в неуправляемом коде, среда выполнения не берет на себя управление им для <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> или <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. В случае использования <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>, среда выполнения помечает поток **прервать** и берет управление, когда он повторно входит в управляемый код. Вместо неуправляемой блокировки рекомендуется использовать управляемую блокировку. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>,<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType>, <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType>и так далее реагируют на <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> и <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Кроме того, если ваш поток находится в однопотоковом подразделении, все эти операции управляемой блокировки будут корректно выдавать сообщения в ваше подразделение, пока поток находится в заблокированном состоянии.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>  
 <xref:System.Threading.ThreadState>  
 <xref:System.EnterpriseServices.ServicedComponent>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.Monitor>
