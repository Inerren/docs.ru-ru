---
title: "Функция GetCORSystemDirectory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetCORSystemDirectory
helpviewer_keywords: GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 802e9a7bd4e6caedd657a8e8cf0132d75b4cbc2e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="getcorsystemdirectory-function"></a>Функция GetCORSystemDirectory
Возвращает каталог установки среды common language runtime (CLR), который загружается процесс. Каталог установки — полное имя, например, «c:\windows\microsoft.net\framework\v1.0.3705».  
  
 Эта функция устарела. Он заменен [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) метода [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a>Параметры  
 `pbuffer`  
 [out] Буфер, в котором среда выполнения возвращает строка, содержащая полное имя каталога установки для среды выполнения, который загружается в процесс. Если среда выполнения еще не был загружен в процесс, функция возвращает сведения каталога, соответствующего последнюю версию среды выполнения, установленную на компьютере.  
  
 `cchBuffer`  
 [in] Размер в байтах для `pbuffer`.  
  
 `dwLength`  
 [out] Число символов, возвращаемых в `pbuffer`.  
  
## <a name="remarks"></a>Примечания  
  
> [!CAUTION]
>  Не используйте эту функцию в процессы, работающие в среде CLR версии 4. Если на компьютере установлена более ранняя версия среды CLR, эта функция возвращает каталог установки для этой версии.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** MSCorEE.h  
  
 **Библиотека:** MSCorEE.dll  
  
 **Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Устаревшие функции размещения CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
