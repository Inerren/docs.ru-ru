---
title: "Метод ICorDebugILFrame::CanSetIP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.CanSetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bbb5b0a8038445372b5e404fac554c0726353bf6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframecansetip-method"></a>Метод ICorDebugILFrame::CanSetIP
Возвращает значение HRESULT, указывающее, можно ли безопасно значение указателя инструкций заданное расположение смещения в коде промежуточного языка Майкрософт (MSIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `nOffset`  
 [in] Нужное значение указателя инструкций.  
  
## <a name="remarks"></a>Примечания  
 Используйте `CanSetIP` метод перед вызовом метода [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) метод. Если `CanSetIP` возвращает любой HRESULT, отличных от S_OK, по-прежнему можно вызвать `ICorDebugILFrame::SetIP`, но нет никакой гарантии, что отладчик продолжит выполнение отлаживаемого кода.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl CorDebug, h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
