---
title: "Практическое руководство. Считывание и установка значения текущей ячейки элемента управления DataGridView в Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb63c48831e19ce3cbb166e899aeee8b6a331839
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Практическое руководство. Считывание и установка значения текущей ячейки элемента управления DataGridView в Windows Forms
Взаимодействие с <xref:System.Windows.Forms.DataGridView> часто требуется программно найденные ячейки, которая в данный момент активна. Кроме того, может потребоваться изменить текущую ячейку. Можно выполнять эти задачи с <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> свойство.  
  
> [!NOTE]
>  Невозможно задать текущую ячейку в строке или столбце с его <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> свойство `false`.  
  
 В зависимости от <xref:System.Windows.Forms.DataGridView> этот выбор можно изменить режим выбора элемента управления, изменения в текущей ячейке. Дополнительные сведения см. в разделе [режимы выбора в элементе управления DataGridView Windows Forms](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-get-the-current-cell-programmatically"></a>Чтобы получить текущую ячейку программным способом  
  
-   Используйте <xref:System.Windows.Forms.DataGridView> элемента управления <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> свойство.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>Установка текущей ячейки программным способом  
  
-   Задать <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> свойства <xref:System.Windows.Forms.DataGridView> элемента управления. В следующем примере кода текущая ячейка имеет значение в строке 0 и 1 столбец.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
-   <xref:System.Windows.Forms.Button>элементы управления с именем `getCurrentCellButton` и `setCurrentCellButton`. В [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], необходимо присоединить <xref:System.Windows.Forms.Control.Click> событий для каждой кнопки в соответствующий обработчик событий в коде.  
  
-   элемент управления <xref:System.Windows.Forms.DataGridView> с именем `dataGridView1`;  
  
-   ссылки на сборки <xref:System?displayProperty=nameWithType> и <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>  
 [Базовые характеристики столбцов, строк и ячеек элемента управления DataGridView в Windows Forms](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Режимы выделения содержимого элемента управления DataGridView в Windows Forms](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)
