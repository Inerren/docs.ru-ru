---
title: "Практическое руководство. Режимы изменения размеров элемента управления DataGridView в Windows Forms"
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
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 811c5edd2f12794035b66260f17255283f405cbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a>Практическое руководство. Режимы изменения размеров элемента управления DataGridView в Windows Forms
Следующие процедуры демонстрируют некоторые распространенные сценарии для настройки или комбинирования параметров изменения размеров, доступных для элемента управления <xref:System.Windows.Forms.DataGridView> и для определенных столбцов в элементе управления.  
  
### <a name="to-create-a-fixed-width-column"></a>Создание столбца с фиксированной шириной  
  
-   Задайте для свойства <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> значение <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, свойства <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> значение <xref:System.Windows.Forms.DataGridViewTriState.False>, свойства <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> значение `true` и свойства <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> соответствующее значение.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a>Создание столбца, который изменяет свой размер в соответствии с содержимым  
  
-   Задайте для свойства <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> значение режима изменения размера на основе содержимого.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a>Создание столбцов с заполнением для значений различного размера и важности  
  
-   Задайте для свойства <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> значение <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>, чтобы указать режим изменения размера для всех столбцов, которые не переопределяют это значение. Задайте свойствам <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> столбцов значения, которые будут указывать средние пропорции их ширины. Задайте свойства <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> для важных столбцов, чтобы обеспечить частичное отображение содержимого.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a>Пример  
 Ниже приводится полный код демонстрационного приложения, которое поможет лучше разобраться с изменениями размеров, описанными в этом разделе.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 Использование этого демонстрационного приложения.  
  
-   Измените размер формы. Обратите внимание, как меняется ширина столбцов с заполнением при сохранении пропорций, указанных в свойстве <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>. Обратите внимание, что столбец <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> не изменяется, если размер формы слишком мал.  
  
-   Измените размеры столбцов, перетаскивая их разделители с помощью мыши. Обратите внимание, что некоторые столбцы не могут изменять размер, а столбцы с изменяемой шириной нельзя сделать уже, чем их минимальная ширина.  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
-   ссылки на сборки System и System.Windows.Forms.  
  
 Информацию о выполнении сборки этого примера из командной строки для [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] или [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] можно найти в разделе [Построение из командной строки](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) или [Построение из командной строки с помощью файла csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Чтобы выполнить сборку этого примера в [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], можно также вставить код в новый проект.  См. также [Практическое руководство. Компиляция и выполнение откомпилированного примера кода формы Windows Forms с помощью Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
