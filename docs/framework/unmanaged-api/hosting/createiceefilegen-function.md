---
title: "Функция CreateICeeFileGen"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type: COM
f1_keywords: CreateICeeFileGen
helpviewer_keywords: CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9162da1b48348da745f8616b5cc643bf3dee97fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="createiceefilegen-function"></a>Функция CreateICeeFileGen
Создает [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) объекта.  
  
 Эта функция рекомендуется к использованию в [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ceeFileGen`  
 [out] Указатель на адрес нового `ICeeFileGen` объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Этот метод возвращает стандартные коды ошибок COM.  
  
## <a name="remarks"></a>Примечания  
 `ICeeFileGen` Объект используется для создания общего языка среды CLR переносимого исполняемого (PE) файлов.  
  
 Вызовите [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) функции для уничтожения `ICeeFileGen` объекта после завершения.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** ICeeFileGen.h  
  
 **Библиотека:** MSCorPE.dll  
  
 **Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Устаревшие функции размещения CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
