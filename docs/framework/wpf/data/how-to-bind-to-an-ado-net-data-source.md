---
title: "Практическое руководство. Привязка к источнику данных ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0eb555bb9f21385d2d0b66fe0dd39112c8350dec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>Практическое руководство. Привязка к источнику данных ADO.NET
В этом примере показано, как привязать [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> управления [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`.  
  
## <a name="example"></a>Пример  
 В этом примере объект `OleDbConnection` используется для подключения к источнику данных, который представляет собой файл `Access MDB`, указанный в строке подключения. После установления соединения создается объект `OleDbDataAdpater`. Объект `OleDbDataAdpater` выполняет запрос select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] для извлечения набора записей из базы данных. Результаты выполнения команды [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] хранятся в `DataTable` элементе `DataSet` путем вызова метода `Fill` класса `OleDbDataAdapter`. `DataTable` в этом примере назван `BookTable`. Затем в примере задаются <xref:System.Windows.FrameworkElement.DataContext%2A> свойство <xref:System.Windows.Controls.ListBox> для `DataSet` объекта.  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Затем можно привязать <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> свойство <xref:System.Windows.Controls.ListBox> для `BookTable` из `DataSet`:  
  
 [!code-xaml[ADODataSet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]  
  
 `BookItemTemplate`— <xref:System.Windows.DataTemplate> , определяющий способ отображения данных:  
  
 [!code-xaml[ADODataSet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]  
  
 `IntColorConverter` преобразует `int` в цвет. С помощью этого преобразователя <xref:System.Windows.Controls.TextBlock.Background%2A> цвет третьего <xref:System.Windows.Controls.TextBlock> появляется зеленая Если значение `NumPages` является менее 350 и красное — в противном случае. Здесь не приведена реализация преобразователя.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Data.BindingListCollectionView>  
 [Общие сведения о привязке данных](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Разделы практического руководства](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
