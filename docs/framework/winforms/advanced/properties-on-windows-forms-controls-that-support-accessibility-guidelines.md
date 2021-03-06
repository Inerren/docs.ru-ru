---
title: "Свойства элементов управления Windows Forms, в которых соблюдены правила доступности"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ca18b35b90b028054e68a0a14fecc819a6c20b9
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2017
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a>Свойства элементов управления Windows Forms, в которых соблюдены правила доступности
Элементы управления на стандартной панели инструментов для Windows Forms поддерживают многие из специальных возможностей, включая демонстрацию фокуса клавиатуры и элементов экрана.  
  
## <a name="planning-ahead-for-accessibility"></a>Планирование для специальных возможностей  
 Свойства элементов управления можно использовать для поддержки других специальных возможностей, как показано в следующей таблице. Кроме того меню следует использовать для предоставления доступа к функциям программы.  
  
|Свойство элемента управления|Соображения о специальных возможностях|  
|----------------------|--------------------------------------|  
|AccessibleDescription|Описание передается в средства специальных возможностей, таких как средства чтения с экрана. Специальные возможности — это специализированные программы и устройства, помогающие людям с ограниченными возможностями эффективнее использовать компьютеры.|  
|AccessibleName|Имя, которое будет сообщено доступа к специальным возможностям.|  
|AccessibleRole|Описание использования элемента в пользовательском интерфейсе.|  
|TabIndex|Создает последовательность переходов по форме. Очень важно для элементов управления, не имеющих внутренних меток, таких как текстовые поля, чтобы их связанных метка непосредственно предшествовала ему в последовательности табуляции.|  
|Text|Используйте символ «&» для создания ключей доступа. Клавиши доступа — часть, предоставляющая документированный доступ с клавиатуры к функциям.|  
|Размер шрифта|Если размер шрифта не является регулируемым, затем оно должно задаваться 10 пунктов или выше. После задания размера шрифта формы, все элементы управления, после добавления в форму будет иметь тот же размер.|  
|Forecolor|Если это свойство имеет значение по умолчанию, с пользовательскими настройками цвета будет использоваться в форме.|  
|Backcolor|Если это свойство имеет значение по умолчанию, с пользовательскими настройками цвета будет использоваться в форме.|  
|BackgroundImage|Не указывайте это свойство для удобства чтения текста.|  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Создание приложения Windows с поддержкой специальных возможностей](../../../../docs/framework/winforms/advanced/walkthrough-creating-an-accessible-windows-based-application.md)
