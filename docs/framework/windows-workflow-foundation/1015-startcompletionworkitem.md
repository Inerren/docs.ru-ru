---
title: 1015 - StartCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 44ef71e254a2407b416a0efc4b560bf2f6013a74
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="1015---startcompletionworkitem"></a>1015 - StartCompletionWorkItem
## <a name="properties"></a>Свойства  
  
|||  
|-|-|  
|Идентификатор|1015|  
|Ключевые слова|WFRuntime|  
|Уровень|Verbose|  
|Канал|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Описание  
 Указывает, что выполнение CompletionWorkItem начинается.  
  
## <a name="message"></a>Сообщение  
 Начато выполнение CompletionWorkItem для родительского действия «%1», DisplayName «%2», InstanceId «%3». Завершено действие «%4», DisplayName «%5», InstanceId «%6».  
  
## <a name="details"></a>Подробные сведения  
  
|Имя элемента данных|Тип элемента данных|Описание|  
|--------------------|--------------------|-----------------|  
|ParentActivity|xs:string|Имя типа родительского действия.|  
|ParentDisplayName|xs:string|Отображаемое имя родительского действия.|  
|ParentInstanceId|xs:string|Идентификатор экземпляра родительского действия.|  
|CompletedActivity|xs:string|Имя типа завершенного действия.|  
|CompletedActivityDisplayName|xs:string|Отображаемое имя завершенного действия.|  
|CompletedActivityInstanceId|xs:string|Идентификатор экземпляра завершенного действия.|  
|AppDomain|xs:string|Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.|
