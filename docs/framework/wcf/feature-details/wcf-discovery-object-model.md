---
title: "Модель объектов обнаружения WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8365a152-eacd-4779-9130-bbc48fa5c5d9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 353c1ce4688442513417ee03bfecd3cee3db3d62
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-discovery-object-model"></a>Модель объектов обнаружения WCF
Обнаружение WCF включает в себя набор типов, обеспечивающих унифицированную модель программирования, которая позволяет создавать службы, доступные для обнаружения во время выполнения, а также клиентов, которые могут находить и использовать их.  
  
## <a name="making-a-service-discoverable-and-finding-services"></a>Включение возможности обнаружения для службы и обнаружения служб  
 Чтобы служба WCF была доступной для обнаружения, добавьте поведение <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> в описание <xref:System.ServiceModel.Description.ServiceDescription> узла службы и задайте конечную точку обнаружения. Если служба настроена для отправки сообщений с объявлениями (путем добавления <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>), то объявление отправляется при открытии и закрытии узла службы.  
  
 Чтобы клиент мог следить за сообщениями службы с объявлениями, он должен разместить службу объявлений и добавить одну или более конечных точек объявлений. Служба объявлений получает сообщения с объявлениями и создает события объявлений.  
  
 Клиент пользуется для поиска доступных служб классом <xref:System.ServiceModel.Discovery.DiscoveryClient>. Приложение клиента создает класс <xref:System.ServiceModel.Discovery.DiscoveryClient>, передавая конечную точку обнаружения, которая указывает, куда следует отправлять сообщения обнаружения. Клиент вызывает метод <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, который отправляет запрос `Probe`. Службы, следящие за сообщениями обнаружения, получают запрос `Probe`. Если служба совпадает с критериями, заданными в `Probe`, то она отправляет сообщение `ProbeMatch` обратно клиенту.  
  
## <a name="object-model"></a>Объектная модель  
 API-интерфейс обнаружения WCF определяет следующие классы:  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementClient>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementService>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryClient>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>  
  
-   <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryProxy>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryService>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryVersion>  
  
-   <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>  
  
-   <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>  
  
-   <xref:System.ServiceModel.Discovery.FindCriteria>  
  
-   <xref:System.ServiceModel.Discovery.FindRequestContext>  
  
-   <xref:System.ServiceModel.Discovery.FindResponse>  
  
-   <xref:System.ServiceModel.Discovery.ResolveCriteria>  
  
-   <xref:System.ServiceModel.Discovery.ResolveResponse>  
  
-   <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>  
  
-   <!--zz <xref:System.ServiceModel.Discovery.ServiceDiscoveryExtension> --> `ServiceDiscoveryExtension`  
  
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
## <a name="announcementclient"></a>AnnouncementClient  
 Класс <xref:System.ServiceModel.Discovery.AnnouncementClient> предоставляет синхронные и асинхронные методы для отправки сообщений с объявлениями. Существует два типа сообщений с объявлениями ― Hello и Bye. Сообщение Hello указывает, что служба стала доступной, а сообщение Bye ― что существующая служба стала недоступной. Разработчик создает экземпляр <xref:System.ServiceModel.Discovery.AnnouncementClient> и передает экземпляр <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> конструктору в качестве параметра.  
  
## <a name="announcementendpoint"></a>AnnouncementEndpoint  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> представляет стандартную конечную точку с заданным контрактом объявления. Используется службой или клиентом для отправки и получения сообщений с объявлениями. По умолчанию класс <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> использует версию протокола WS_Discovery 11.  
  
