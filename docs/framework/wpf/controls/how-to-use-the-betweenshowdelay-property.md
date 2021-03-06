---
title: "Практическое руководство. Использование свойства BetweenShowDelay"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dca6dc7c6238ef4accc921818090237d17ce1cbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-betweenshowdelay-property"></a>Практическое руководство. Использование свойства BetweenShowDelay
В этом примере показано, как использовать <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> свойства времени, чтобы подсказки отображаются быстро — с минимумом или совсем без задержки — при перемещении пользователем указателя мыши с одной подсказки непосредственно на другую.  
  
## <a name="example"></a>Пример  
 В следующем примере <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> свойству одной секунды (1000 миллисекунд) и <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> задано равным двум секундам (2000 мс) для подсказок обоих <xref:System.Windows.Shapes.Ellipse> элементов управления. Если отображается подсказка одного из эллипсов, затем наведите указатель мыши на другой эллипс в течение двух секунд и Пауза на нем подсказка второго эллипса отображается немедленно.  
  
 В любом из следующих сценариев <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> применяется, чего подсказка для второго эллипса ожидания одной секунды до появления:  
  
-   Если время, необходимое для перемещения вторая кнопка является более двух секунд.  
  
-   Если подсказка не отображается в начале временного интервала для первого эллипса.  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [Разделы практического руководства](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [Общие сведения о всплывающих подсказках](../../../../docs/framework/wpf/controls/tooltip-overview.md)
