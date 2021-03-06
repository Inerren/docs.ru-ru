---
title: "Практическое руководство. Сокращение времени запуска клиентских приложений WCF с использованием XmlSerializer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 14f5cf25bbcde4732162f2c44c83661a0ac739ea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a>Практическое руководство. Сокращение времени запуска клиентских приложений WCF с использованием XmlSerializer
Службы и клиентские приложения, использующие типы данных, сериализуемые с помощью сериализатора <xref:System.Xml.Serialization.XmlSerializer>, создают и компилируют код сериализации для этих типов данных во время выполнения, что может привести к снижению производительности при запуске.  
  
> [!NOTE]
>  Предварительно созданный код сериализации может использоваться только в клиентских приложениях, но не в службах.  
  
 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) может повысить производительность при запуске этих приложений путем создания кода необходимости сериализации из компилированных сборок для приложения. Svcutil.exe создает код сериализации для всех типов данных, используемых в контрактах служб в скомпилированной сборке приложения, которые могут быть сериализованы с помощью <xref:System.Xml.Serialization.XmlSerializer>. Контракты служб и операций, предусматривающие использование <xref:System.Xml.Serialization.XmlSerializer>, отмечены атрибутом <xref:System.ServiceModel.XmlSerializerFormatAttribute>.  
  
### <a name="to-generate-xmlserializer-serialization-code"></a>Создание кода сериализации XmlSerializer  
  
1.  Скомпилируйте код службы или клиента в одну или несколько сборок.  
  
2.  Откройте окно командной строки SDK.  
  
3.  Из командной строки запустите средство Svcutil.exe, используя следующий формат.  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     Аргумент `assemblyPath` задает путь к сборке, содержащей типы из контракта службы. Svcutil.exe создает код сериализации для всех типов данных, используемых в контрактах служб в скомпилированной сборке приложения, которые могут быть сериализованы с помощью <xref:System.Xml.Serialization.XmlSerializer>.  
  
     Svcutil.exe может формировать только код сериализации на C#. Для каждой входной сборки создается один файл исходного кода. Нельзя использовать **/Language** коммутатора, чтобы изменить язык создаваемого кода.  
  
     Чтобы указать путь к зависимым сборкам, используйте **/reference** параметр.  
  
4.  Предоставьте приложению доступ к созданному коду сериализации одним из следующих способов.  
  
    1.  Скомпилируйте созданный код сериализации в отдельную сборку с именем [*исходной сборки*]. XmlSerializers.dll (например, MyApp.XmlSerializers.dll). Приложение должно иметь возможность загрузить эту сборку, которая должна быть подписана с помощью того же ключа, что и исходная сборка. В случае повторной компиляции исходной сборки необходимо заново создать сборку сериализации.  
  
    2.  Скомпилируйте созданный код сериализации в отдельную сборку и используйте атрибут <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> в контракте службы, в котором используется атрибут <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Задайте свойство <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> или <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> так, чтобы оно указывало на скомпилированную сборку сериализации.  
  
    3.  Скомпилируйте созданный код сериализации в сборку приложения и добавьте атрибут <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> в контракт службы, в котором используется атрибут <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Не задавайте свойства <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> или <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A>. По умолчанию предполагается, что сборка сериализации по умолчанию является текущей сборкой.  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a>Создание кода сериализации XmlSerializer в Visual Studio  
  
1.  Создание службы WCF и клиентских проектов в Visual Studio. Затем добавьте ссылку на службу в проект клиента.  
  
2.  Добавить <xref:System.ServiceModel.XmlSerializerFormatAttribute> в контракт службы в *reference.cs* файл в проект клиентского приложения в разделе **serviceReference** -> **reference.svcmap** . Обратите внимание, что необходимо показать все файлы в **обозревателе решений** для просмотра этих файлов.  
  
3.  Построение клиентского приложения.  
  
4.  Используйте [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) для создания предварительного сериализатора *.cs* файла с помощью команды:  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     Аргумент assemblyPath указывает путь к сборке клиента WCF.  
  
     Например:  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     *WCFClient.XmlSerializers.dll.cs* будет создан файл.  
  
5.  Компилировать предварительно созданную сборку сериализации.  
  
     Основываясь на примере на предыдущем шаге, компиляции команда будет выглядеть следующим образом:  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     Убедитесь в том, созданный *WCFClient.XmlSerializers.dll* находится в каталоге, где клиентские приложения, который является *WCFClient.exe* в этом случае.  
  
6.  Запустите клиентское приложение обычным образом. Будет использоваться предварительно созданную сборку сериализации.  
  
## <a name="example"></a>Пример  
 Следующая команда создает типы сериализации для типов `XmlSerializer`, используемых любыми контрактами служб в сборке.  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a>См. также  
 [Служебная программа для метаданных ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
