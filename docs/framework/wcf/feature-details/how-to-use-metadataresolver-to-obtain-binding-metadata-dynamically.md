---
title: "Практическое руководство. Использование MetadataResolver для динамического получения метаданных привязки"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8f3d8245b9d5bf05297b4d1edfba1926d2104ce
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a>Практическое руководство. Использование MetadataResolver для динамического получения метаданных привязки
В этом разделе показано, как использовать класс <xref:System.ServiceModel.Description.MetadataResolver> для динамического получения метаданных привязки.  
  
### <a name="to-dynamically-obtain-binding-metadata"></a>Динамическое получение метаданных привязки  
  
1.  Создайте объект <xref:System.ServiceModel.EndpointAddress> с адресом конечной точки метаданных.  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2.  Вызовите метод <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, передающий тип службы и адрес конечной точки метаданных. Возвращается коллекция конечных точек, реализующих указанный контракт. Из метаданных импортируются только сведения о привязке; сведения о контракте не импортируются. Вместо этого используется предоставленный контракт.  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3.  Затем можно последовательно просмотреть коллекцию конечных точек службы, чтобы извлечь требуемые сведения о привязке. Приведенный ниже код просматривает конечные точки, создает объект клиента службы, который передает привязку и адрес, связанный с текущей конечной точкой, а затем вызывает метод службы.  
  
    ```  
    foreach (ServiceEndpoint point in endpoints)  
    {  
       if (point != null)  
       {  
          // Create a new wcfClient using retrieved endpoints.  
          using (wcfClient = new SampleServiceClient(point.Binding, point.Address))  
          {  
             Console.WriteLine(  
               wcfClient.SampleMethod("Client used the "  
               + point.Address.ToString() + " address."));  
          }  
      }  
    }  
    ```  
  
## <a name="see-also"></a>См. также  
 [Метаданные](../../../../docs/framework/wcf/feature-details/metadata.md)
