---
title: "Балансировка нагрузки"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 699a770e1ff1ec8cebf904a72338f400236b737a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="load-balancing"></a>Балансировка нагрузки
Один из способов повышения производительности приложений [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] заключается в масштабировании и развертывании приложений на ферме серверов с балансировкой нагрузки. Нагрузку баланса для приложений [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] можно осуществлять с помощью стандартных методов подсистемы балансировки нагрузки, в том числе с использованием ПО для балансировки сетевой нагрузки Windows и аппаратных средств балансировки нагрузки.  
  
 В следующих разделах рассматриваются вопросы балансировки нагрузки приложений [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], построенных с использованием различных предоставляемых системой привязок.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Балансировка нагрузки с базовой привязкой HTTP  
 С точки зрения балансировки нагрузки приложения [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], которые используют <xref:System.ServiceModel.BasicHttpBinding> для обмена данными, не отличаются от других стандартных типов сетевого HTTP-трафика (статических HTML-страниц, страниц ASP.NET или веб-служб ASMX). Каналы [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], использующие эту привязку, по сути являются каналами без запоминания состояния и завершают свои соединения, когда закрывается канал. Поэтому привязка <xref:System.ServiceModel.BasicHttpBinding> хорошо работает с имеющимися методами балансировки нагрузки HTTP.  
  
 По умолчанию <xref:System.ServiceModel.BasicHttpBinding> отправляет заголовок HTTP подключения в сообщениях со значением `Keep-Alive`, которое позволяет клиентам устанавливать устойчивые подключения к службам, которые поддерживают их. Такая конфигурация увеличивает пропускную способность, потому что ранее установленные подключения можно повторно использовать для отправки новых сообщений одному и тому же серверу. Однако повторное использований подключений может привести к тому, что клиенты будут слишком сильно связаны с конкретным сервером фермы балансировки нагрузки, что приведет к снижению эффективности балансировки нагрузки за счет равномерного распределения запросов между серверами фермы. Если такое поведение является нежелательным, можно на сервере отключить заголовок `Keep-Alive`, присвоив свойству <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> значение <xref:System.ServiceModel.Channels.CustomBinding> или пользовательскую привязку <xref:System.ServiceModel.Channels.Binding>. В следующем примере показано, как добиться этого с помощью конфигурации.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
 <system.serviceModel>  
  <services>  
   <service   
     name="Microsoft.ServiceModel.Samples.CalculatorService"  
     behaviorConfiguration="CalculatorServiceBehavior">  
     <host>  
      <baseAddresses>  
       <add baseAddress="http://localhost:8000/servicemodelsamples/service"/>  
      </baseAddresses>  
     </host>  
    <!-- configure http endpoint, use base address provided by host  
         And the customBinding -->  
     <endpoint address=""  
           binding="customBinding"  
           bindingConfiguration="HttpBinding"   
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   </service>  
  </services>  
  
  <bindings>  
    <customBinding>  
  
    <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
      <binding name="HttpBinding" keepAliveEnabled="False"/>  
  
    </customBinding>  
  </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 При использовании упрощенной конфигурации, реализованной в [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], можно обеспечить такой же режим работы за счет использования следующей упрощенной конфигурации.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
 <system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="customBinding" />  
    </protocolMapping>  
    <bindings>  
      <customBinding>  
  
      <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
        <binding keepAliveEnabled="False"/>  
  
      </customBinding>  
    </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] о конечных точках по умолчанию, привязках и режимах работы см. в разделах [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) и [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a>Балансировка нагрузки с привязкой WSHttp и привязкой WSDualHttp  
 Для привязок <xref:System.ServiceModel.WSHttpBinding> и <xref:System.ServiceModel.WSDualHttpBinding> можно обеспечить балансировку нагрузки, используя для этого методы балансировки нагрузки HTTP, реализуемые путем внесения некоторых изменений в конфигурацию привязки по умолчанию.  
  
-   Отключите установление контекста безопасности. Для этого присвойте свойству <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> привязки <xref:System.ServiceModel.WSHttpBinding> значение `false`. Кроме того, если требуются сеансов безопасности, возможна для использования сеансов безопасности с отслеживанием состояния, как описано в [безопасные сеансы](../../../docs/framework/wcf/feature-details/secure-sessions.md) раздела. Сеансы безопасности с отслеживанием состояния позволяют службе не учитывать состояние, потому что все сведения о состоянии сеанса безопасности передаются с каждым запросом в рамках маркера безопасности защиты. Обратите внимание, что для включения сеансов безопасности с отслеживанием состояния необходимо использовать привязку <xref:System.ServiceModel.Channels.CustomBinding> или определенную пользователем привязку <xref:System.ServiceModel.Channels.Binding>, поскольку необходимые параметры конфигурации не доступны в привязках <xref:System.ServiceModel.WSHttpBinding> и <xref:System.ServiceModel.WSDualHttpBinding>, которые предоставляются системой.  
  
-   Не используйте надежные сеансы. Эта функция отключена по умолчанию.  
  
## <a name="load-balancing-the-nettcp-binding"></a>Балансировка нагрузки привязки Net.TCP  
 Балансировку нагрузки привязки <xref:System.ServiceModel.NetTcpBinding> можно осуществлять с помощью методов балансировки нагрузки уровня протокола IP. Однако для уменьшения времени задержки подключений привязка <xref:System.ServiceModel.NetTcpBinding> по умолчанию объединяет TCP-подключения. Такая оптимизация противоречит базовому механизму балансировки нагрузки. Основным параметром конфигурации, используемым для оптимизации <xref:System.ServiceModel.NetTcpBinding>, является время ожидания аренды, которое входит в настройки пула подключений. В результате объединения клиентских подключений в пул эти подключения оказываются связанными с конкретными серверами фермы. По мере увеличения времени существования таких подключений (этот показатель зависит от значения времени ожидания аренды) распределение нагрузки между различными серверами фермы становится несбалансированным. В результате среднее время одного вызова увеличивается. Поэтому при использовании привязки <xref:System.ServiceModel.NetTcpBinding> с балансировкой нагрузки следует рассмотреть возможность уменьшения используемого привязкой времени ожидания аренды по умолчанию. Для начала использования балансировки нагрузки можно установить время ожидания аренды равным 30 секундам, хотя оптимальное значение будет зависеть от конкретного приложения. Дополнительные сведения о времени ожидания аренды канала и другие квоты транспорта см. в разделе [квоты транспорта](../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
 Для достижения максимальной производительности при балансировке нагрузки рекомендуется использовать <xref:System.ServiceModel.NetTcpSecurity> (<xref:System.ServiceModel.SecurityMode.Transport> или <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).  
  
## <a name="see-also"></a>См. также  
 [Рекомендации по размещению в службах IIS](../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
