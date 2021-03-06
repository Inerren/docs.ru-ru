---
title: "Получение уведомления об изменении данных привязки Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ffafaff2355e89e2127742f2fba5c005492b4580
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Получение уведомления об изменении данных привязки Windows Forms
Одним из наиболее важных понятий привязки данных Windows Forms является *уведомление об изменении*. Чтобы обеспечить источника данных и связанными элементами управления всегда самые последние данные, необходимо добавить уведомление об изменении для привязки данных. В частности вы хотите убедиться, что элементы управления с привязкой уведомления об изменении, внесенные в источнике данных, а источник данных получает уведомление об изменениях, внесенных в свойства привязанного элемента управления.  
  
 Существуют различные виды уведомления об изменении, в зависимости от вида привязки данных:  
  
-   Простая привязка, в которой привязано свойство одного элемента управления к одному экземпляру объекта.  
  
-   Привязки список, который может включать свойство один элемент управления привязан к свойству элемента в списке или свойство элемента управления к списку объектов.  
  
 Кроме того, если вы создаете элементы управления Windows Forms, которые вы хотите использовать для привязки данных, необходимо применить *PropertyName*изменить шаблон к элементам управления, чтобы изменения связанных свойств элемента управления распространяются на источник данных.  
  
## <a name="change-notification-for-simple-binding"></a>Уведомление об изменении для простой привязки  
 Простая привязка бизнес-объектов необходимо предоставить уведомление об изменении при изменении значения свойства привязки. Это можно сделать путем предоставления доступа к *PropertyName*Changed для каждого свойства бизнес-объекта и привязки к элементам управления с бизнес-объекта <xref:System.Windows.Forms.BindingSource> или предпочтительный метод, который реализует бизнес-объект <xref:System.ComponentModel.INotifyPropertyChanged> интерфейс и вызывает <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> событие при изменении значения свойства. Дополнительные сведения см. в разделе [как: реализация интерфейса INotifyPropertyChanged](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md). При использовании объектов, реализующих <xref:System.ComponentModel.INotifyPropertyChanged> интерфейс, не нужно использовать <xref:System.Windows.Forms.BindingSource> для привязки объекта к элементу управления, но с помощью <xref:System.Windows.Forms.BindingSource> рекомендуется.  
  
## <a name="change-notification-for-list-based-binding"></a>Уведомление об изменении для привязки на основе списка  
 Windows Forms опирается на связанный список, образуя изменение свойства (меняет значение свойства элемента списка) или списка (элемент удален или добавлен в список) сведения о привязке элементов управления. Таким образом, списки, используемые для привязки данных должны реализовывать интерфейс <xref:System.ComponentModel.IBindingList>, который поддерживает оба типа уведомлений об изменении. <xref:System.ComponentModel.BindingList%601> — Это реализация универсального интерфейса <xref:System.ComponentModel.IBindingList> и предназначен для использования с привязкой данных Windows Forms. Можно создать <xref:System.ComponentModel.BindingList%601> , содержащий тип бизнес-объекта, который реализует <xref:System.ComponentModel.INotifyPropertyChanged> и автоматически преобразует список <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> событий для <xref:System.ComponentModel.IBindingList.ListChanged> события. Если связанный список не <xref:System.ComponentModel.IBindingList>, необходимо привязать список объектов к элементам управления Windows Forms с помощью <xref:System.Windows.Forms.BindingSource> компонента. <xref:System.Windows.Forms.BindingSource> Компонент предоставляет список свойств преобразования аналогична <xref:System.ComponentModel.BindingList%601>. Дополнительные сведения см. в разделе [как: уведомление об изменении данных с помощью компонента BindingSource и интерфейса INotifyPropertyChanged](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md).  
  
## <a name="change-notification-for-custom-controls"></a>Уведомление об изменении для пользовательских элементов управления  
 Наконец, на стороне элементов управления можно предоставить *PropertyName*Changed для каждого свойства, предназначенного для привязки к данным. Изменения свойств элемента управления, затем распространяются привязанного источника данных. Дополнительные сведения см. в разделе [как: применение шаблона PropertyNameChanged](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 <xref:System.ComponentModel.BindingList%601>  
 [Привязка данных Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Источники данных, поддерживаемые Windows Forms](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [Привязка данных и Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
