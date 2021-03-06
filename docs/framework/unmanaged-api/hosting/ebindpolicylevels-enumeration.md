---
title: "Перечисление EBindPolicyLevels"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EBindPolicyLevels
api_location: mscoree.dll
api_type: COM
f1_keywords: EBindPolicyLevels
helpviewer_keywords: EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e55fdb58129cd530bb63f26fab0be471b133d62f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ebindpolicylevels-enumeration"></a>Перечисление EBindPolicyLevels
Предоставляет флаги, чтобы задать уровень, на котором следует применять или изменять политику сборки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Описание|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|Включение применения политики на уровне администратора.|  
|`ePolicyLevelApp`|Включение применения политики на уровне приложения.|  
|`ePolicyLevelHost`|Включение применения политики на уровне узла.|  
|`ePolicyLevelNone`|Задает флаги не уровня политики.|  
|`ePolicyLevelPublisher`|Включение применения политики на уровне издателя.|  
|`ePolicyLevelRetargetable`|Указывает, что политика должна быть применимо на уровнях переменной.|  
|`ePolicyPortability`|Указывает, что политика должен поддерживать переносимости между реализациями сборки платформы .NET Framework. В разделе [ \<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) элемент файла конфигурации.|  
|`ePolicyUnifiedToCLR`|Указывает, что политика должна соответствовать политике среды common language runtime (CLR).|  
  
## <a name="remarks"></a>Примечания  
 Это перечисление передается методам [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) интерфейс для выполнения изменений в политике приложения.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** MSCorEE.h  
  
 **Библиотека:** MSCorEE.dll  
  
 **Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Iclrassemblyidentitymanager-интерфейс](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [Перечисления размещения](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
