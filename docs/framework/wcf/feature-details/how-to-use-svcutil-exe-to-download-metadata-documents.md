---
title: "Практическое руководство. Использование Svcutil.exe для загрузки документов метаданных"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6868bbecd83305c07e0b547d0102d7bca48d41f8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Практическое руководство. Использование Svcutil.exe для загрузки документов метаданных
Средство Svcutil.exe позволяет загружать метаданные из выполняющихся служб и сохранять эти метаданные в локальных файлах. Для схем HTTP и HTTPS URL-адрес Svcutil.exe предпринимает попытку получить метаданные с помощью WS-MetadataExchange и [обнаружения веб-службы XML](http://go.microsoft.com/fwlink/?LinkId=94950). Для всех остальных URL-схем средство Svcutil.exe использует только протокол WS-MetadataExchange.  
  
 По умолчанию средство Svcutil.exe использует привязки, определенные в классе <xref:System.ServiceModel.Description.MetadataExchangeBindings>. Чтобы настроить привязку, используемую для протокола WS-MetadataExchange, необходимо в файле конфигурации Svcutil.exe (svcutil.exe.config) настроить конечную точку клиента, которая бы использовала контракт `IMetadataExchange` и имя которой совпадало бы со схемой универсального кода ресурса (URI) адреса конечной точки метаданных.  
  
> [!CAUTION]
>  При запуске Svcutil.exe, чтобы получить метаданные службы, которая предоставляет две разные службы контрактов, каждый из которых содержит операции с тем же именем, Svcutil.exe выводится сообщение об ошибке говорит: «Не удается получить метаданные из...» Например если имеется служба, которая предоставляет доступ к контракту службы с именем ICarService, который содержит операцию Get (Car c) и же служба предоставляет доступ к контракту службы с именем IBookService, который содержит операцию Get (Book b). Чтобы устранить эту проблему, выполните одно из следующих действий.  
>   
>  -   Переименуйте одну из операций  
> -   Задайте другое имя в свойстве <xref:System.ServiceModel.OperationContractAttribute.Name%2A>.  
> -   Установите другое пространство имен для одной из операций с помощью свойства <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.  
  
### <a name="to-download-metadata-using-svcutilexe"></a>Загрузка метаданных с помощью средства Svcutil.exe  
  
1.  Найдите средство Svcutil.exe в следующей папке:  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2.  Из командной строки запустите средство, используя следующий формат.  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Параметр `/t:metadata` необходимо указать, чтобы загружались метаданные. В противном случае будут созданы код и конфигурация клиента.  
  
3.  <`url`> Аргумент задает URL-адрес конечной точки службы, предоставляющей метаданные, или документа метаданных, размещенного в сети. <`epr`> Аргумент указывает путь к файлу XML, который содержит WS-Addressing `EndpointAddress` для конечной точки службы, которая поддерживает WS-MetadataExchange.  
  
 Дополнительные сведения об использовании этого инструмента для загрузки метаданных, в разделе [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Пример  
 Следующая команда позволяет загрузить документы с метаданными из выполняющейся службы.  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>См. также  
 [Служебная программа для метаданных ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
