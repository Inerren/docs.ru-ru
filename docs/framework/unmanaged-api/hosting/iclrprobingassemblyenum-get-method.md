---
title: "Метод ICLRProbingAssemblyEnum::Get"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRProbingAssemblyEnum.Get
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cdd198f7a7a35fe4df371f3a53964b94459fd314
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="iclrprobingassemblyenumget-method"></a>Метод ICLRProbingAssemblyEnum::Get
Возвращает удостоверение сборки по указанному индексу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwIndex`  
 [in] Отсчитываемый от нуля индекс удостоверение сборки для возврата.  
  
 `pwzBuffer`  
 [out] Буфер, содержащий данные идентификации сборки.  
  
 `pcchBufferSize`  
 [in, out] Размер `pwzBuffer` буфера.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
|HRESULT|Описание|  
|-------------|-----------------|  
|S_OK|`Get`успешно возвращен.|  
|ERROR_INSUFFICIENT_BUFFER|`pwzBuffer` слишком мал.|  
|ERROR_NO_MORE_ITEMS|Перечисление не содержит несколько элементов.|  
|ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE|Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.|  
|HOST_E_TIMEOUT|Истекло время ожидания вызова.|  
|HOST_E_NOT_OWNER|Вызывающий объект не является владельцем блокировки.|  
|HOST_E_ABANDONED|Событие было отменено заблокированный поток или ожидал волокон.|  
|E_FAIL|Неизвестная Неустранимая ошибка. Если метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе. Последующие вызовы методов размещения возвращают значение HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Примечания  
 Идентификация по индексу 0 — это идентификатор, соответствующий архитектуре процессора. Удостоверение с индексом 1 — это зависящий от архитектуры сборка промежуточного языка Майкрософт (MSIL). Идентификация по индексу 2 не содержат архитектура сведений.  
  
 `Get`обычно вызывается дважды. Первый вызов предоставляет значение null для `pwzBuffer`и задает `pcchBufferSize` соответствующие размеру `pwzBuffer`. При втором вызове указывается подходящего размера `pwzBuffer`и содержит данные идентификации канонической сборки после завершения.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** MSCorEE.h  
  
 **Библиотека:** включена как ресурс в MSCorEE.dll  
  
 **Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [ICLRProbingAssemblyEnum-интерфейс](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [Iclrassemblyidentitymanager-интерфейс](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
