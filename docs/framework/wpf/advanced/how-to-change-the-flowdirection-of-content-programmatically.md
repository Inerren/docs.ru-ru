---
title: "Как изменить FlowDirection содержимого программными средствами"
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
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ca4c94fe073fd618ca79d08812c42550594f445d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a>Как изменить FlowDirection содержимого программными средствами
В этом примере показано, как программно изменить <xref:System.Windows.FrameworkElement.FlowDirection%2A> свойство <xref:System.Windows.Controls.FlowDocumentReader>.  
  
## <a name="example"></a>Пример  
 Два <xref:System.Windows.Controls.Button> создаются элементы, каждый из которых представляет одно из возможных значений <xref:System.Windows.FlowDirection>. При нажатии кнопки значение связанного свойства применяется к содержимому <xref:System.Windows.Controls.FlowDocumentReader> с именем `tf1`.  Значение свойства также записывается <xref:System.Windows.Controls.TextBlock> с именем `txt1`.  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a>Пример  
 События, связанные с нажатием кнопки, определенные выше, обрабатываются в [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] файл кода программной части.  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
