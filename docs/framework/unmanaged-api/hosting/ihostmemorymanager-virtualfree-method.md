---
title: "Метод IHostMemoryManager::VirtualFree"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualFree
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 468228101403c7ce3c123401e906e3ccbe301e28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmemorymanagervirtualfree-method"></a>Метод IHostMemoryManager::VirtualFree
Служит в качестве логической программой-оболочкой для соответствующей функции Win32. Реализация Win32 `VirtualFree` освобождает, разблокирует или освобождает и разблокирует диапазон страниц в пределах виртуального адресного пространства вызывающего процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `lpAddress`  
 [in] Указатель на базовый адрес для освобождения страниц виртуальной памяти.  
  
 `dwSize`  
 [in] Размер в байтах, области, чтобы освободить.  
  
 `dwFreeType`  
 [in] Тип операции освобождения.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
|HRESULT|Описание|  
|-------------|-----------------|  
|S_OK|`VirtualFree`успешно возвращен.|  
|ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE|Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.|  
|HOST_E_TIMEOUT|Истекло время ожидания вызова.|  
|HOST_E_NOT_OWNER|Вызывающий объект не является владельцем блокировки.|  
|HOST_E_ABANDONED|Событие было отменено заблокированный поток или ожидал волокон.|  
|E_FAIL|Неизвестная Неустранимая ошибка. Если метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе. Последующие вызовы размещение методы возвращают значение HOST_E_CLRNOTAVAILABLE.|  
|ЗНАЧЕНИЕ HOST_E_INVALIDOPERATION|Была предпринята попытка освободить память, выделенная не через узел.|  
  
## <a name="remarks"></a>Примечания  
 `VirtualFree`Освобождает страницы виртуальной памяти, связанные с `lpAddress` параметр по предыдущим вызовом [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) функции. Пытается освободить память, выделенная через узел не должен возвращать значение HOST_E_INVALIDOPERATION.  
  
 Семантика идентична реализация Win32 `VirtualFree`. Дополнительные сведения см. в документации по платформе Windows.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** MSCorEE.h  
  
 **Библиотека:** включена как ресурс в MSCorEE.dll  
  
 **Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [IHostMemoryManager-интерфейс](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [IHostMalloc-интерфейс](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
