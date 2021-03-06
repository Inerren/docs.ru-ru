---
title: "Элемент &lt;messageSenderAuthentication&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5a280f9fe59ca5294276b98ec3632d6bc1a7ecba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="ltmessagesenderauthenticationgt-element"></a>Элемент &lt;messageSenderAuthentication&gt;
Задает параметры проверки подлинности для одноранговых отправителей сообщений.  
  
 Дополнительные сведения о программировании одноранговая сеть см. в разделе [-одноранговые сети](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
 \<система. ServiceModel >  
\<поведения >  
\<endpointBehaviors >  
\<поведение >  
\<clientCredentials >  
\<Одноранговый >  
\<messageSenderAuthentication >  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<messageSenderAuthentication  
customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описываются атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|customCertificateValidatorType|Тип и сборка, используемые для проверки пользовательского типа. Этот атрибут должен быть задан, когда `certificateValidationMode` имеет значение `Custom`.|  
|certifcateValidationMode|Задает один из трех режимов для проверки учетных данных. Если свойству присвоено значение `Custom`, также необходимо указать свойство `customCertificateValidator`.|  
|revocationMode|Один из режимов, используемых для проверки списков отозванных сертификатов (CRL).|  
|trustedStoreLocation|Одно из двух местоположений системного хранилища: `LocalMachine` или `CurrentUser`. Данное значение используется при согласовании сертификата службы для клиента. Проверка выполняется для **доверенные лица** хранения в указанном местоположении хранилища.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>Атрибут customCertificateValidatorType  
  
|Значение|Описание|  
|-----------|-----------------|  
|Строковое|Необязательно. Задает имя типа и сборку, а также другие данные, используемые для поиска типа. Требуется, как минимум, пространство имен и имя типа. К дополнительным сведениям относятся: имя сборки, номер версии, язык и региональные параметры и маркер открытого ключа.|  
  
## <a name="certificatevalidationmode-attribute"></a>Атрибут certificateValidationMode  
  
|Значение|Описание|  
|-----------|-----------------|  
|Перечисление|Необязательно. Одно из следующих значений: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`. Значение по умолчанию — `ChainTrust`. Значение по умолчанию — `ChainTrust`.<br /><br /> Дополнительные сведения см. в разделе [работа с сертификатами](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>Атрибут revocationMode  
  
|Значение|Описание|  
|-----------|-----------------|  
|Перечисление|Одно из следующих значений: `NoCheck`, `Online`, `Offline`. Значение по умолчанию — `Online`.<br /><br /> Дополнительные сведения см. в разделе [работа с сертификатами](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>Атрибут trustedStoreLocation  
  
|Значение|Описание|  
|-----------|-----------------|  
|Перечисление|Одно из следующих значений: `LocalMachine` или `CurrentUser`. Значение по умолчанию — `CurrentUser`. Если клиентское приложение выполняется под учетной записью системы, сертификат обычно находится в расположении `LocalMachine`. Если клиентское приложение выполняется под учетной записью пользователя, то сертификат обычно находится в расположении `CurrentUser`. Значение по умолчанию — `CurrentUser`.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<Одноранговый >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|Задает учетные данные, используемые для проверки подлинности клиента при подключении к одноранговой службе.|  
  
## <a name="remarks"></a>Примечания  
 Этот элемент должен быть настроен, если выбрана проверка подлинности сообщения. Для вывода каналов, каждое сообщение подписывается с помощью сертификата, предоставляемого [ \<сертификата >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md). Во всех сообщениях перед доставкой приложению проверяются учетные данные сообщения с помощью модуля проверки, заданного атрибутом `customCertificateValidatorType` этого элемента. Модуль проверки может принять или отклонить учетные данные.  
  
## <a name="example"></a>Пример  
 В приведенном ниже примере кода устанавливается режим проверки отправителя сообщения `PeerOrChainTrust`.  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
      <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
        <messageSenderAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
       <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
## <a name="see-also"></a>См. также  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [Работа с сертификатами](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Одноранговые сети](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Проверка подлинности сообщения одноранговых каналов](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Нестандартная проверка подлинности одноранговых каналов](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Защита приложений одноранговых каналов](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
