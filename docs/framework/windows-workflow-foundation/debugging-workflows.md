---
title: "Отладка рабочих процессов"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 857f227d8541687768f470633e5430aee2171ea8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="debugging-workflows"></a>Отладка рабочих процессов
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] обеспечивает несколько возможностей отладки выполняемых рабочих процессов из среды разработки. Отладку рабочих процессов можно выполнять в конструкторе, XAML или в коде.  
  
## <a name="debugging-in-the-workflow-designer"></a>Отладка в конструкторе рабочих процессов  
 Точки останова можно задать для действий в конструкторе рабочих процессов, выделить действие и нажав клавишу **F9** или с помощью контекстного меню действия. Затем выполнение рабочего процесса прерывается при запуске узла рабочего процесса в режиме отладки. На следующем снимке экрана выполнение рабочего процесса приостановлено в точке останова. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Отладка рабочих процессов в конструкторе рабочих процессов](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer).  
  
## <a name="debugging-in-xaml"></a>Отладка в XAML  
 Если выполнение рабочего процесса было приостановлено в точке останова в конструкторе, то отладку рабочего процесса также можно выполнить в XAML. Чтобы просмотреть точку выполнения в XAML, выберите **представление XAML** в конструкторе рабочих процессов при приостановке выполнения рабочего процесса. Отладку можно переключить обратно в конструктор, повторно открыв рабочий процесс в конструкторе из обозревателя решений. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Как: отладка XAML в конструкторе рабочих процессов](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer).  
  
## <a name="debugging-in-code"></a>Отладка в коде  
 Точки останова кода можно использовать в [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] аналогично их использованию в других императивных приложениях. Щелкните левую границу области кода, чтобы создать точку останова кода, или нажмите клавишу **F9** чтобы поместить точку останова в положении курсора.  
  
## <a name="attaching-to-a-workflow-process"></a>Присоединение к рабочему процессу  
 Отладка рабочих процессов поддерживает также использование инфраструктуры Visual Studio для присоединения к процессу. Это позволяет автору рабочего процесса выполнять отладку рабочего процесса, запущенного в другой среде узла, например в службах IIS 7.0.  
  
## <a name="remote-debugging"></a>Удаленная отладка  
 Функции удаленной отладки [!INCLUDE[wf](../../../includes/wf-md.md)] такие же, как у удаленной отладки других компонентов [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]. Сведения об использовании удаленной отладки см. в разделе [как: Включение удаленной отладки](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
> [!NOTE]
>  Если приложение рабочего процесса предназначено x86 архитектуры и размещается на компьютере под управлением 64-разрядной операционной системы, удаленная отладка не будет работать без [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] установлен на удаленном компьютере или цель приложения рабочего процесса изменена Чтобы **любой ЦП**.  
  
## <a name="extending-the-workflow-debugging-service"></a>Расширение службы отладки рабочих процессов  
 Теперь служба отладки рабочих процессов является открытой и может быть использована для создания настраиваемых приложений, таких как приложения наблюдения, моделирования и отладки в повторно размещенном конструкторе. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] см. раздел <xref:System.Activities.Presentation.Debug.DebuggerService>.
