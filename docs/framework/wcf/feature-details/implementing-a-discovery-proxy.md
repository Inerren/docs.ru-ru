---
title: "Реализация прокси-сервера обнаружения"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 98affacf611ad31c7c3f8a93ff5793279a42a128
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="implementing-a-discovery-proxy"></a>Реализация прокси-сервера обнаружения
В данном разделе приводятся инструкции по реализации прокси-сервера обнаружения. Прокси-сервер обнаружения - это автономная служба, содержащая репозиторий служб. Клиенты могут выполнять запросы к прокси-серверу обнаружения, чтобы найти обнаружимые службы, доступные серверу. Метод заполнения прокси-сервера службами определяется разработчиком. Например, прокси-сервер обнаружения может подключаться к существующему репозиторию служб и сделать эту информацию обнаружимой, администратор может при помощи API управления добавить обнаружимые службы к прокси-серверу, а прокси-сервер обнаружения может при помощи функции объявлений обновить свой внутренний кэш.  
  
 Реализация WCF обеспечивает базовые классы, которые позволят легко создавать прокси-сервер. Эти API-интерфейсы можно использовать для создания прокси-сервера обнаружения поверх существующего репозитория.  
  
 Используемый здесь прокси-сервер обнаружения похож на любую другую службу WCF в том, что можно сделать прокси-сервер обнаруживаемым и позволить клиентам находить его конечные точки.  
  
## <a name="in-this-section"></a>Содержание  
 [Как: реализация прокси-сервера обнаружения](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 Реализация прокси-сервера обнаружения.  
  
 [Как: реализовать Обнаружимую службу, которая регистрирует с прокси-сервера обнаружения](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 Описано, как реализовать обнаружимую службу [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], которая регистрируется в прокси-сервере обнаружения.  
  
 [Как: реализовать клиентское приложение, которое использует прокси-сервер обнаружения для поиска службы](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 Описывает, как реализовать клиентское приложение [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], которое при помощи прокси-сервера обнаружения ищет службы.  
  
 [Как: тестирования прокси-сервера обнаружения](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 Описывает, как проверить код, приведенный в предыдущих трех разделах.  
  
## <a name="see-also"></a>См. также  
 [Обнаружение WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [Как: программно добавить возможность обнаружения службы WCF и клиент](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
