---
title: "Несколько конечных точек по одному ListenUri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8860749430d1c6ec1f9b89c1a9740b836ff28ae9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Несколько конечных точек по одному ListenUri
В этом образце показана служба, в которой размещается несколько конечных точек по одному адресу `ListenUri`. Этот пример построен на [Приступая к работе](../../../../docs/framework/wcf/samples/getting-started-sample.md) , реализующий службу калькулятора.  
  
> [!NOTE]
>  Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.  
  
 Как показано в [несколько конечных точек](../../../../docs/framework/wcf/samples/multiple-endpoints.md) примера службы можно разместить несколько конечных точек, каждая из которых разные адреса и, возможно, также различных привязок. В этом образце показано, что можно разместить несколько конечных точек по одному адресу. Кроме того, в этом образце демонстрируются различия между двумя видами адресов конечной точки службы: `EndpointAddress` и `ListenUri`.  
  
 `EndpointAddress` является логическим адресом службы. Это адрес, по которому отправляются сообщения SOAP. `ListenUri` является физическим адресом службы. В нем содержится информация о порте и адресе, где конечная точка службы фактически прослушивает сообщения на текущем компьютере. В большинстве случаев эти адреса не должны отличаться; если `ListenUri` не указан явно, по умолчанию используется URI из адреса `EndpointAddress` конечной точки. В некоторых случаях, например при настройке маршрутизатора, который может принимать сообщения, адресованные нескольким различным службам, эти адреса полезно различать.  
  
## <a name="service"></a>Служба  
 Служба в образце имеет два контракта: `ICalculator` и `IEcho`. Кроме обычной конечной точки `IMetadataExchange` существуют три конечные точки приложения, как показано в следующем коде.  
  
```xml  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.ICalculator"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:OtherEcho"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
```  
  
 Все три конечные точки размещаются по одному адресу `ListenUri` и используют одну привязку (`binding`) - конечные точки, расположенные по одному адресу `ListenUri`, должны иметь одну и ту же привязку, поскольку они совместно используют один стек каналов, который прослушивает сообщения в расположении, определенном данным физическим адресом на компьютере. Адрес (`address`) каждой конечной точки является универсальным именем ресурса (URN); несмотря на то что обычно адреса представляют физические расположения, фактически, адресом может быть URI любого вида, поскольку адрес используется для сопоставления и фильтрации, как показано в данном образце.  
  
 Поскольку все три конечные точки совместно используют один `ListenUri`, при поступлении сообщения по этому адресу [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] необходимо решить, для какой конечной точки оно предназначено. Каждая конечная точка имеет фильтр сообщений, состоящий из двух частей: фильтр адресов и фильтр контрактов. Фильтр адресов сопоставляет значение поля `To` сообщения SOAP с адресом конечной точки службы. Например, только сообщения с адресацией `To "Urn:OtherEcho"` являются кандидатами для третьей конечной точки данной службы. Фильтр контрактов соответствует действиям, связанным с операциями конкретного контракта. Например, сообщения с действием `IEcho`. `Echo` сопоставляется с фильтрами контрактов второй и третьей конечной точки данной службы, поскольку обе эти конечные точки размещают контракт `IEcho`.  
  
 Таким образом, комбинация фильтра адресов и фильтра контрактов позволяет направлять каждое сообщение, поступающее по адресу `ListenUri` данной службы, в правильную конечную точку. Третья конечная точка отличается от других двух, поскольку она принимает сообщения, отправляемые по другому адресу из других конечных точек. Первая и вторая конечные точки отличаются друг от друга своими контрактами (действием исходящего сообщения).  
  
## <a name="client"></a>Клиент  
 Как и в случае конечных точек сервера у конечных точек клиента имеется два адреса. Логический адрес на сервере и на клиенте называется `EndpointAddress`. Однако на сервере физический адрес называется `ListenUri`, в то время как на клиенте он называется `Via`.  
  
 Аналогично серверу по умолчанию эти два адреса одинаковы. Для задания на клиенте адреса `Via`, отличающегося от адреса конечной точки, используется `ClientViaBehavior`:  
  
```  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 Как обычно, адрес поступает из файла конфигурации клиента, созданного с помощью средства Svcutil.exe. Адрес `Via` (который соответствует `ListenUri` службы) не отображается в метаданных службы, таким образом, эту информацию необходимо передать клиенту вне диапазона (аналогично адресу метаданных службы).  
  
 В этом образце клиент отправляет сообщения каждой из трех конечных точек приложения, чтобы показать, что он может взаимодействовать со всеми тремя конечными точками (и различать их), даже если они имеют один и тот же адрес `Via`.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Настройка, сборка и выполнение образца  
  
1.  Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Для запуска образца в конфигурации одного или нескольких компьютерах, следуйте инструкциям в [выполнение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  В случае нескольких компьютеров в файле Client.cs необходимо заменить localhost именем компьютера службы.  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите на страницу [Примеры Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) , чтобы скачать все примеры [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
  
## <a name="see-also"></a>См. также
