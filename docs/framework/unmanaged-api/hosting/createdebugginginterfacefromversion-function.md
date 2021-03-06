---
title: "Функция CreateDebuggingInterfaceFromVersion"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CreateDebuggingInterfaceFromVersion
helpviewer_keywords: CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cc352603ef1c3610edf99f7bdd877c6bb0e5d9fb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="createdebugginginterfacefromversion-function"></a>Функция CreateDebuggingInterfaceFromVersion
Создает [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) объекта на основе указанной версии данных.  
  
 Эта функция устарела в [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Для обеспечения интерфейса для общеязыковой среды выполнения (CLR) 2.0, используйте [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) метод и задайте идентификатор класса CLSID_CLRDebuggingLegacy идентификатор интерфейса IID_ICorDebug. Для получения интерфейса для CLR 4 или более поздней версии, вызовите [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) и задайте идентификатор класса CLSID_CLRDebugging и IID_ICLRDebugging идентификатор интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `iDebuggerVersion`  
 [in] Версия `ICorDebug` , ожидается отладчиком. В разделе [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) перечисления для допустимых значений.  
  
 `szDebuggeeVersion`  
 [in] Общие версию среды CLR, связанный с приложением или процесс для отладки. В разделе [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) или [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) метод сведения о получении этого значения.  
  
 `ppCordb`  
 [out] В расположение, которое получает указатель на `ICorDebug` объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Этот метод возвращает стандартные коды ошибок COM, как определено в файле WinError.h, кроме следующих значений.  
  
|Код возврата|Описание|  
|-----------------|-----------------|  
|S_OK|Метод завершился успешно.|  
|E_INVALIDARG|`szDebuggeeVersion`или `ppCordb` имеет значение null или версия Неверная строка.|  
  
## <a name="remarks"></a>Примечания  
 `szDebuggeeVersion` Параметр сопоставляется соответствующую версию библиотеки MSCorDbi.dll.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** MSCorEE.h  
  
 **Библиотека:** MSCorEE.dll  
  
 **Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Устаревшие функции размещения CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
