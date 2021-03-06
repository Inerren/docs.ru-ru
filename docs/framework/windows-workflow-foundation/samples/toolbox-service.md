---
title: "Служба области элементов"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 294c530072b2d694f9aeb54d04b36d72bb6da637
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="toolbox-service"></a>Служба области элементов
Этот образец демонстрирует, как обновлять действия области элементов [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] на базе контекста рабочего процесса. Образец содержит рабочий процесс, изменяющий содержание области элементов в зависимости от выбранного пользовательского действия.  
  
## <a name="discussion"></a>Обсуждение  
 В ходе разработки рабочего процесса клиенты обычно выражают пожелание, чтобы область элементов отображалась по-разному в зависимости от контекста. Например, пользователь может захотеть, чтобы в области элементов отображались дополнительные действия, если в рабочий процесс добавляется определенное действие. При удалении действий из рабочего процесса область элементов должна соответствующим образом прореагировать на это согласно требованиям домена.  
  
 Находясь в повторно размещенном конструкторе рабочих процессов, можно работать с элементом управления области элементов и обеспечить, чтобы узел, основанный на модели изменения рабочего процесса, включал соответствующие изменения в элемент управления области элементов. Тем не менее в [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] пользователь не может контролировать область элементов, поэтому для изменения его содержания требуется специальный интерфейс. Этот интерфейс - `IActivityToolboxService`.  
  
 API-интерфейс реализует следующие четыре метода.  
  
```  
public interface IActivityToolboxService   
{   
        void AddCategory(string categoryName);   
        void RemoveCategory(string categoryName);   
        void AddItem(string qualifiedTypeName, string categoryName);   
        void RemoveItem(string qualifiedTypeName, string categoryName);   
        IList<string> EnumCategories();   
        IList<string> EnumItems(string categoryName);   
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Настройка, сборка и выполнение образца  
  
1.  Откройте в среде [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] файл решения WorkflowSimulator.sln.  
  
2.  Выполните сборку решения, нажав клавиши CTRL+SHIFT+B.  
  
3.  Откройте файл Workflow.xaml.  
  
4.  Добавить **CustomActivity** , перетащив его из области элементов. Обратите внимание, что дополнительная область элементов имеет имя: **новая категория WF** с дополнительным действием **назначить**.  
  
5.  Снимите выбор **CustomActivity** , перетащив на него другое действие.  
  
6.  Элемент **назначить** в категории **новая категория WF** в области элементов будет удален. Кроме того, поскольку в категории больше не осталось элементов, будет удалена и сама категория.  
  
7.  Выберите **CustomActivity** еще раз и категорию и **назначить** действие будет добавлено повторно.  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите на страницу [Примеры Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) , чтобы скачать все примеры [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`
