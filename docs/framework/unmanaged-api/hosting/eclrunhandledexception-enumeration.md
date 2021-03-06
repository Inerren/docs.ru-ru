---
title: "Перечисление EClrUnhandledException"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrUnhandledException
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrUnhandledException
helpviewer_keywords: EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 67787072779e0cb22a339c2d13c972ba36f3ed61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="eclrunhandledexception-enumeration"></a>Перечисление EClrUnhandledException
Описывает доступные параметры для управления исключениями, которые обрабатываются в пользовательском коде.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Описание|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|Указывает, что используется поведение по умолчанию. Процесс завершен.|  
|`eHostDeterminedPolicy`|Указывает, что игнорирует необработанные исключения общеязыковой среды выполнения (CLR) и позволяет узлу определить никаких дальнейших действий.|  
  
## <a name="remarks"></a>Примечания  
 Чтобы указать, что среда CLR аналогично поведению более ранних версий, используйте `eHostDeterminedPolicy` член.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** MSCorEE.h  
  
 **Библиотека:** MSCorEE.dll  
  
 **Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [EClrFailure-перечисление](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [EClrOperation-перечисление](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [Интерфейс ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [Setunhandledexceptionpolicy-метод](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)  
 [IHostPolicyManager-интерфейс](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [Перечисления размещения](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
