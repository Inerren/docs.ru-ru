---
title: "Интерфейс IGCThreadControl"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCThreadControl
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCThreadControl
helpviewer_keywords: IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 66afef7dec0637e98249838ae06ae6f1161df3f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="788bd-102">Интерфейс IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="788bd-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="788bd-103">Предоставляет методы для участия в планировании потоков, которые в противном случае были бы заблокированы для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="788bd-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="788bd-104">Методы</span><span class="sxs-lookup"><span data-stu-id="788bd-104">Methods</span></span>  
  
|<span data-ttu-id="788bd-105">Метод</span><span class="sxs-lookup"><span data-stu-id="788bd-105">Method</span></span>|<span data-ttu-id="788bd-106">Описание</span><span class="sxs-lookup"><span data-stu-id="788bd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="788bd-107">Метод SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="788bd-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="788bd-108">Уведомляет узел, что среда выполнения возобновляет выполнение после сборки мусора или по другой причине.</span><span class="sxs-lookup"><span data-stu-id="788bd-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="788bd-109">Метод SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="788bd-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="788bd-110">Уведомляет узел, что среда выполнения начинает приостановку потока для сборки мусора или по другим причинам.</span><span class="sxs-lookup"><span data-stu-id="788bd-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="788bd-111">Threadisblockingforsuspension-метод</span><span class="sxs-lookup"><span data-stu-id="788bd-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="788bd-112">Уведомляет узел, что вызывающий поток заблокирован, возможно, для сборки мусора или по другой причине.</span><span class="sxs-lookup"><span data-stu-id="788bd-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="788bd-113">Требования</span><span class="sxs-lookup"><span data-stu-id="788bd-113">Requirements</span></span>  
 <span data-ttu-id="788bd-114">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="788bd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="788bd-115">**Заголовок:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="788bd-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="788bd-116">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="788bd-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="788bd-117">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="788bd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="788bd-118">См. также</span><span class="sxs-lookup"><span data-stu-id="788bd-118">See Also</span></span>  
 [<span data-ttu-id="788bd-119">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="788bd-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)