## <a name="announcementservice"></a>AnnouncementService  
 <xref:System.ServiceModel.Discovery.AnnouncementService> ― системная реализация службы объявлений, которая получает и обрабатывает сообщения с объявлениями. При получении сообщения Hello или Bye экземпляр <xref:System.ServiceModel.Discovery.AnnouncementService> вызывает соответствующий виртуальный метод <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOnlineAnnouncement%2A> или <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOfflineAnnouncement%2A>, который создает события объявлений.  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 Класс <xref:System.ServiceModel.Discovery.DiscoveryClient> используется клиентским приложением для нахождения и разрешения доступных служб. Он предоставляет синхронные и асинхронные методы для нахождения и разрешения служб на основе заданных критериев <xref:System.ServiceModel.Discovery.FindCriteria> и <xref:System.ServiceModel.Discovery.ResolveCriteria> соответственно. Разработчик создает экземпляр <xref:System.ServiceModel.Discovery.DiscoveryClient> и передает экземпляр <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> в качестве параметра конструктора.  
  
 Чтобы найти службу, разработчик вызывает синхронный или асинхронный `Find` метод, который обеспечивает <!--zz <xref:System.ServiceModel.Discription.FindCriteria> --> `FindCriteria` экземпляр, содержащий критерии поиска для использования. Клиент <xref:System.ServiceModel.Discovery.DiscoveryClient> создает сообщение `Probe` с соответствующими заголовками и отправляет запрос поиска. Поскольку в любое время может быть более одного необработанного запроса `Find`, клиент сопоставляет полученные ответы и проверяет ответ. Затем клиент доставляет результаты объекту, вызвавшему операцию `Find`, с помощью метода <xref:System.ServiceModel.Discovery.FindResponse>.  
  
 Чтобы разрешить известную службу, разработчик вызывает синхронный или асинхронный `Resolve` метод, который предоставляет экземпляр <!--zz <xref:System.ServiceModel.ResolveCriteria>--> `ResolveCriteria` , содержащий <xref:System.ServiceModel.EndpointAddress> известной службы. Клиент <xref:System.ServiceModel.Discovery.DiscoveryClient> создает сообщение `Resolve` с соответствующими заголовками и отправляет запрос разрешения. Полученный ответ сопоставляется с необработанными запросами разрешения, и результат доставляется объекту, вызвавшему операцию `Resolve`, при помощи метода <xref:System.ServiceModel.Discovery.ResolveResponse>.  
  
 Если прокси-сервер обнаружения присутствует в сети и <!--zz <xref:System.ServiceModel.Discover.DiscoveryClient> --> `DiscoveryClient` отправляет запрос обнаружения многоканально, прокси-сервер обнаружения может ответить на приветственное сообщение подавления многоадресной рассылки. <!--zz <xref:System.ServiceModel.Discover.DiscoveryClient> --> `DiscoveryClient` Вызывает `ProxyAvailable` событие при получении сообщений Hello в ответ на необработанный `Find` или `Resolve` запросов. Событие `ProxyAvailable` содержит метаданные <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> о прокси-сервере обнаружения. Затем разработчик должен использовать эту информацию для переключения из нерегламентированного режима в управляемый.  
  
## <a name="discoveryendpoint"></a>DiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> представляет стандартную конечную точку с заданным контрактом обнаружения. Используется службой или клиентом для отправки и получения сообщений обнаружения. По умолчанию <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> используется <!--zz <xref:System.ServiceModel.Discovery.DiscoveryMode.Managed>--> `Managed` режим и версию WSDiscovery11 WS-Discovery.  
  
## <a name="discoverymessagesequencegenerator"></a>DiscoveryMessageSequenceGenerator  
 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator> используется для формирования последовательности сообщений <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>, когда служба отправляет сообщения обнаружения или сообщения с объявлениями.  
  
