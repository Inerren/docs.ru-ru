---
title: "Профилирующие интерфейсы"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
caps.latest.revision: "31"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5c0423f9c8b01c1289e1107c0c16c59968a6e2a4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-interfaces"></a><span data-ttu-id="1ec01-102">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="1ec01-102">Profiling Interfaces</span></span>
<span data-ttu-id="1ec01-103">В этом разделе описываются неуправляемые интерфейсы, позволяющие профилировать программу, выполняемую в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="1ec01-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ec01-104">Содержание</span><span class="sxs-lookup"><span data-stu-id="1ec01-104">In This Section</span></span>  
 [<span data-ttu-id="1ec01-105">Интерфейс ICLRProfiling</span><span class="sxs-lookup"><span data-stu-id="1ec01-105">ICLRProfiling Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 <span data-ttu-id="1ec01-106">Предоставляет [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) метод, который позволяет профилировщику для присоединения к выполняющемуся процессу.</span><span class="sxs-lookup"><span data-stu-id="1ec01-106">Provides the [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="1ec01-107">Интерфейс ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="1ec01-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="1ec01-108">Позволяет профилировщику информировать среду CLR ссылки на сборки, которые профилировщик добавит в [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="1ec01-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="1ec01-109">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="1ec01-109">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 <span data-ttu-id="1ec01-110">Предоставляет методы, используемые средой CLR для уведомления профилировщика кода при событиях, на которые подписан профилировщик.</span><span class="sxs-lookup"><span data-stu-id="1ec01-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="1ec01-111">Интерфейс ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="1ec01-111">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 <span data-ttu-id="1ec01-112">Расширяет интерфейс `ICorProfilerCallback` обратными вызовами, поддерживаемыми платформой .NET Framework 2.0 и более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="1ec01-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="1ec01-113">Интерфейс ICorProfilerCallback3</span><span class="sxs-lookup"><span data-stu-id="1ec01-113">ICorProfilerCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 <span data-ttu-id="1ec01-114">Предоставляет методы обратного вызова, используемые средой CLR для передачи сведений о подключенном и отключенном состоянии профилировщику.</span><span class="sxs-lookup"><span data-stu-id="1ec01-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="1ec01-115">Интерфейс ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="1ec01-115">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 <span data-ttu-id="1ec01-116">Предоставляет методы обратного вызова, используемые средой CLR для передачи сведений профилировщику.</span><span class="sxs-lookup"><span data-stu-id="1ec01-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="1ec01-117">Интерфейс ICorProfilerCallback5</span><span class="sxs-lookup"><span data-stu-id="1ec01-117">ICorProfilerCallback5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 <span data-ttu-id="1ec01-118">Предоставляет метод, идентифицирующий транзитивное замыкание объектов, на которые ссылаются корни сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="1ec01-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="1ec01-119">Интерфейс ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="1ec01-119">ICorProfilerCallback6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 <span data-ttu-id="1ec01-120">Предоставляет метод обратного вызова, который используется средой CLR для уведомления профилировщика о загрузке сборки.</span><span class="sxs-lookup"><span data-stu-id="1ec01-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="1ec01-121">Интерфейс ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="1ec01-121">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 <span data-ttu-id="1ec01-122">Предоставляет метод обратного вызова, который общеязыковая среда выполнения использует для уведомления профилировщика о том, что обновляется поток символов, связанный с модулем в памяти.</span><span class="sxs-lookup"><span data-stu-id="1ec01-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
 [<span data-ttu-id="1ec01-123">Интерфейс ICorProfilerFunctionControl</span><span class="sxs-lookup"><span data-stu-id="1ec01-123">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="1ec01-124">Предоставляет методы, позволяющие профилировщику кода взаимодействовать со средой выполнения CLR и контролировать порядок генерирования кода JIT-компилятором при повторной компиляции указанного метода.</span><span class="sxs-lookup"><span data-stu-id="1ec01-124">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="1ec01-125">ICorProfilerFunctionEnum-интерфейс</span><span class="sxs-lookup"><span data-stu-id="1ec01-125">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="1ec01-126">Предоставляет методы для последовательного перебора коллекции функций в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="1ec01-126">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="1ec01-127">ICorProfilerInfo-интерфейс</span><span class="sxs-lookup"><span data-stu-id="1ec01-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 <span data-ttu-id="1ec01-128">Предоставляет методы, которые используются профилировщиками кода для взаимодействия со средой CLR с целью управления отслеживанием событий и для запроса сведений.</span><span class="sxs-lookup"><span data-stu-id="1ec01-128">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="1ec01-129">ICorProfilerInfo2-интерфейс</span><span class="sxs-lookup"><span data-stu-id="1ec01-129">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 <span data-ttu-id="1ec01-130">Расширяет интерфейс `ICorProfilerInfo` методами, поддерживаемыми платформой .NET Framework 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="1ec01-130">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="1ec01-131">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="1ec01-131">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 <span data-ttu-id="1ec01-132">Расширяет интерфейс `ICorProfilerInfo2` методами, поддерживаемыми платформой [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="1ec01-132">Extends the `ICorProfilerInfo2` interface with methods supported in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] and later versions.</span></span>  
  
 [<span data-ttu-id="1ec01-133">Интерфейс ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="1ec01-133">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 <span data-ttu-id="1ec01-134">Предоставляет методы, которые используются профилировщиками кода для взаимодействия со средой CLR с целью управления отслеживанием событий и для запроса сведений.</span><span class="sxs-lookup"><span data-stu-id="1ec01-134">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="1ec01-135">Интерфейс ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="1ec01-135">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 <span data-ttu-id="1ec01-136">Предоставляет методы, которые используются профилировщиками кода для взаимодействия со средой CLR с целью управления отслеживанием событий.</span><span class="sxs-lookup"><span data-stu-id="1ec01-136">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="1ec01-137">Интерфейс ICorProfilerInfo6</span><span class="sxs-lookup"><span data-stu-id="1ec01-137">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 <span data-ttu-id="1ec01-138">Предоставляет перечислитель для всех методов, принадлежащих данного модуля NGen, и, встраиваются в основной части данного метода.</span><span class="sxs-lookup"><span data-stu-id="1ec01-138">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="1ec01-139">Интерфейс ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="1ec01-139">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 <span data-ttu-id="1ec01-140">Предоставляет метод для применения вновь определен метаданных для модуля и, обеспечивающий доступ к поток символов в памяти.</span><span class="sxs-lookup"><span data-stu-id="1ec01-140">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="1ec01-141">Icorprofilermoduleenum-интерфейс</span><span class="sxs-lookup"><span data-stu-id="1ec01-141">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="1ec01-142">Предоставляет методы для последовательного перебора коллекции модулей, загруженных приложением или профилировщиком.</span><span class="sxs-lookup"><span data-stu-id="1ec01-142">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="1ec01-143">Icorprofilerobjectenum-интерфейс</span><span class="sxs-lookup"><span data-stu-id="1ec01-143">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="1ec01-144">Предоставляет методы для последовательного перебора коллекции замороженный объектов, создаваемых [Ngen.exe (генератор образов в машинном)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="1ec01-144">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="1ec01-145">Интерфейс ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="1ec01-145">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="1ec01-146">Предоставляет методы для последовательного перебора коллекции потоков в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="1ec01-146">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="1ec01-147">IMethodMalloc-интерфейс</span><span class="sxs-lookup"><span data-stu-id="1ec01-147">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 <span data-ttu-id="1ec01-148">Предоставляет [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) метод выделения памяти для нового тела функции промежуточного языка MSIL.</span><span class="sxs-lookup"><span data-stu-id="1ec01-148">Provides the [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1ec01-149">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="1ec01-149">Related Sections</span></span>  
 [<span data-ttu-id="1ec01-150">Общие сведения о профилировании</span><span class="sxs-lookup"><span data-stu-id="1ec01-150">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="1ec01-151">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="1ec01-151">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="1ec01-152">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="1ec01-152">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [<span data-ttu-id="1ec01-153">Структуры профилирования</span><span class="sxs-lookup"><span data-stu-id="1ec01-153">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)