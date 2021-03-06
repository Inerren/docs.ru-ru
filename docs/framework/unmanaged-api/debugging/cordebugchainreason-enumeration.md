---
title: "Перечисление CorDebugChainReason"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugChainReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugChainReason
helpviewer_keywords: CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0d501db111256861a3d0a602712e4c32f40b7b6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugchainreason-enumeration"></a>Перечисление CorDebugChainReason
Указывает причину или причины запуска цепочки вызовов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef enum CorDebugChainReason {  
    CHAIN_NONE              = 0x000,  
    CHAIN_CLASS_INIT        = 0x001,  
    CHAIN_EXCEPTION_FILTER  = 0x002,  
    CHAIN_SECURITY          = 0x004,  
    CHAIN_CONTEXT_POLICY    = 0x008,  
    CHAIN_INTERCEPTION      = 0x010,  
    CHAIN_PROCESS_START     = 0x020,  
    CHAIN_THREAD_START      = 0x040,  
    CHAIN_ENTER_MANAGED     = 0x080,  
    CHAIN_ENTER_UNMANAGED   = 0x100,  
    CHAIN_DEBUGGER_EVAL     = 0x200,  
    CHAIN_CONTEXT_SWITCH    = 0x400,  
    CHAIN_FUNC_EVAL         = 0x800  
} CorDebugChainReason;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Описание|  
|------------|-----------------|  
|`CHAIN_NONE`|Цепочки вызовов не инициированы.|  
|`CHAIN_CLASS_INIT`|Цепочка была инициирована конструктором.|  
|`CHAIN_EXCEPTION_FILTER`|Цепочка была инициирована фильтром исключений.|  
|`CHAIN_SECURITY`|Цепочка была инициирована кодом, который принудительно обеспечивает безопасность.|  
|`CHAIN_CONTEXT_POLICY`|Цепочка была инициирована контекстной политикой.|  
|`CHAIN_INTERCEPTION`|Не используется.|  
|`CHAIN_PROCESS_START`|Не используется.|  
|`CHAIN_THREAD_START`|Цепочка была инициирована началом выполнения потока.|  
|`CHAIN_ENTER_MANAGED`|Цепочка была инициирована входом в управляемый код.|  
|`CHAIN_ENTER_UNMANAGED`|Цепочка была инициирована входом в неуправляемый код.|  
|`CHAIN_DEBUGGER_EVAL`|Не используется.|  
|`CHAIN_CONTEXT_SWITCH`|Не используется.|  
|`CHAIN_FUNC_EVAL`|Цепочка была инициирована оценкой функции.|  
  
## <a name="remarks"></a>Примечания  
 Используйте [ICorDebugChain::GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) метод для выяснения причины инициирования цепочки вызовов.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Перечисления отладки](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
