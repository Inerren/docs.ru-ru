---
title: "Количество подозрительных сообщений из очереди в секунду"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2811cbcca7d4e11465191e5d25b820b4a7b15e4d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="queued-poison-messages-per-second"></a>Количество подозрительных сообщений из очереди в секунду
Имя счетчика: Queued Poison Messages Per Second.  
  
## <a name="description"></a>Описание  
 Количество сообщений, отмеченных как подозрительные транспортом очередей в этой службе в секунду.  
  
 Этот счетчик является счетчиком производительности типа [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), значение которого вычисляется по следующей формуле.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
