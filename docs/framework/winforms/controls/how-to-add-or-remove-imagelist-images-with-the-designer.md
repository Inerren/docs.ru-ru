---
title: "Практическое руководство. Добавление и удаление изображений из компонента ImageList с помощью конструктора"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71fa29fc36292bb6620ab458785abaabc749c38d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a>Практическое руководство. Добавление и удаление изображений из компонента ImageList с помощью конструктора
Можно добавить изображения для <xref:System.Windows.Forms.ImageList> компонент несколькими различными способами. Быстро добавлять рисунки с помощью смарт-тег, связанные с <xref:System.Windows.Forms.ImageList>, или при установке на несколько других свойств <xref:System.Windows.Forms.ImageList>, может оказаться удобнее добавлять изображения с помощью окна «Свойства». Можно также добавлять изображения с помощью кода. Дополнительные сведения о добавлении изображений в коде см. в разделе [как: Добавление и удаление изображений с помощью компонента ImageList в Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md). Обычно заполняется <xref:System.Windows.Forms.ImageList> компонент с изображениями, прежде чем он связан с элементом управления, но это не является обязательным.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-or-remove-images-by-using-the-properties-window"></a>Чтобы добавить или удалить изображения с помощью окна «Свойства»  
  
1.  Выберите <xref:System.Windows.Forms.ImageList> компонента, или добавьте его в форму.  
  
2.  В окне свойств нажмите кнопку с многоточием (![экрана VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) рядом с <xref:System.Windows.Forms.ImageList.Images%2A> свойство.  
  
3.  В **редактор коллекции изображений**, нажмите кнопку **добавить** или **удалить** на добавление и удаление изображений из списка.  
  
### <a name="to-add-or-remove-images-using-the-smart-tag"></a>Добавление и удаление изображений с помощью смарт-тег  
  
1.  Выберите <xref:System.Windows.Forms.ImageList> компонента, или добавьте его в форму.  
  
2.  Щелкните глиф смарт-тега (![глиф смарт-тега](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))  
  
3.  В **задачи ImageList** выберите **выбрать рисунки**.  
  
4.  В **редактор коллекции изображений** щелкните **добавить** или **удалить** на добавление и удаление изображений из списка.  
  
## <a name="see-also"></a>См. также  
 [Изображения, точечные рисунки и метафайлы](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Пошаговое руководство. Выполнение типичных задач с помощью смарт-тегов в элементах управления Windows Forms](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 [Компонент ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
