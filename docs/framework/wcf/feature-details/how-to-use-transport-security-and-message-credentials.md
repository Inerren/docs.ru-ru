---
title: "Практическое руководство. Использование средств обеспечения безопасности транспорта и учетных данных сообщения"
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
helpviewer_keywords: TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: e29ae3a0374f6ee027180835629eacceaa928d2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-transport-security-and-message-credentials"></a>Практическое руководство. Использование средств обеспечения безопасности транспорта и учетных данных сообщения
Механизм защиты службы с помощью учетных данных транспорта и учетных данных сообщения использует лучшие возможности режимов безопасности транспорта (TLS) и сообщений (MLS) в [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. В общих словах, TLS обеспечивает целостность и конфиденциальность, а MLS предоставляет различные учетные данные, которые невозможно использовать в строгих механизмах обеспечения безопасности транспорта. В этом разделе приведены основные этапы реализации транспорта с учетными данными сообщения с помощью привязок <xref:System.ServiceModel.WSHttpBinding> и <xref:System.ServiceModel.NetTcpBinding>. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Настройка режима безопасности, в разделе [как: режим безопасности](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
 При задании режима безопасности`TransportWithMessageCredential` транспорт определяет фактический механизм, обеспечивающий безопасность на транспортном уровне. В случае HTTP таким механизмом является SSL по HTTP (HTTPS); в случае TCP таким механизмом является SSL по TCP или Windows.  
  
 Если транспортом является HTTP (используется <xref:System.ServiceModel.WSHttpBinding>), SSL по HTTP обеспечивает безопасность на транспортном уровне. В этом случае необходимо задать для компьютера, на котором размещена служба, SSL-сертификат, привязанный к порту, как показано далее в этом разделе.  
  
 Если транспортом является TCP (используется <xref:System.ServiceModel.NetTcpBinding>), по умолчанию безопасность на транспортном уровне обеспечивается механизмом безопасности Windows или SSL по TCP. При использовании SSL по TCP необходимо указать сертификат с помощью метода <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>, как показано далее в этом разделе.  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a>Использование привязки WSHttpBinding с сертификатом для обеспечения безопасности транспорта (в коде)  
  
1.  Воспользуйтесь средством HttpCfg.exe для привязки SSL-сертификата к порту на компьютере. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Как: Настройка порта с SSL-сертификата](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
2.  Создайте экземпляр класса <xref:System.ServiceModel.WSHttpBinding> и задайте для свойства <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> значение <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
3.  Присвойте свойству <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> соответствующее значение. ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [При выборе типа учетных данных](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) В следующем коде используется значение <xref:System.ServiceModel.MessageCredentialType.Certificate>.  
  
4.  Создайте экземпляр класса <xref:System.Uri> с соответствующим базовым адресом. Обратите внимание, что адрес должен использовать схему "HTTPS" и содержать фактическое имя компьютера и номер порта, к которому привязан SSL-сертификат. (Кроме того, базовый адрес можно задать в конфигурации.)  
  
5.  Добавьте конечную точку службы с помощью метода <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.  
  
6.  Создайте экземпляр класса <xref:System.ServiceModel.ServiceHost> и вызовите метод <xref:System.ServiceModel.ICommunicationObject.Open%2A>, как показано в следующем примере кода.  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a>Использование привязки NetTcpBinding с сертификатом для обеспечения безопасности транспорта (в коде)  
  
1.  Создайте экземпляр класса <xref:System.ServiceModel.NetTcpBinding> и задайте для свойства <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> значение <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2.  Присвойте свойству <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> соответствующее значение. В следующем коде используется значение <xref:System.ServiceModel.MessageCredentialType.Certificate>.  
  
3.  Создайте экземпляр класса <xref:System.Uri> с соответствующим базовым адресом. Обратите внимание, что адрес должен использовать схему "net.tcp". (Кроме того, базовый адрес можно задать в конфигурации.)  
  
4.  Создайте экземпляр класса <xref:System.ServiceModel.ServiceHost>.  
  
5.  Воспользуйтесь методом <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> класса <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>, чтобы явно задать сертификат X.509 для службы.  
  
6.  Добавьте конечную точку службы с помощью метода <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.  
  
7.  Вызовите метод <xref:System.ServiceModel.ICommunicationObject.Open%2A>, как показано в следующем примере кода.  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a>Использование привязки NetTcpBinding с Windows для обеспечения безопасности транспорта (в коде)  
  
1.  Создайте экземпляр класса <xref:System.ServiceModel.NetTcpBinding> и задайте для свойства <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> значение <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2.  Настройте безопасность транспорта на использование Windows, задав для свойства <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> значение <xref:System.ServiceModel.TcpClientCredentialType.Windows>. (Обратите внимание, что это значение используется по умолчанию.)  
  
3.  Присвойте свойству <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> соответствующее значение. В следующем коде используется значение <xref:System.ServiceModel.MessageCredentialType.Certificate>.  
  
4.  Создайте экземпляр класса <xref:System.Uri> с соответствующим базовым адресом. Обратите внимание, что адрес должен использовать схему "net.tcp". (Кроме того, базовый адрес можно задать в конфигурации.)  
  
5.  Создайте экземпляр класса <xref:System.ServiceModel.ServiceHost>.  
  
6.  Воспользуйтесь методом <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> класса <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>, чтобы явно задать сертификат X.509 для службы.  
  
7.  Добавьте конечную точку службы с помощью метода <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.  
  
8.  Вызовите метод <xref:System.ServiceModel.ICommunicationObject.Open%2A>, как показано в следующем примере кода.  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a>Использование конфигурации  
  
#### <a name="to-use-the-wshttpbinding"></a>Использование привязки WSHttpBinding  
  
1.  Задайте для компьютера SSL-сертификат, привязанный к порту. ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Как: Настройка порта SSL-сертификат,](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)). Не нужно задавать <`transport`> значение элемента в этой конфигурации.  
  
2.  Задайте тип учетных данных клиента для MLS. В следующем примере задается `clientCredentialType` атрибут <`message`> элемент `UserName`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a>Использование привязки NetTcpBinding с сертификатом для обеспечения безопасности транспорта  
  
1.  В случае SSL по TCP необходимо явно задать сертификат в элементе `<behaviors>`. В следующем примере сертификат задается своим издателем в хранилище по умолчанию (в хранилище локального компьютера и личном хранилище).  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  Добавить [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) для раздела привязок  
  
3.  Добавьте элемент привязки и присвойте атрибуту `name` соответствующее значение.  
  
4.  Добавить <`security`> и присвойте `mode` атрибут `TransportWithMessageCredential`.  
  
5.  Добавить <`message>` элемент, а также установите `clientCredentialType` соответствующее значение атрибута.  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a>Использование привязки NetTcpBinding с Windows для обеспечения безопасности транспорта  
  
1.  Добавить [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) для раздела привязок  
  
2.  Добавить <`binding`> и присвойте `name` соответствующее значение атрибута.  
  
3.  Добавить <`security`> и присвойте `mode` атрибут `TransportWithMessageCredential`.  
  
4.  Добавить <`transport`> и присвойте `clientCredentialType` атрибут `Windows`.  
  
5.  Добавить <`message`> и присвойте `clientCredentialType` соответствующее значение атрибута. В следующем коде задается значение для сертификата.  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Задание режима безопасности](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)  
 [Защита служб](../../../../docs/framework/wcf/securing-services.md)  
 [Защита служб и клиентов](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
