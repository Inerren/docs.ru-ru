---
title: "Практическое руководство. Выравнивание и растягивание элемента управления в элементе управления TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 043adb68b88ab031cea3de1206d1f2c4252b75d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a>Практическое руководство. Выравнивание и растягивание элемента управления в элементе управления TableLayoutPanel
Можно выравнивать и растягивать элементы управления в <xref:System.Windows.Forms.TableLayoutPanel> с <xref:System.Windows.Forms.Control.Anchor%2A> и <xref:System.Windows.Forms.Control.Dock%2A> свойства.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-align-and-stretch-a-control"></a>Выравнивание и Растягивание элемента управления  
  
1.  Перетащите <xref:System.Windows.Forms.TableLayoutPanel> управления из **элементов** на форму.  
  
2.  Перетащите <xref:System.Windows.Forms.Button> управления из **элементов** в левый верхний угол элемента <xref:System.Windows.Forms.TableLayoutPanel> элемента управления. <xref:System.Windows.Forms.Button> Управления выравнивается по центру ячейки.  
  
3.  Установите для параметра <xref:System.Windows.Forms.Button> элемента управления <xref:System.Windows.Forms.Control.Anchor%2A> свойства `Left,Right`. <xref:System.Windows.Forms.Button> Управления растягивается по ширине ячейки.  
  
4.  Установите для параметра <xref:System.Windows.Forms.Button> элемента управления <xref:System.Windows.Forms.Control.Anchor%2A> свойства `Top,Bottom`. <xref:System.Windows.Forms.Button> Управления растягивается в соответствии с высотой ячейки.  
  
5.  Установите для параметра <xref:System.Windows.Forms.Button> элемента управления <xref:System.Windows.Forms.Control.Dock%2A> свойства <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Button> Элемент управления расширяется для заполнения ячейки.  
  
6.  Установите для параметра <xref:System.Windows.Forms.Button> элемента управления <xref:System.Windows.Forms.Control.Dock%2A> свойства <xref:System.Windows.Forms.DockStyle.None>. <xref:System.Windows.Forms.Button> Управления возвращает исходный размер и перемещается в левый верхний угол ячейки. **Конструктор Windows Forms** задал <xref:System.Windows.Forms.Control.Anchor%2A> свойства `Top, Left`.  
  
7.  Установите для параметра <xref:System.Windows.Forms.Button> элемента управления <xref:System.Windows.Forms.Control.Anchor%2A> свойства `Bottom,Right`. <xref:System.Windows.Forms.Button> Элемент управления перемещается в правом нижнем углу ячейки.  
  
8.  Установите для параметра <xref:System.Windows.Forms.Button> элемента управления <xref:System.Windows.Forms.Control.Anchor%2A> свойства <xref:System.Windows.Forms.AnchorStyles.None>. <xref:System.Windows.Forms.Button> Управления перемещается по центру ячейки.  
  
## <a name="see-also"></a>См. также  
 [Элемент управления TableLayoutPanel](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
