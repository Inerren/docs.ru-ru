---
title: "Передача формы"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa6f84f9-2e07-4e3c-92d0-a245308b7dff
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e0fe1f8641de2b4ee504deeae8f97b312dfe9b99
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="form-post"></a>Передача формы
Данный образец демонстрирует расширение программной модели WCF REST для поддержки новых форматов входящих запросов. Образец также содержит реализацию модуля форматирования, который может десериализовать запрос из передачи формы HTML методом POST в тип [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Кроме того, образец использует шаблон T4 для возврата страницы HTML, которая предоставляет форму HTML, дающую пользователям возможность возвращать данные в службу WCF REST.  
  
## <a name="demonstrates"></a>Демонстрации  
  
-   Расширение поддержки для форматов входящих запросов.  
  
-   Интеграция шаблонов T4.  
  
## <a name="discussion"></a>Обсуждение  
 Этот образец состоит из двух проектов. Один проект представляет собой библиотеку HtmlFormProcessing, которая содержит пользовательский модуль форматирования запросов, реализующий десериализацию запросов из форм HTML, метода POST в типы [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Второй проект представляет собой консольное приложение, которое расширяет образец базовой службы ресурсов для поддержки использования пользовательского модуля форматирования запросов библиотеки HtmlFormProcessing.  
  
 Пользовательский модуль форматирования, который может десериализовать передачу форм HTML методом POST (HtmlFormRequestDispatchFormatter), принимает как типы [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], которые можно преобразовать из строки с помощью <xref:System.ServiceModel.Dispatcher.QueryStringConverter>, так и типы, отмеченные атрибутом <xref:System.Runtime.Serialization.DataContractAttribute> и имеющие только члены, которые допускают преобразование из строки с помощью QueryStringConverter.  
  
 Проект библиотеки HtmlFormProcessing также содержит абстрактный базовый класс, `RequestBodyDispatchFormatter`, который можно использовать для создания других пользовательских модулей форматирования запросов. Наследование от `RequestBodyDispatchFormatter` позволяет разработчику сосредоточиться на логике десериализации текста запроса, что обеспечивает сопоставление базовым классом параметров шаблона URI параметрам метода операции. Также в проекте библиотеки HtmlFormProcessing содержится класс `HtmlFormProcessingBehavior`, который показывает, как наследовать от класса <xref:System.ServiceModel.Description.WebHttpBehavior>, чтобы заменить модуль форматирования по умолчанию на пользовательский модуль форматирования запросов.  
  
 Этот проект консольного приложения расширяет [базовой службы ресурсов](../../../../docs/framework/wcf/samples/basic-resource-service.md) образца. В образце базовой службы ресурсов показано, как предоставить доступ к ресурсу с использованием модели программирования WCF REST. В образце базовой службы ресурсов доступ к коллекции клиентских ресурсов предоставляется образом, позволяющим создавать, извлекать, обновлять и удалять клиентов в коллекции. В образце базовой службы ресурсов используются только два непосредственно поддерживаемых формата входящих запросов - XML и JSON.  
  
 Консольное приложение в этом образце формы использует пользовательский модуль форматирования в библиотеке HtmlFormProcessing, что дает пользователям возможность создавать клиентов, отправляя запрос из формы HTML с помощью браузера. Кроме того, добавляется операция, которая возвращает страницу HTML, содержащую форму для публикации в службе. Эта страница HTML формируется с использованием предварительно обработанного шаблона T4, который состоит из TT-файла и автоматически формируемого файла CS. TT-файл позволяет разработчику записывать ответ в виде шаблона, содержащего переменные и управляющие структуры. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]T4 см. в разделе [Создание артефактов с помощью текстовых шаблонов](http://go.microsoft.com/fwlink/?LinkId=178139).  
  
#### <a name="to-run-the-sample"></a>Выполнение образца  
  
1.  Откройте решение для образца публикации формы. Для успешного выполнения образца среду [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] необходимо запускать от имени администратора. Для этого щелкните правой кнопкой мыши [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] значок и выберите «Запуск от имени администратора» в контекстном меню.  
  
2.  Нажмите сочетание клавиш CTRL+SHIFT+B, чтобы создать решение, а затем сочетание клавиш CTRL+F5, чтобы запустить проект консольного приложения FormPost.  
  
3.  Открывается окно консоли с URI запущенной службы и URI HTML-страницы справки для запущенной службы.  
  
4.  При выполнении образца клиент записывает состояние текущего действия, будь то добавление заказчика, обновление заказчика, удаление заказчика или получение списка текущих заказчиков из списка в окно консоли.  
  
5.  Затем выдается предложение перейти к URI формы заказчика. Откройте браузер и перейдите по заданному URI. Введите имя и адрес клиента и нажмите кнопку **отправить** кнопки.  
  
6.  Нажмите любую клавишу, чтобы продолжить выполнение образца в окне консоли.  
  
7.  После завершения обратите внимание, что заказчик, созданный из браузера, включен в окончательный список заказчиков.  
  
8.  Чтобы завершить образец, нажмите любую клавишу.  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите на страницу [Примеры Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) , чтобы скачать все примеры [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Web\FormPost`
