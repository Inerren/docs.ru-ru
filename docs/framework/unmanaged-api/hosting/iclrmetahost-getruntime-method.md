---
title: "Метод ICLRMetaHost::GetRuntime"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.GetRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type: apiref
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6ebfa1af4b824f4fcd4247cd7d0a667488f3e3ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostgetruntime-method"></a>Метод ICLRMetaHost::GetRuntime
Возвращает [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) интерфейс, который соответствует определенной версии среды common language runtime (CLR). Этот метод заменяет [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) функция, используемая с [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) флаг.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in, REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pwzVersion`  
 [in] Версии платформы .NET Framework компиляции, хранятся в метаданных в формате «v*A*. *B*[. *X*]». *Объект*, *B*, и *X* — десятичные числа, соответствуют основной номер версии, дополнительный номер версии и номер сборки.  
  
> [!NOTE]
>  Этот параметр должно соответствовать имени каталога для версии платформы .NET Framework, как оно отображается в списке C:\Windows\Microsoft.NET\Framework или C:\Windows\Microsoft.NET\Framework64.  
  
 Примеры значений: «v1.0.3705», «v1.1.4322», «v2.0.50727» и «v4.0. *X*», где *X* зависит от номера установленного построения. Префикс «v» является обязательным.  
  
 `riid`  
 [in] Идентификатор для нужного интерфейса. В настоящее время единственным допустимым значением для этого параметра — IID_ICLRRuntimeInfo.  
  
 `ppRuntime`  
 [out] Указатель на [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) интерфейс, используемый для запрошенной среды выполнения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.  
  
|HRESULT|Описание|  
|-------------|-----------------|  
|S_OK|Метод завершился успешно.|  
|E_POINTER|`pwzVersion` или `ppRuntime` равно null.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод постоянно взаимодействует с устаревшими интерфейсами, таких как [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) и устаревшими функциями, такие как устаревшие `CorBindTo*` функции (см. [устаревшие функции среды CLR размещение](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) в API размещения платформы .NET Framework 2.0). То есть являются видимыми для нового API среды выполнения, загруженные со старым API и являются видимыми для предыдущих версий API среды выполнения, загруженные с новым API. .  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** MetaHost.h  
  
 **Библиотека:** включена как ресурс в MSCorEE.dll  
  
 **Версии платформы .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [ICLRMetaHost-интерфейс](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [Интерфейсы размещения устаревшие CLR и Coclasses](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 [Интерфейсы размещения CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [Устаревшие функции размещения CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [Размещение](../../../../docs/framework/unmanaged-api/hosting/index.md)
