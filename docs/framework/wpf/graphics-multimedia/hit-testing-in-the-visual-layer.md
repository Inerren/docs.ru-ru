---
title: "Проверка попадания на визуальном уровне"
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
- hit testing functionality [WPF]
- visual layer [WPF], hit testing functionality
ms.assetid: b1a64b61-14be-4d75-b89a-5c67bebb2c7b
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 49fbb0c71b13ee7d7ca04e0d40c1f9e32230d805
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="hit-testing-in-the-visual-layer"></a>Проверка попадания на визуальном уровне
В этом разделе приведены общие сведения о функции проверки попадания, предоставляемой на визуальном уровне. Поддержка проверки попадания позволяет определить, попадает ли геометрический объект или точка в отображаемое содержимое <xref:System.Windows.Media.Visual>, что позволяет реализовать поведение пользовательского интерфейса, например прямоугольник выделения, чтобы выбрать несколько объектов.  
  
 
  
<a name="hit_testing_scenarios"></a>   
## <a name="hit-testing-scenarios"></a>Сценарии проверки попадания  
 <xref:System.Windows.UIElement> Класс предоставляет <xref:System.Windows.UIElement.InputHitTest%2A> метод, который служит для проверки нажатия элемента с использованием заданного значения координат. Во многих случаях <xref:System.Windows.UIElement.InputHitTest%2A> метод предоставляет необходимые функции для реализации попадания элементов. Однако существует несколько сценариев, в которых может потребоваться реализация проверки попадания на визуальном уровне.  
  
-   Попадания отличных<xref:System.Windows.UIElement> объектов: это применимо, если нажать тестирование отличных<xref:System.Windows.UIElement> объекты, такие как <xref:System.Windows.Media.DrawingVisual> или графических объектов.  
  
-   Проверка попадания с использованием геометрического объекта: это применимо, если нужно проверить попадание с использованием геометрического объекта, а не значения координат точки.  
  
-   Проверка попадания для нескольких объектов: это применимо, когда нужно проверить попадание для нескольких объектов, например перекрывающихся объектов. Можно получить результаты для всех визуальных объектов, пересекающих геометрический объект или точку, а не только для первого из них.  
  
-   Пропуск <xref:System.Windows.UIElement> политики проверки попадания: он применяется, когда необходимо игнорировать <xref:System.Windows.UIElement> политику, которая принимает во внимание такие факторы, как ли отключен элемент или недоступные для проверки нажатия.  
  
