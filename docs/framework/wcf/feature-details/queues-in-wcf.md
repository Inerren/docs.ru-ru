---
title: "Очереди в Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d00f8847e64e30b42490f319ea3e1df5e5a1850d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="queues-in-windows-communication-foundation"></a>Очереди в Windows Communication Foundation
В подразделах этого раздела рассматривается поддержка очередей в [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] обеспечивает поддержку организации очереди с помощью технологии службу очередей сообщений (Майкрософт) (ранее носившей название MSMQ) в качестве транспорта и позволяет осуществить следующие сценарии:  
  
-   Слабо связанные приложения. Отправляющие приложения могут отправлять сообщения в очереди без необходимости наличия информации о доступности принимающего приложения для обработки сообщения. Очередь обеспечивает независимость обработки, позволяя отправляющему приложению отправлять сообщения в очередь со скоростью, не зависящей от скорости обработки сообщений принимающими приложениями. Доступность всей системы повышается, если отправка сообщений в очередь тесно не связана с обработкой сообщений.  
  
-   Изоляция сбоев. При выполнении приложения, отправляющего сообщения в очередь или получающего сообщения из очереди, может возникнуть сбой, не влияющий на работу другого приложения. Если, например, произошел сбой принимающего приложения, отправляющее приложение может продолжить отправку сообщений в очередь. После возобновления работы принимающее приложение может обрабатывать такие сообщения из очереди. Изоляция сбоев повышает надежность и доступность всей системы.  
  
-   Распределение нагрузки. Отправляющие приложения могут переполнить принимающие приложения сообщениями. В очередях можно управлять несоответствием между интенсивностью создания сообщений и пропускной способностью приложений, чтобы избежать переполнения принимающего приложения.  
  
-   Операции при отсутствии подключения к сети. Операции отправки, получения и обработки могут прерваться во время передачи данных по сетям с высокой задержкой или сетям с ограниченным доступом, например в случае с мобильными устройствами. В очереди выполнение этих операций продолжится даже при отключении конечных точек. При повторном подключении сообщения из очереди пересылаются в принимающее приложение.  
  
 Чтобы использовать функцию очередей в приложении [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], следует применить одну из стандартных привязок или создать пользовательскую привязку, если ни одна из стандартных привязок не удовлетворяет необходимым требованиям. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]соответствующие стандартные привязки и способ выбора, в разделе [как: обмена сообщениями с конечными точками WCF и приложениями очереди сообщений](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]создании пользовательских привязок см. в разделе [пользовательские привязки](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Содержание  
 [Общие сведения об очередях](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 Обзор понятий очереди сообщений.  
  
 [Очереди в WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 Обзор поддержки очередей службой [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Как: обмен сообщениями с конечными точками WCF в очереди](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 Описание использования класса <xref:System.ServiceModel.NetMsmqBinding> для взаимодействия между клиентом [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] и службой [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Как: обмена сообщениями с конечными точками WCF и приложениями очереди сообщений](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 Описание использования привязки <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> для взаимодействия между приложениями [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] и приложениями очереди сообщений.  
  
 [Группирование сообщений в очереди в сеансе](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 Описание группирования сообщений в очереди для упрощения обработки связанных сообщений одним принимающим приложением.  
  
 [Пакетная обработка сообщений в одну транзакцию](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 Описание объединения сообщений в одну транзакцию.  
  
 [Использование очередей недоставленных сообщений для обработки сбоев при передаче сообщений](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 Описание порядка обработки ошибок передачи и доставки сообщений с помощью очередей недоставленных сообщений и описание процедуры обработки сообщений из очереди недоставленных сообщений.  
  
 [Обработка подозрительных сообщений](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 Описание процедуры обработки подозрительных сообщений (превышено максимальное количество попыток доставки сообщений в принимающее приложение).  
  
 [Различия в возможностях очередей в Windows Vista, Windows Server 2003 и Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 Общие сведения о различиях функций очереди [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] в [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] и [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
 [Защита сообщений с использованием безопасности транспорта](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 Описание способов защиты сообщений в очереди с помощью безопасности транспорта.  
  
 [Защита сообщений с помощью безопасности сообщений](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 Описание способов защиты сообщений в очереди с помощью безопасности сообщения.  
  
 [Устранение неполадок обмена сообщениями в очереди](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 Описание способов устранения общих проблем, связанных с организацией очереди.  
  
 [Советы и рекомендации по взаимодействию с использованием очередей](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 Рекомендации по применению взаимодействия с использованием очередей [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Очереди сообщений](http://msdn.microsoft.com/en-us/ff917e87-05d5-478f-9430-0f560675ece1)
