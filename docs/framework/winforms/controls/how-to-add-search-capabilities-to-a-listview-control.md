---
title: "Практическое руководство. Добавление в элемент управления ListView возможностей поиска"
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
- cpp
helpviewer_keywords:
- lists [Windows Forms], enabling searching
- list views [Windows Forms], enabling searching
- ListView control [Windows Forms], adding search capabilities
- searching [Windows Forms], adding search capabilities to ListView control
ms.assetid: 557782d9-b705-4bab-b496-9938afddac82
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fd6c3011b234f9d281a68a51fa8d9ef9d610816c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a>Практическое руководство. Добавление в элемент управления ListView возможностей поиска
Зачастую при работе с большой список элементов в <xref:System.Windows.Forms.ListView> элемента управления, необходимо предоставить пользователям возможности поиска. <xref:System.Windows.Forms.ListView> Управления обеспечивает такую функцию двумя способами: поиск совпадений текста и поиск расположений.  
  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A> Метод позволяет выполнять поиск текста в <xref:System.Windows.Forms.ListView> в представлении списка или подробных сведений, заданным строку поиска и необязательного начального и конечного индекса. Напротив <xref:System.Windows.Forms.ListView.FindNearestItem%2A> метод позволяет находить элементы в <xref:System.Windows.Forms.ListView> в представлении значков или эскизов, исходя из набора координат x и y и направление поиска.  
  
### <a name="to-find-an-item-using-text"></a>Чтобы найти элемент с помощью текста  
  
1.  Создание <xref:System.Windows.Forms.ListView> с <xref:System.Windows.Forms.ListView.View%2A> свойству присвоено <xref:System.Windows.Forms.View.Details> или <xref:System.Windows.Forms.View.List>, а затем заполнить <xref:System.Windows.Forms.ListView> с элементами.  
  
2.  Вызовите <xref:System.Windows.Forms.ListView.FindItemWithText%2A> метод, передав текст элемента, который требуется найти.  
  
3.  В следующем примере кода показано, как создать простую <xref:System.Windows.Forms.ListView>, заполнить его элементами и использовать введенный пользователем текст для поиска элемента в списке.  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a>Чтобы найти элемент с помощью координат x и y  
  
1.  Создание <xref:System.Windows.Forms.ListView> с <xref:System.Windows.Forms.View> свойству присвоено <xref:System.Windows.Forms.View.SmallIcon> или <xref:System.Windows.Forms.View.LargeIcon>, а затем заполнить <xref:System.Windows.Forms.ListView> с элементами.  
  
2.  Вызовите <xref:System.Windows.Forms.ListView.FindNearestItem%2A> метод, передав нужные координаты x и y — и направление поиска.  
  
3.  В следующем примере кода демонстрируется способ создания основных значок <xref:System.Windows.Forms.ListView>, заполнение ее элементов и отслеживания <xref:System.Windows.Forms.Control.MouseDown> событий для поиска ближайшего элемента по оси вверх.  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A>  
 <xref:System.Windows.Forms.ListView.FindNearestItem%2A>  
 [Элемент управления ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Общие сведения об элементе управления ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Практическое руководство. Добавление и удаление элементов с помощью элемента управления ListView в Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
