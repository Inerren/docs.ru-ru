---
title: "Метод ICorProfilerInfo7::GetInMemorySymbolsLength"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type: COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 34da00bdc33a836e5f459e6e4314f252e1e39e9b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>Метод ICorProfilerInfo7::GetInMemorySymbolsLength
[Поддерживается в .NET Framework 4.6.1 и более поздних версиях.]  
  
 Возвращает длину потока в памяти символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `moduleId`  
 [in] Идентификатор модуля, содержащего потока в памяти.  
  
 pCountSymbolBytes  
 [out] Указатель на `DWORD` значение, которое при возврате из метода содержит длину потока в байтах.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `S_OK` Если длина потока памяти может определяться, даже если оно равно нулю (0).  
  
 Метод возвращает `CORPROF_E_MODULE_IS_DYNAMIC` метод создан с помощью <xref:System.Reflection.Emit?displayProperty=nameWithType>.  
  
## <a name="remarks"></a>Примечания  
 Если модуль содержит символы в памяти, длина потока помещается в `pCountSymbolBytes`. Если модуль не содержит символов в памяти `*pCountSymbolBytes = 0`.  
  
> [!NOTE]
>  Текущая реализация не поддерживает Reflection.Emit. Если модуль был создан с помощью Reflection.Emit, метод возвращает `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Интерфейс ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
