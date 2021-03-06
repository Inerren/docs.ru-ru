---
title: "Интеграция транзакционных компонентов служб Enterprise Services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a236a34dd20661d62d59a3712a1800ff1f9a11ad
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="integrating-enterprise-services-transactional-components"></a>Интеграция транзакционных компонентов служб Enterprise Services
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]предоставляет механизм автоматического для интеграции с Enterprise Services (в разделе [интеграция с приложениями COM +](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)). Однако для разработки служб, которые внутренне используют транзакционные компоненты, размещенные внутри служб Enterprise Services, может потребоваться гибкость. Поскольку [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] транзакций функция основана на <xref:System.Transactions> инфраструктуры, процесс Интеграция служб Enterprise Services с [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] идентична для указания демонстрацию взаимодействия между <xref:System.Transactions> и Enterprise Службы, как описано в [взаимодействие с Enterprise Services и транзакции COM +](http://go.microsoft.com/fwlink/?LinkId=94949).  
  
 Чтобы обеспечить требуемый уровень взаимодействия между входящей поточной транзакцией и транзакцией контекста COM+, реализация службы должна создать экземпляр <xref:System.Transactions.TransactionScope> и использовать соответствующее значение из перечисления <xref:System.Transactions.EnterpriseServicesInteropOption>.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Интеграция служб Enterprise Services с операцией службы  
 В представленном ниже коде показана операция с разрешенным потоком транзакций, которая создает область <xref:System.Transactions.TransactionScope> с параметром <xref:System.Transactions.EnterpriseServicesInteropOption.Full>. В этом сценарии используются следующие условия.  
  
-   Если клиент передает транзакцию, операция, включая вызов компонента Enterprise Services, выполняется в рамках области этой транзакции. Использование параметра <xref:System.Transactions.EnterpriseServicesInteropOption.Full> обеспечивает синхронизацию транзакции с контекстом <xref:System.EnterpriseServices>. Это означает, что внешняя транзакция для <xref:System.Transactions> и <xref:System.EnterpriseServices> одна и та же.  
  
-   Если клиент не передает транзакцию, при присвоении <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> значения `true` для операции создается новая область транзакции. Аналогично, использование параметра <xref:System.Transactions.EnterpriseServicesInteropOption.Full> обеспечивает идентичность транзакции операции и транзакции, используемой внутри контекста компонента <xref:System.EnterpriseServices>.  
  
 Любые дополнительные вызовы метода также происходят в пределах области той же транзакции операции.  
  
```  
[ServiceContract()]  
public interface ICustomerServiceContract  
{  
   [OperationContract]  
   [TransactionFlow(TransactionFlowOption.Allowed)]  
   void UpdateCustomerNameOperation(int customerID, string newCustomerName);  
}  
  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CustomerService : ICustomerServiceContract  
{  
   [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
   public void UpdateCustomerNameOperation(int customerID, string newCustomerName)  
   {  
   // Create a transaction scope with full ES interop  
      using (TransactionScope ts = new TransactionScope(  
                     TransactionScopeOption.Required,  
                     new TransactionOptions(),  
                     EnterpriseServicesInteropOption.Full))  
      {  
         // Create an Enterprise Services component  
         // Call UpdateCustomer method on an Enterprise Services   
         // component   
  
         // Call UpdateOtherCustomerData method on an Enterprise   
         // Services component   
         ts.Complete();  
      }  
  
      // Do UpdateAdditionalData on an non-Enterprise Services  
      // component  
   }  
}  
```  
  
 Если между текущей транзакцией операции и вызовами транзакционных компонентов Enterprise Services синхронизация не требуется, при создании экземпляра <xref:System.Transactions.EnterpriseServicesInteropOption.None> используйте параметр <xref:System.Transactions.TransactionScope>.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Интеграция служб Enterprise Services с клиентом  
 В представленном ниже клиентском коде показано использование экземпляра <xref:System.Transactions.TransactionScope> с параметром <xref:System.Transactions.EnterpriseServicesInteropOption.Full>. В этом сценарии вызовы операций службы, которые поддерживают поток транзакций, происходят в рамках области той же транзакции, что и вызовы компонентов Enterprise Services.  
  
```  
static void Main()  
{  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
  
    // Create a transaction scope with full ES interop  
    using (TransactionScope ts = new TransactionScope(  
          TransactionScopeOption.Required,  
          new TransactionOptions(),  
          EnterpriseServicesInteropOption.Full))  
    {  
        // Call Add calculator service operation  
  
        // Create an Enterprise Services component  
  
        // Call UpdateCustomer method on an Enterprise Services   
        // component   
  
        ts.Complete();  
    }  
  
    // Closing the client gracefully closes the connection and   
    // cleans up resources  
    client.Close();  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Интеграция с приложениями COM +](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Интеграция с приложениями COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
