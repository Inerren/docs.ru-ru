---
title: "Пользовательские привязки"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45945fb07f7d1807674453296f7c5e62c829a401
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="custom-bindings"></a>Пользовательские привязки
Класс <xref:System.ServiceModel.Channels.CustomBinding> можно использовать, когда ни одна из системных привязок не соответствует требованиям службы. Все привязки создаются из упорядоченных наборов элементов привязки. Пользовательские привязки можно создавать из набора предоставляемых системой элементов привязки или в них можно включать определяемые пользователем элементы привязки. Пользовательские элементы привязки можно применять, например, для использования в конечной точке службы новых транспортов или кодировщиков. Рабочие примеры см. в разделе [пользовательские привязки образцы](http://msdn.microsoft.com/en-us/657e8143-beb0-472d-9cfe-ed1a19c2ab08). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
## <a name="construction-of-a-custom-binding"></a>Создание пользовательской привязки  
 Пользовательские привязки создаются с использованием одного из конструкторов <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> из коллекции элементов привязки, которые располагаются в определенном порядке.  
  
-   Вверху расположен необязательный класс <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, который разрешает поток транзакций.  
  
-   Далее следует необязательный класс <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>, который обеспечивает сеанс и механизмы сортировки, в соответствии со спецификацией WS-ReliableMessaging. Сеанс может включать посредников SOAP и транспорта.  
  
-   Далее следует необязательный класс <xref:System.ServiceModel.Channels.SecurityBindingElement>, который предоставляет функции безопасности, такие как авторизация, проверка подлинности, защита и конфиденциальность.  
  
-   Далее следует необязательный класс <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>, который обеспечивает возможность двусторонней дуплексной связи с транспортным протоколом, изначально не поддерживающим дуплексную связь, таким как HTTP.  
  
-   Далее следует необязательный класс <xref:System.ServiceModel.Channels.OneWayBindingElement>), который обеспечивает одностороннюю связь.  
  
-   Далее следует обязательный элемент привязки безопасности потока, который может быть одним из следующих.  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   Далее следует обязательный элемент привязки для кодирования сообщений. Можно использовать свой кодировщик транспорта или одну из трех привязок кодировки сообщений:  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
 Внизу расположен обязательный элемент транспорта. Можно использовать свой транспорт или один из следующих элементов привязки транспорта, предоставляемых [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]:  
  
-   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
-   <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
 В следующей таблице приведены сводные данные по параметрам каждого уровня.  
  
|Уровень|Параметры|Обязательно|  
|-----------|-------------|--------------|  
|Транзакции|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Нет|  
|Надежность|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Нет|  
|Безопасность|<xref:System.ServiceModel.Channels.SecurityBindingElement>|Нет|  
|кодировка|Текст, двоичное, механизм оптимизации передачи сообщений (MTOM), пользовательское|Да|  
|Transport|TCP, HTTP, HTTPS, именованные каналы (также называются IPC), одноранговый (P2P), очередь сообщений (также называется MSMQ), пользовательский|Да|  
  
 Кроме того, можно определить собственные элементы привязки и вставить их между любыми из приведенных выше заданных уровней.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о создании конечных точек](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Использование привязок для настройки служб и клиентов](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Привязки, предоставляемые системой](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Как: изменение привязки, предоставляемые системой](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)  
 [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Пользовательская привязка](../../../../docs/framework/wcf/samples/custom-binding.md)
