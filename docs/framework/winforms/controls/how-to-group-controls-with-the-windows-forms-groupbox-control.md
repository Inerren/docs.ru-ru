---
title: "Практическое руководство. Группировка элементов управления с помощью элемента управления GroupBox в формах Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 50d29de04b4e221105bb02e58de01344f13af69f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a>Практическое руководство. Группировка элементов управления с помощью элемента управления GroupBox в формах Windows Forms
Windows Forms <xref:System.Windows.Forms.GroupBox> элементы управления используются для группировки других элементов управления. Существует три причины для группировки элементов управления.  
  
-   Чтобы создать визуальную группировку связанных элементов форм для упрощения пользовательского интерфейса.  
  
-   Создание программной группировки (переключатели, например).  
  
-   Перемещение элементов управления как единое целое, во время разработки.  
  
### <a name="to-create-a-group-of-controls"></a>Чтобы создать группу элементов управления  
  
1.  Рисование <xref:System.Windows.Forms.GroupBox> элемента управления в форме.  
  
2.  Добавьте другие элементы управления в поле группы, рисования каждого элемента внутри группы.  
  
     При наличии существующих элементов управления, которые надо включить в группу, можно выбрать все элементы управления, вырезать их в буфер обмена, выберите <xref:System.Windows.Forms.GroupBox> управления, а затем вставьте их в группу. Также можно перетащить их в группу.  
  
3.  Задать <xref:System.Windows.Forms.GroupBox.Text%2A> свойства поля группы, соответствующий заголовок.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Forms.GroupBox>  
 [Элемент управления GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