## <a name="discoveryservice"></a>DiscoveryService  
 Абстрактный класс <xref:System.ServiceModel.Discovery.DiscoveryService> реализует базовые функции для получения и обработки сообщений `Probe` и `Resolve`. При получении сообщения `Probe` служба <xref:System.ServiceModel.Discovery.DiscoveryService> создает экземпляр <xref:System.ServiceModel.Discovery.FindRequestContext> на основе входящего сообщения и вызывает виртуальный метод <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A>. При получении сообщения `Resolve` служба <xref:System.ServiceModel.Discovery.DiscoveryService> вызывает виртуальный метод <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginResolve%2A>. Можно наследовать у этого класса для обеспечения реализации пользовательской службы обнаружения.  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  
 Абстрактный класс <xref:System.ServiceModel.Discovery.DiscoveryProxy> реализует базовые функции для получения и обработки сообщений обнаружения и сообщений с объявлениями. Этот класс можно наследовать при реализации пользовательского прокси-сервера обнаружения. При получении сообщения `Probe` через многоадресную рассылку класс <xref:System.ServiceModel.Discovery.DiscoveryProxy> вызывает виртуальный метод `BeginShouldRedirectFind`, чтобы определить, следует ли отправить многоадресное сообщение отмены. Если разработчик решит не отправлять многоадресное сообщение отмены либо если по адресу одноадресной рассылки получено сообщение `Probe`, будет создан экземпляр класса <xref:System.ServiceModel.Discovery.FindRequestContext> на основе входящего сообщения и вызван виртуальный метод `OnBeginFind`. При получении сообщения `Resolve` через многоадресную рассылку класс <xref:System.ServiceModel.Discovery.DiscoveryProxy> вызывает виртуальный метод `ShouldRedirectResolve`, чтобы определить, следует ли отправить многоадресное сообщение отмены. Если разработчик решит не отправлять многоадресное сообщение отмены либо если по адресу одноадресной рассылки получено сообщение `Resolve`, будет создан экземпляр класса <xref:System.ServiceModel.Discovery.ResolveCriteria> на основе входящего сообщения и вызван виртуальный метод `OnBeginResolve`. При получении сообщения Hello или Bye экземпляр <xref:System.ServiceModel.Discovery.DiscoveryProxy> вызывает соответствующий виртуальный метод (`OnBeginOnlineAnnouncement` или `OnBeingOfflineAnnouncement`), который создает события объявлений.  
  
## <a name="discoveryversion"></a>DiscoveryVersion  
 Класс <xref:System.ServiceModel.Discovery.DiscoveryVersion> представляет используемую версию протокола обнаружения.  
  
## <a name="endpointdiscoverybehavior"></a>EndpointDiscoveryBehavior  
 Класс <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> служит для контроля возможности обнаружения конечной точки, указания расширений и дополнительных имен типов контрактов. и областей, связанных с этой конечной точкой. Это поведение добавляется в конечную точку приложения для настройки ее метаданных <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. При добавлении поведения <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> к узлу службы все конечные точки приложения, размещенные узлом службы, по умолчанию получают возможность обнаружения. Разработчик может отключить обнаружение для конкретной конечной точки, задав <!--zz <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enable%2A>--> `Enable` свойства `false`.  
  
## <a name="endpointdiscoverymetadata"></a>EndpointDiscoveryMetadata  
 Класс <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> обеспечивает независимое от версии представление конечной точки, опубликованной службой. Служба содержит адреса конечных точек, URI прослушивания, имена типов контрактов, области, версию метаданных и модули, указанные разработчиком службы. Критерии <xref:System.ServiceModel.Discovery.FindCriteria>, отправляемые клиентом в течение операции `Probe`, сопоставляются с метаданными <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Если критерии совпадут, метаданные <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> будут возвращены клиенту. Адрес конечной точки в <xref:System.ServiceModel.Discovery.ResolveCriteria> сопоставляется с адресом конечной точки <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Если критерии совпадут, метаданные <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> будут возвращены клиенту.  
  
## <a name="findcriteria"></a>FindCriteria  
 Класс <xref:System.ServiceModel.Discovery.FindCriteria> является независимым от версии классом, который используется для указания критериев, используемых при нахождении службы. Класс полностью поддерживает критерии, определенные WS-Discovery, для сопоставления служб. Он также имеет модули, которые разработчики могут использовать для указания пользовательских значений, используемых в течение процесса сопоставления. Разработчик может предоставить критерии завершения для `Find` операцию, указав <!--zz <xref:System.ServiceModel.Discovery.FindCriteria.MaxResult%2A>--> `MaxResult`, который определяет общее количество служб, разработчик выполняет поиск значения или <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>, который является значение, указывающее, как долго клиент ожидает ответы.  
  
