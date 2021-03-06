---
title: "Практическое руководство. Преобразование кисти"
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
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a36ba5bce60b88d662f03fcff75a6fa04cad039d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-transform-a-brush"></a>Практическое руководство. Преобразование кисти
В этом примере показано, как преобразовывать <xref:System.Windows.Media.Brush> объектов с помощью двух свойств преобразования: <xref:System.Windows.Media.Brush.RelativeTransform%2A> и <xref:System.Windows.Media.Brush.Transform%2A>.  
  
 В следующих примерах используется <xref:System.Windows.Media.RotateTransform> для поворота содержимого <xref:System.Windows.Media.ImageBrush> на 45 градусов.  
  
 На следующем рисунке показана <xref:System.Windows.Media.ImageBrush> без <xref:System.Windows.Media.RotateTransform>, с <xref:System.Windows.Media.RotateTransform> применены к <xref:System.Windows.Media.Brush.RelativeTransform%2A> свойство и с <xref:System.Windows.Media.RotateTransform> применены к <xref:System.Windows.Media.Brush.Transform%2A> свойство.  
  
 ![Параметры RelativeTransform и Transform для кисти](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
## <a name="example"></a>Пример  
 В первом примере применяется <xref:System.Windows.Media.RotateTransform> для <xref:System.Windows.Media.Brush.RelativeTransform%2A> свойство <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.RotateTransform.CenterX%2A> И <xref:System.Windows.Media.RotateTransform.CenterY%2A> свойства <xref:System.Windows.Media.RotateTransform> объекта задаются 0,5, что является относительная координата центральной точки этого содержимого. В результате <xref:System.Windows.Media.ImageBrush> поворачивает содержимое по центру.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 Во втором примере также применяется <xref:System.Windows.Media.RotateTransform> для <xref:System.Windows.Media.ImageBrush>, однако в этом примере используется <xref:System.Windows.Media.Brush.Transform%2A> вместо <xref:System.Windows.Media.Brush.RelativeTransform%2A> свойство.  
  
 Чтобы сменить кисть по центру, в этом примере <xref:System.Windows.Media.RotateTransform.CenterX%2A> и <xref:System.Windows.Media.RotateTransform.CenterY%2A> свойства <xref:System.Windows.Media.RotateTransform> абсолютные координаты. Так как эта кисть рисует прямоугольник размером 175 на 90 пикселей, центральная точка прямоугольника имеет координаты (87,5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Описание того, как <xref:System.Windows.Media.Brush.RelativeTransform%2A> и <xref:System.Windows.Media.Brush.Transform%2A> свойства работы см. в разделе [Обзор преобразования кисти](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).  
  
 Полный пример см. в разделе [Примеры кистей](http://go.microsoft.com/fwlink/?LinkID=159973). Дополнительные сведения о кистях см. в разделе [Общие сведения о закраске сплошным цветом и градиентом](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о преобразованиях кистей](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)  
 [Общие сведения о закраске сплошным цветом и градиентом](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Общие сведения о классах Transform](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