> [!NOTE]
>  Пример полного кода, иллюстрирующего проверку попадания на визуальном уровне, см. в разделе [Пример проверки попадания с помощью DrawingVisuals](http://go.microsoft.com/fwlink/?LinkID=159994) и [Пример взаимодействия проверки попадания с Win32](http://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="hit_testing_support"></a>   
## <a name="hit-testing-support"></a>Поддержка проверки попадания  
 Назначение <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> методы в <xref:System.Windows.Media.VisualTreeHelper> класса — определить, является ли значение координаты геометрического или точка в отображаемое содержимое заданного объекта, например элемент управления или графический элемент. Например, можно использовать проверку попадания для определения, попадает ли щелчок мышью в ограничивающем прямоугольнике объекта в границы фигуры круга. Можно также переопределить реализацию проверки попадания по умолчанию для выполнения собственных вычислений по проверке попадания.  
  
 На следующем рисунке показана связь между областью не прямоугольного объекта и ограничивающим его прямоугольником.  
  
 ![Схема области допустимым проверки](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
Допустимая область проверки попадания  
  
<a name="hit_testing_and_z-order"></a>   
## <a name="hit-testing-and-z-order"></a>Проверка попадания и порядок по оси Z  
 Визуальный уровень [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] поддерживает проверку попадания для всех объектов, в которых находится точка или геометрическая фигура, а не только для самого верхнего. Результаты возвращаются в порядке по оси z. Однако визуальный объект, который передается как параметр для <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> метод определяет, какие части визуального дерева, который будет достигнута тестирования. Можно проверять на попадание все визуальное дерево или любую его часть.  
  
 На следующем рисунке объект-круг расположен поверх объектов квадрат и треугольник. Если вас интересуют только попадания, значение которого z порядка самый верхний визуальный объект, можно задать перечисления visual проверки нажатия для возврата <xref:System.Windows.Media.HitTestResultBehavior.Stop> из <xref:System.Windows.Media.HitTestResultCallback> для остановки прохождения проверки попадания после первого элемента.  
  
 ![Схема z-45; порядок для визуального дерева](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
Z-порядок для визуального дерева  
  
 Если требуется перечислить все визуальные объекты в определенный момент или геометрии, возвращают <xref:System.Windows.Media.HitTestResultBehavior.Continue> из <xref:System.Windows.Media.HitTestResultCallback>. Это означает, что можно выполнять проверку попадания для визуальных объектов, которые находятся под другими объектами, даже если они полностью не видны. Более подробные сведения см. в примере кода в разделе «Использование обратного вызова результатов проверки попадания».  
  
> [!NOTE]
>  Проверку попадания можно выполнять и для прозрачного визуального объекта.  
  
<a name="using_default_hit_testing"></a>   
## <a name="using-default-hit-testing"></a>Проверка попадания по умолчанию  
 Можно определить, расположена ли точка внутри визуального объекта с помощью <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> метод для указания визуального объекта и точкой координации значение для проверки. Параметр-визуальный объект определяет начальную точку в визуальном дереве для поиска при проверке попадания. Найденные визуального объекта в визуальном дереве которого геометрия содержит координаты, ему присваивается <xref:System.Windows.Media.HitTestResult.VisualHit%2A> свойство <xref:System.Windows.Media.HitTestResult> объекта. <xref:System.Windows.Media.HitTestResult> Возвращается из <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> метод. Если с помощью визуального поддерева, срабатывают тестирования, не содержится точка <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> возвращает `null`.  
  
> [!NOTE]
>  Проверка попадания по умолчанию всегда возвращает самый верхний объект по оси Z. Чтобы определить все визуальные объекты, даже те, которые могут быть частично или полностью перекрыты, используйте обратный вызов результатов проверки попадания.  
  
 Недопустимое значение координаты, передается как параметр точки для <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> метод должен быть относительно координат визуального объекта нажатия проверку. Например, при наличии вложенных визуальных объектов, определенных в точке (100, 100) пространства координат родительского элемента, проверка попадания дочернего визуального объекта в (0, 0) эквивалентно проверке попадания в точке (100, 100) в пространстве координат родительского элемента.  
  
 Ниже показано, как настройка обработчиков событий мыши для <xref:System.Windows.UIElement> объект, используемый для записи событий, которые используются для проверки попадания.  
  
 [!code-csharp[HitTestingOverview#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>Влияние визуального дерева на проверку попадания  
 Начальная точка в визуальном дереве определяет, какие объекты возвращаются во время перечисления объектов проверки попадания. Если есть несколько объектов, для которых нужно выполнить проверку попадания, визуальные объект, используемый в качестве начальной точки в визуальном дереве, должен быть общим предком всех интересующих объектов. Например если нужно выполнить проверку попадания и для элемента-кнопки и для визуального объекта на следующем рисунке, необходимо установить начальную точку в визуальном дереве на их общего предка. В этом случае элемент общим предком элемента-кнопки и визуального объекта является элемент canvas.  
  
 ![Схема иерархии визуального дерева](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
Иерархия визуального дерева  
  
> [!NOTE]
>  <xref:System.Windows.UIElement.IsHitTestVisible%2A> Возвращает или задает значение, указывающее, является ли <xref:System.Windows.UIElement>-производного объекта может быть возвращен в качестве результата проверки нажатия в какой-либо части его отображаемого содержимого. Это позволяет выборочно изменять визуальное дерево, чтобы определить, какие визуальные объекты участвуют в проверке попадания.  
  
<a name="using_a_hit_test_result_callback"></a>   
## <a name="using-a-hit-test-result-callback"></a>Использование обратного вызова результатов проверки попадания  
 Можно перечислить в визуальном дереве все визуальные объекты, геометрия которых содержит заданное значение координат. Это позволяет выделить все визуальные объекты, даже те, которые могут быть частично или полностью перекрыты другими визуальными объектами. Для перечисления визуальных объектов в визуальном дереве используется <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> метод с помощью функции обратного вызова проверки нажатия. Функция обратного вызова проверки попадания вызывается системой, если указанное значение координат содержится в визуальном объекте.  
  
 Во время перечисления результатов проверки попадания не следует выполнять никакие операции по изменению визуального дерева. Добавление или удаление объектов визуального дерева во время его проверки может привести к непредсказуемому поведению. Можно безопасно изменить визуальное дерево после <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> возвращает метод. Может потребоваться предоставить структуру данных, таких как <xref:System.Collections.ArrayList>, для хранения значений во время перечисления результатов проверки нажатия.  
  
 [!code-csharp[HitTestingOverview#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 Метод обратного вызова проверки попадания определяет действия, которые выполняются при определении проверки попадания для конкретного визуального объекта в визуальном дереве. После выполнения этих действий возвращается <xref:System.Windows.Media.HitTestResultBehavior> значение, которое определяет, следует ли продолжать перечисление визуальных объектов или нет.  
  
 [!code-csharp[HitTestingOverview#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
>  Порядок перечисления визуальных объектов попадания соответствует их координатам по оси Z. Первым перечисляется визуальный объект с самой большой координатой по оси Z. Остальные визуальные объекты перечисляются по убыванию значения координаты по оси Z. Этот порядок перечисления соответствует порядку отрисовки визуальных объектов.  
  
 Можно остановить перечисление визуальных объектов в любое время в функции обратного вызова проверки нажатия, возвращая <xref:System.Windows.Media.HitTestResultBehavior.Stop>.  
  
 [!code-csharp[HitTestingOverview#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>   
## <a name="using-a-hit-test-filter-callback"></a>Использование обратного вызова фильтра проверки попадания  
 Можно использовать необязательный фильтр проверки попадания для ограничения объектов, которые передаются в качестве результатов проверки попадания. Это позволяет пропустить части визуального дерева, которые не нужны для обработки в результатах проверки нажатия. Для реализации фильтра проверки нажатия, определить функцию обратного вызова фильтра проверки нажатия и передайте его в качестве значения параметра, при вызове <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> метода.  
  
 [!code-csharp[HitTestingOverview#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 Если вы не хотите предоставить функции обратного вызова фильтра необязательно проверки нажатия, передайте `null` значение в качестве параметра для <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> метод.  
  
 [!code-csharp[HitTestingOverview#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![Создание визуального дерева, используя фильтр проверки нажатия](../../../../docs/framework/wpf/graphics-multimedia/media/filteredvisualtree-01.png "FilteredVisualTree_01")  
Обрезка визуального дерева  
  
 Функция обратного вызова фильтра проверки попадания позволяет перечислить все визуальные объекты, отображаемое содержимое которых содержит указанные координаты. Однако, может понадобиться пропустить отдельные части визуального дерева в функции обратного вызова результатов проверки нажатия. Возвращаемое значение функции обратного вызова фильтра проверки нажатия определяет, какой тип действия должен выполняться при перечислении визуальных объектов. Например, если возвращается значение <xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>, можно удалить текущий визуальный объект и его дочерние элементы из перечисления результатов проверки нажатия. Это означает, что функция обратного вызова результатов проверки попадания не увидит эти объекты в перечислении. Обрезка визуального дерева объектов позволяет уменьшить объем обработки во время перечисления результатов проверки попадания. В следующем примере кода фильтр пропускает метки и их потомков и проверяет все остальные объекты.  
  
 [!code-csharp[HitTestingOverview#106](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
>  Функция обратного вызова фильтра проверки попадания иногда вызывается в случаях, когда функция обратного вызова результатов проверки попадания не вызывается.  
  
<a name="overriding_default_hit_testing"></a>   
## <a name="overriding-default-hit-testing"></a>Переопределение проверки попадания по умолчанию  
 Можно переопределить визуального объекта по умолчанию попадания путем переопределения <xref:System.Windows.Media.Visual.HitTestCore%2A> метод. Это означает, что при вызове <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> метод, переопределенная реализация метода <xref:System.Windows.Media.Visual.HitTestCore%2A> вызывается. Переопределенный метод вызывается при попадании в ограничивающий прямоугольник визуального объекта, даже если координата не попадает в отображаемое содержимое визуального объекта.  
  
 [!code-csharp[HitTestingOverview#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 Иногда может понадобиться проверка попадания как для ограничивающего прямоугольника, так и для отображаемого содержимого визуального объекта. С помощью `PointHitTestParameters` значение параметра в переопределенном <xref:System.Windows.Media.Visual.HitTestCore%2A> метода в качестве параметра для базового метода <xref:System.Windows.Media.Visual.HitTestCore%2A>, выполняют действия над попадание ограничивающего прямоугольника визуального объекта и выполните второй проверку нажатия для к просмотру содержимого визуального объекта.  
  
 [!code-csharp[HitTestingOverview#108](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>  
 <xref:System.Windows.Media.HitTestResult>  
 <xref:System.Windows.Media.HitTestResultCallback>  
 <xref:System.Windows.Media.HitTestFilterCallback>  
 <xref:System.Windows.UIElement.IsHitTestVisible%2A>  
 [Использование образца взят проверки нажатия](http://go.microsoft.com/fwlink/?LinkID=159994)  
 [Попадания с примером взаимодействия Win32](http://go.microsoft.com/fwlink/?LinkID=159995)  
 [Проверка попадания геометрического объекта в визуальный объект](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)  
 [Проверка попадания с использованием контейнера узла Win32](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-a-win32-host-container.md)