## <a name="findrequestcontext"></a>FindRequestContext  
 Класс <xref:System.ServiceModel.Discovery.FindRequestContext> создается службой обнаружения на основе сообщения `Probe`, полученного при запуске клиентом операции `Find`. Класс содержит экземпляр <xref:System.ServiceModel.Discovery.FindCriteria>, заданный клиентом.  
  
## <a name="findresponse"></a>FindResponse  
 Класс <xref:System.ServiceModel.Discovery.FindResponse> возвращается объекту, вызвавшему метод <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, с ответами операции `Find`. Также присутствует в <xref:System.ServiceModel.Discovery.FindCompletedEventArgs>. Содержит коллекцию метаданных <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, которая является коллекцией обнаруженных конечных точек и словарем элементов <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> и <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="resolvecriteria"></a>ResolveCriteria  
 Класс <xref:System.ServiceModel.Discovery.ResolveCriteria> является независимым от версии классом, который используется для указания критериев, используемых при разрешении уже известной службы. Содержит адрес конечной точки известной службы. Разработчик может предоставить критерии завершения для операции разрешения путем указания длительности <xref:System.ServiceModel.Discovery.ResolveCriteria.Duration%2A>, то есть времени, в течение которого клиент ожидает ответов.  
  
## <a name="resolveresponse"></a>ResolveResponse  
 Класс <xref:System.ServiceModel.Discovery.ResolveResponse> возвращается объекту, вызвавшему метод <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A>, с ответом операции `Resolve`. Также присутствует в <xref:System.ServiceModel.Discovery.ResolveCompletedEventArgs>. Содержит экземпляр метаданных <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, которые являются обнаруженными конечными точками, и экземпляр <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="servicediscoverybehavior"></a>ServiceDiscoveryBehavior  
 Класс <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> позволяет разработчику добавлять функцию обнаружения для службы. Это поведение добавляется к <xref:System.ServiceModel.ServiceHost>. Класс <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> просматривает конечные точки приложения, добавленные к узлу службы, и создает коллекцию <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, содержащую конечные точки, доступные для обнаружения. Все конечные точки по умолчанию доступны для обнаружения. Возможность обнаружения определенной конечной точки может быть ограничена за счет добавления к ней поведения <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>. Если конечные точки объявлений добавлены в поведение <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>, то объявление всех точек, которые могут быть обнаружены, отправляется для каждой конечной точки объявления при открытии или закрытии узла службы.  
  
## <a name="servicediscoveryextension"></a>ServiceDiscoveryExtension  
 <!--zz <xref:System.ServiceModel.Discovery.ServiceDiscoveryExtension> --> `ServiceDiscoveryExtension` Класс создается с помощью <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> класса. Конечные точки, которые выполняются обнаруживаемыми можно получить из <!--zz <xref:System.ServiceModel.Discovery.ServiceDiscoveryExtension> --> `ServiceDiscoveryExtension`. Этот класс также используется для реализации пользовательской службы обнаружения.  
  
## <a name="udpannouncementendpoint"></a>UdpAnnouncementEndpoint  
 Класс <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> ― это стандартная точка объявления, которая является предустановленной для объявления через привязку для многоадресной рассылки UDP. По умолчанию класс <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> использует версию WSApril2005 WS_Discovery.  
  
## <a name="udpdiscoveryendpoint"></a>UdpDiscoveryEndpoint  
 Конечная точка <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ― это стандартная конечная точка обнаружения, заранее настроенная для операций обнаружения через привязку для многоадресной рассылки. По умолчанию <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> использует версию WSDiscovery11 WS-Discovery и <!--zz <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.Adhoc>--> `Adhoc` режим.
