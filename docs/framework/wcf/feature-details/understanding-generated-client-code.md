---
title: "Основные сведения о созданном коде клиента"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 935f3fe168ebafd7a62c54d2aec1c8336a31a54a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="understanding-generated-client-code"></a>Основные сведения о созданном коде клиента
[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) создает код клиента и файл конфигурации клиентского приложения для использования при сборке клиентских приложений. В этом разделе содержатся примеры созданного кода для стандартных сценариев контрактов служб. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] сборке клиентского приложения с помощью созданного кода см. в разделе [WCF Client Overview](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Обзор  
 При использовании [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] для создания типов клиентов [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] для проекта проверки созданного кода клиента обычно не требуется. Если используемая среда разработки не выполняет аналогичные службы, для создания кода клиента, а также для последующего использования этого кода для разработки клиентского приложения можно использовать такое средство, как Svcutil.exe.  
  
 Поскольку Svcutil.exe имеет несколько параметров, способных изменить тип созданной информации, данный раздел не рассматривает все сценарии. Тем не менее, поиск созданного кода включен в следующие задачи:  
  
-   Определение интерфейсов контрактов служб.  
  
-   Определение класса клиента [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .  
  
-   Определение типа данных.  
  
-   Определение контрактов обратного вызова для дуплексных служб.  
  
-   Определение интерфейса канала контракта службы поддержки.  
  
### <a name="finding-service-contract-interfaces"></a>Поиск интерфейсов контрактов служб  
 Чтобы найти интерфейсы, которые моделируют контракты служб, необходимо искать интерфейсы, отмеченные атрибутом <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>. Зачастую этот атрибут сложно найти при быстром прочтении из-за наличия других атрибутов и явных свойств, установленных на сам атрибут. Не следует забывать, что интерфейс контракта службы и интерфейс контракта клиента - это разные типы интерфейса. В следующем примере кода показан исходный контракт службы.  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 В следующем примере кода показан тот же контракт службы, созданный Svcutil.exe.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Можно использовать созданный интерфейс контракта службы наряду с классом <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> для создания объекта канала [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], с помощью которого вызываются операции службы. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Как: использование ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).  
  
### <a name="finding-wcf-client-classes"></a>Поиск классов клиента WCF  
 Чтобы найти класс клиента [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], реализующий необходимый контракт службы, следует искать расширение класса <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, параметром типа в котором является интерфейс контракта службы, который был только что найден и который расширяет этот интерфейс. Следующий пример кода иллюстрирует класс <xref:System.ServiceModel.ClientBase%601> типа `ISampleService`.  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Класс клиента [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] можно использовать путем создания его нового экземпляра и вызова методов его реализации. Эти методы вызывают операцию службы, для взаимодействия с которой они разработаны и сконфигурированы. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Общие сведения о клиенте WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
> [!NOTE]
>  При создании средством SvcUtil.exe класса клиента WCF к классу клиента добавляется <xref:System.Diagnostics.DebuggerStepThroughAttribute> для предотвращения пошагового перебора элементов класса клиента WCF отладчиками.  
  
### <a name="finding-data-types"></a>Поиск типа данных  
 Основным способом поиска данных в созданном коде является идентификация имени типа, заданного в контракте, и поиск в коде объявления этого типа. Например, следующий контракт задает, что метод `SampleMethod` может возвращать ошибку SOAP типа `microsoft.wcf.documentation.SampleFault`.  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 Поиск `SampleFault` определяет местонахождение следующего объявления типа.  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 В этом случае тип данных представляет собой тип сведений, вызванный конкретным исключением со стороны клиента <xref:System.ServiceModel.FaultException%601> , где параметром типа сведений является `microsoft.wcf.documentation.SampleFault`. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] типах данных см. в разделе [Specifying Data Transfer in Service Contracts](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] обработке исключений в клиентских приложениях см. в разделе [Sending and Receiving Faults](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>Поиск контрактов обратного вызова для дуплексных служб  
 Если определяется местоположение контракта службы, для которого интерфейс контракта задает значение свойства <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType>, то этот контракт задает дуплексный контракт. Дуплексные контракты требуют, чтобы клиентское приложение создавало класс обратного вызова, реализующий контракт обратного вызова, и передавало экземпляр этого класса в <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> или <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>, которые используются для общения со службой. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]дуплексных клиентах см. в разделе [как: службы доступа с дуплексным контрактом](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).  
  
 Следующий контракт задает контракт обратного вызова типа `SampleDuplexHelloCallback`.  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 Поиск этого контракта обратного вызова определяет местоположение следующего интерфейса, который должен быть реализован в клиентском приложении.  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a>Поиск интерфейсов каналов контрактов служб  
 При использовании класса <xref:System.ServiceModel.ChannelFactory> с интерфейсом контракта службы следует перейти к интерфейсу <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>, чтобы явно открыть, закрыть канал или прервать его работу. Для упрощения работы средство Svcutil.exe создает также вспомогательный интерфейс, реализующий и интерфейс контракта службы, и интерфейс <xref:System.ServiceModel.IClientChannel> , чтобы можно было взаимодействовать с инфраструктурой клиентских каналов без переходов. В следующем коде показано определение вспомогательного клиентского канала, который реализует указанный выше контракт службы.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о клиентах WCF](../../../../docs/framework/wcf/wcf-client-overview.md)
