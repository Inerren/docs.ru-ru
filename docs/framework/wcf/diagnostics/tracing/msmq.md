---
title: MSMQ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15be4b6bfb84a0aa843e3d62861a9195e125a04e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="msmq"></a>MSMQ
В приложениях MSMQ никакие дополнительные действия не передаются из очереди канала в MSMQ и обратно.  
  
 Кроме того, в рамках трассировки очереди канала во время операции Send отслеживаются идентификатор сообщения MSMQ, идентификатор сообщения SOAP (а также идентификатор действия, если он существует).  
  
 Идентификатор сообщения MSMQ, идентификатор сообщения SOAP (а также идентификатор действия, если он существует) отслеживаются в рамках трассировки очереди канала во время операции Receive.  
  
 Необходимые действия по передаче во время операции Receive выполняются так же, как при любом другом транспорте (получение данных -> обработка сообщения -> операция).
