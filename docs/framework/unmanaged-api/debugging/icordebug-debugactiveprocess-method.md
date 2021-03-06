---
title: "Метод ICorDebug::DebugActiveProcess"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.DebugActiveProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c17345caaec71e4d4b057bdcfc2cc395014cbf82
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugdebugactiveprocess-method"></a>Метод ICorDebug::DebugActiveProcess
Присоединяет отладчик к существующему процессу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `id`  
 [in] Идентификатор процесса, в котором отладчик должен быть связан.  
  
 `win32Attach`  
 [in] Логическое значение, равное `true` Если отладчик должен ведут себя как отладчик Win32 для процесса и направление неуправляемые обратных вызовов; в противном случае `false`.  
  
 `ppProcess`  
 [out] Указатель на адрес объекта «ICorDebugProcess», который представляет собой процесс, к которому присоединен отладчик.  
  
## <a name="remarks"></a>Примечания  
 Отладка взаимодействия не поддерживается на платформах Win9x и не x86, например основе AMD64 и IA-64-разрядных платформах.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [ICorDebug-интерфейс](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
