---
title: "Безопасность транспорта с проверкой подлинности с использованием сертификатов"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
caps.latest.revision: "20"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: abff650bd7c0e613524e4903cc754b7ff4200328
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="transport-security-with-certificate-authentication"></a>Безопасность транспорта с проверкой подлинности с использованием сертификатов
В этом разделе рассматривается проверка подлинности сервера и клиента при использовании безопасности транспорта с помощью сертификатов X.509. Дополнительные сведения о X.509 см. [сертификаты открытого ключа X.509](http://msdn.microsoft.com/library/bb540819\(VS.85\).aspx). Сертификаты должны быть выданы центром сертификации, который часто сторонним издателем сертификатов. В домене Windows Server для выдачи сертификатов клиентским компьютерам домена можно использовать службу сертификации Active Directory. Дополнительные сведения см. [служб сертификатов Windows 2008 R2](http://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409). В этом сценарии служба размещена в службах IIS, которые используют протокол SSL. В службе задано использование сертификата SSL (X.509), чтобы клиенты могли проверять подлинность сервера. В клиенте также задано использование сертификата X.509, что позволяет службе проверять подлинность клиента. Клиент должен доверять сертификату сервера, а сервер ― сертификату клиента. Фактический механизм проверки подлинности друг друга службой и клиентом в данном разделе не обсуждается. Дополнительные сведения см. [цифровой подписи в Википедии](http://go.microsoft.com/fwlink/?LinkId=253157).  
  
 В этом сценарии реализуется шаблон обмена сообщениями «запрос-ответ», показанный на следующей схеме.  
  
 ![Безопасная передача с помощью сертификатов](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]с помощью сертификата со службой, в разделе [работа с сертификатами](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) и [как: Настройка порта с SSL-сертификата](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md). В следующей таблице описываются различные особенности этого сценария.  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Режим безопасности|Transport|  
|Взаимодействие|С существующими службами и клиентами веб-служб.|  
|Проверка подлинности (сервера)<br /><br /> Проверка подлинности (клиента)|Да (с использованием SSL-сертификата)<br /><br /> Да (с использованием сертификата X.509)|  
|Целостность данных|Да|  
|Конфиденциальность данных|Да|  
|Transport|HTTPS|  
|Привязка|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a>Настройка службы  
 Поскольку в этом сценарии служба размещается в службах IIS, он настраивается с помощью файла web.config. В следующем примере содержимого файла web.config показано, как настроить в <xref:System.ServiceModel.WSHttpBinding> использование безопасности транспорта и учетных данных клиента X.509.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <protocolMapping>  
      <add scheme="https" binding="wsHttpBinding" />  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttp binding with Transport security mode and clientCredentialType as Certificate -->  
        <binding>  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>              
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>            
           <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="configure-the-client"></a>Настройка клиента  
 Настроить клиент можно в коде или в файле app.config. В следующем примере показано, как настроить клиент в коде.  
  
```vb  
// Create the binding.  
WSHttpBinding myBinding = new WSHttpBinding();  
myBinding.Security.Mode = SecurityMode.Transport;  
myBinding.Security.Transport.ClientCredentialType =  
   HttpClientCredentialType.Certificate;  
  
// Create the endpoint address. Note that the machine name   
// must match the subject or DNS field of the X.509 certificate  
// used to authenticate the service.   
EndpointAddress ea = new  
   EndpointAddress("https://localhost/CalculatorService/service.svc");  
  
// Create the client. The code for the calculator   
// client is not shown here. See the sample applications  
// for examples of the calculator code.  
CalculatorClient cc =  
   new CalculatorClient(myBinding, ea);  
  
// The client must specify a certificate trusted by the server.  
cc.ClientCredentials.ClientCertificate.SetCertificate(  
    StoreLocation.CurrentUser,  
    StoreName.My,  
    X509FindType.FindBySubjectName,  
    "contoso.com");  
  
// Begin using the client.  
Console.WriteLine(cc.Add(100, 1111));  
//...  
cc.Close();  
```  
  
 Также можно настроить клиент в файле App.config, как показано в следующем примере:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address=" https://localhost/CalculatorService/service.svc "   
                behaviorConfiguration="endpointCredentialBehavior"  
                binding="wsHttpBinding"   
                bindingConfiguration="Binding1"   
                contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="contoso.com"  
                               storeLocation="CurrentUser"  
                               storeName="My"  
                               x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as Certificate -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
  
<startup><supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.0"/></startup></configuration>  
```  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о безопасности](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Модель безопасности для Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
