---
title: "Практическое руководство. Указание типа учетных данных клиента"
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
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c6959ec7f2226f0d6554e9210b3ee1311871cdcf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-specify-the-client-credential-type"></a>Практическое руководство. Указание типа учетных данных клиента
После установки режима безопасности (на уровне транспорта или сообщений) можно установить тип учетных данных клиента. Это свойство определяет тип учетных данных, которые клиент должен предоставить службе для проверки подлинности. [!INCLUDE[crabout](../../../includes/crabout-md.md)]режим безопасности (необходимым этапом перед установкой типа учетных данных клиента), см. параметр [как: режим безопасности](../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
### <a name="to-set-the-client-credential-type-in-code"></a>Установка типа учетных данных клиента в коде  
  
1.  Создайте экземпляр привязки, который будет использовать служба. В этом примере используется привязка <xref:System.ServiceModel.WSHttpBinding>.  
  
2.  Присвойте свойству <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> соответствующее значение. В этом примере используется режим Message.  
  
3.  Присвойте свойству <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> соответствующее значение. В этом примере используется проверка подлинности Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a>Установка типа учетных данных клиента в файле конфигурации  
  
1.  Добавить [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) в файле конфигурации.  
  
2.  В качестве дочернего элемента, добавить [ \<привязки >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) элемента.  
  
3.  Добавьте соответствующую привязку. В этом примере используется [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) элемента.  
  
4.  Добавить [ \<привязки >](../../../docs/framework/misc/binding.md) и присвойте `name` соответствующее значение атрибута. В этом примере используется имя "SecureBinding".  
  
5.  Добавьте привязку `<security>`. Присвойте атрибуту `mode` соответствующее значение. В данном примере используется значение `"Message"`.  
  
6.  Добавьте элемент `<message>` или `<transport>` в зависимости от режима безопасности. Присвойте атрибуту `clientCredentialType` соответствующее значение. В этом примере используется `"Windows"`.  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a>См. также  
 [Защита служб](../../../docs/framework/wcf/securing-services.md)  
 [Практическое руководство. Задание режима безопасности](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
