---
title: "Проверка клиента"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0c1f805-1a81-4d0d-a112-bf5e2e87a631
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 340af20c44b8fde3fdff92d07837c3cc04ca517d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="client-validation"></a>Проверка клиента
Службы часто публикуют метаданные, чтобы включить автоматическое создание и настройку типов прокси клиента. Если служба не является доверенной, клиентские приложения должны убедиться, что метаданные соответствуют политике клиентского приложения в плане безопасности, транзакций, типа контракта службы и т. д. В следующем образце показано, как создать поведение конечной точки клиента, которое проверяет конечную точку службы на предмет безопасности использования.  
  
 Служба предоставляет четыре конечных точки службы. Первая конечная точка использует WSDualHttpBinding, вторая - проверку подлинности NTLM, третья конечная точка включает поток транзакций, а четвертая использует проверку подлинности на основе сертификатов.  
  
 Для извлечения метаданных для службы клиент использует класс <xref:System.ServiceModel.Description.MetadataResolver>. Клиент реализует политику запрещения дуплексных привязок, проверки подлинности NTLM и потока транзакций с помощью поведения проверки. Для каждого импортированного из метаданных службы экземпляра <xref:System.ServiceModel.Description.ServiceEndpoint> клиентское приложение добавляет в `InternetClientValidatorBehavior` экземпляр поведения конечной точки <xref:System.ServiceModel.Description.ServiceEndpoint>, прежде чем пытаться использовать клиент [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] для подключения к конечной точке. Метод `Validate` этого поведения выполняется до вызова каких-либо операций в службе и реализует политику клиента, создавая исключение `InvalidOperationExceptions`.  
  
### <a name="to-build-the-sample"></a>Сборка образца  
  
1.  Чтобы построить решение, следуйте инструкциям в [сборка образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Запуск образца на одном компьютере  
  
1.  Откройте командную строку Visual Studio (2010) с правами администратора и запустите файл Setup.bat из папки установки образцов. При этом устанавливаются все сертификаты, необходимые для выполнения образца.  
  
2.  Запустите приложение службы из каталога \service\bin\Debug.  
  
3.  Запустите клиентское приложение из каталога \client\bin\Debug. Действия клиента отображаются в консольном приложении клиента.  
  
4.  Если клиенту и службе не удается взаимодействовать, см. раздел [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
5.  После завершения работы образца запустите файл Cleanup.bat, чтобы удалить сертификаты. В других образцах обеспечения безопасности используются те же сертификаты.  
  
### <a name="to-run-the-sample-across-computers"></a>Запуск образца на нескольких компьютерах  
  
1.  На сервере командную строку Visual Studio с правами администратора, введите `setup.bat service`. Под управлением `setup.bat` с `service` аргумент создается сертификат службы с полным доменным именем компьютера и экспортируется в файл с именем Service.cer.  
  
2.  Измените App.config на сервере так, чтобы в файле отражалось новое имя сертификата. То есть изменить `findValue` атрибута в [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) элемента, который требуется полное доменное имя компьютера.  
  
3.  Скопируйте файл Service.cer из каталога службы в клиентский каталог на клиентском компьютере.  
  
4.  На стороне клиента, откройте командную строку Visual Studio с правами администратора и введите `setup.bat client`. Под управлением `setup.bat` с `client` создается сертификат клиента с именем Client.com, который экспортируется в файл с именем Client.cer.  
  
5.  В файле client.cs измените значение адреса конечной точки MEX и `findValue` для задания сертификата сервера по умолчанию таким образом, чтобы они соответствовали новому адресу службы. Для этого замените имя localhost полным именем домена сервера. Выполните перестроение.  
  
6.  Скопируйте файл Client.cer из клиентского каталога в каталог службы на сервере.  
  
7.  На клиентском компьютере откройте командную строку Visual Studio с правами администратора и запустите файл ImportServiceCert.bat. Он импортирует сертификат службы из файла Service.cer в хранилище CurrentUser - TrustedPeople.  
  
8.  На сервере откройте командную строку Visual Studio с правами администратора и запустите файл ImportClientCert.bat. При этом импортируется сертификат клиента из файла Client.cer в хранилище «LocalMachine - TrustedPeople».  
  
9. На компьютере службы постройте проект службы в Visual Studio и запустите файл service.exe.  
  
10. На клиентском компьютере запустите файл client.exe.  
  
    1.  Если клиенту и службе не удается взаимодействовать, см. раздел [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Очистка после образца  
  
-   После завершения работы примера запустите в папке примеров файл Cleanup.bat.  
  
    > [!NOTE]
    >  Этот скрипт не удаляет сертификаты службы на клиенте при запуске образца на нескольких компьютерах. Если образцы [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], в которых использовались сертификаты, запускались на нескольких компьютерах, обязательно удалите сертификаты службы, которые были установлены в хранилище «CurrentUser - TrustedPeople». Для этого используйте следующую команду: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>См. также  
 [Использование метаданных](../../../../docs/framework/wcf/feature-details/using-metadata.md)
