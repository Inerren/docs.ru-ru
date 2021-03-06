---
title: "Взаимодействие WPF и Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d713a03469edc5d4c950c75c8094386372657486
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="wpf-and-windows-forms-interoperation"></a>Взаимодействие WPF и Windows Forms
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] и [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] представляют собой две различные архитектуры для создания интерфейсов приложений. <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> Пространство имен предоставляет классы, обеспечивающие общие сценарии взаимодействия. Ключевыми классами, реализующими возможности взаимодействия, <xref:System.Windows.Forms.Integration.WindowsFormsHost> и <xref:System.Windows.Forms.Integration.ElementHost>. В этом разделе описано, какие сценарии взаимодействия поддерживаются, а какие нет.  
  
> [!NOTE]
>  Особое внимание уделено сценарию *гибридного элемента управления*. Гибридный элемент управления — это элемент управления на основе одной технологии, в который вложен элемент управления на основе другой технологии. Это также называется *вложенным взаимодействием*. В *многоуровневом гибридном элементе управления* более одного уровня вложения. Примером многоуровневого вложенного взаимодействия является элемент управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], который содержит элемент управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], содержащий другой элемент управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Многоуровневые гибридные элементы управления не поддерживаются.  
  
  
<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>Размещение элементов управления Windows Forms в WPF  
 Если в элемент управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] вложен элемент управления [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)], поддерживаются перечисленные ниже сценарии взаимодействия.  
  
-   В элемент управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] с помощью XAML могут быть вложены один или несколько элементов управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
-   С помощью кода в него могут быть вложены один или несколько элементов управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
-   В него могут быть вложены контейнерные элементы управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], содержащие элементы управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
-   В него может быть вложена форма с отношением "главный-подчиненный" с главным элементом [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] и подчиненными элементами [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
-   В него может быть вложена форма с отношением "главный-подчиненный" с главным элементом [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] и подчиненными элементами [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   В него могут быть вложены один или несколько элементов [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)].  
  
-   В него могут быть вложены один или несколько составных элементов управления.  
  
-   С помощью [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] в него могут быть вложены гибридные элементы управления.  
  
-   С помощью кода в него могут быть вложены гибридные элементы управления.  
  
### <a name="layout-support"></a>Поддержка макета  
 Ниже перечислены известные ограничения при <xref:System.Windows.Forms.Integration.WindowsFormsHost> пытается интегрировать его вложенный элемент [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] управления в [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] система макета.  
  
-   В некоторых случаях размеры элемента управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] изменять нельзя, или же их можно изменять, но только в фиксированных пределах. Например [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> элемент управления поддерживает только одну высоту, которая определяется размером шрифта элемента управления. В [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] динамического макета, в котором предполагается, что элементы можно растянуть по вертикали, размещенных <xref:System.Windows.Forms.ComboBox> управления не растягивается, как ожидалось.  
  
-   Элементы управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] нельзя поворачивать или наклонять. Например, при повороте пользовательского интерфейса на 90 градусов вложенные элементы управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] сохранят свое вертикальное положение.  
  
-   В большинстве случаев элементы управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] не поддерживают пропорциональное масштабирование. Несмотря на то, что общий размер элемента управления масштабируется, дочерние элементы управления и компоненты элемента управления могут изменять размеры не так, как ожидается. Это ограничение зависит от поддержки масштабирования каждым элементом управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
-   В пользовательском интерфейсе [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] можно изменить z-порядок элементов для контроля поведения перекрывания. Вложенный элемент управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] рисуется в отдельном HWND, причем он всегда рисуется поверх элементов [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   Элементы управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] поддерживают автоматическое масштабирование в соответствии с размером шрифта. В пользовательском интерфейсе [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] изменение размера шрифта не влечет за собой изменение размера всего макета, хотя отдельные элементы могут динамически изменять размер.  
  
### <a name="ambient-properties"></a>Внешние свойства  
 Некоторые внешние свойства элементов управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] имеют эквиваленты [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Эти свойства окружения распространяются на вложенные [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] элементов управления и предоставляются как общие свойства на <xref:System.Windows.Forms.Integration.WindowsFormsHost> элемента управления. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Управления переводит каждое [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] свойство окружения в его [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] эквивалент.  
  
 Дополнительные сведения см. в разделе [Сопоставление свойств Windows Forms и WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Поведение  
 В приведенной ниже таблице описаны возможности взаимодействия.  
  
|Поведение|Поддерживается|Не поддерживается|  
|--------------|---------------|-------------------|  
|Прозрачность|Отрисовка элемента управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] поддерживает прозрачность. Фон родительского элемента управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] может стать фоном вложенного элемента управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].|Некоторые элементы управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] не поддерживают прозрачность. Например <xref:System.Windows.Forms.TextBox> и <xref:System.Windows.Forms.ComboBox> элементы управления не будет прозрачным, если они размещаются в [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|Переход по клавише TAB|Последовательность табуляции для вложенных элементов управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] та же, что и при вложении этих элементов управления в приложение, основанное на [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].<br /><br /> Переход от элемента управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] к элементу управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] по клавишам TAB и SHIFT+TAB работает как обычно.<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]элементы управления, имеющие <xref:System.Windows.Forms.Control.TabStop%2A> значение свойства `false` не получают фокус, когда пользователь переключается между элементами управления.<br /><br /> -Каждое <xref:System.Windows.Forms.Integration.WindowsFormsHost> управления имеет <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> значение, которое определяет, когда, <xref:System.Windows.Forms.Integration.WindowsFormsHost> элемент управления получает фокус.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]элементы управления, содержащиеся внутри <xref:System.Windows.Forms.Integration.WindowsFormsHost> контейнера выполните порядке, указанном <xref:System.Windows.Forms.Control.TabIndex%2A> свойство. При переходе от последнего индекса табуляции фокус получает следующий элемент управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], если таковой существует. Если нет других элементов управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], принимающих фокус, то переход по табуляции переводит фокус на первый элемент управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] в последовательности табуляции.<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>значения для элементов управления внутри <xref:System.Windows.Forms.Integration.WindowsFormsHost> относительно того же уровня [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] элементы управления, содержащиеся в <xref:System.Windows.Forms.Integration.WindowsFormsHost> элемента управления.<br />— При переходе по табуляции учитывается модель поведения элемента управления. Например, нажатие клавиши TAB в <xref:System.Windows.Forms.TextBox> управления, имеющий <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> значение свойства `true` вводит табуляции в текстовом поле, вместо перемещения фокуса.|Неприменимо.|  
|Переход с помощью клавиш со стрелками|-Ключи навигации со стрелкой в <xref:System.Windows.Forms.Integration.WindowsFormsHost> управления является такой же, как обычный [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] контейнерный элемент управления: клавиши Стрелка вверх и Стрелка влево выберите предыдущий элемент управления, а клавиши со стрелкой вниз и вправо выберите следующий элемент управления.<br />-Стрелками ключи из первого элемента управления, содержащегося в <xref:System.Windows.Forms.Integration.WindowsFormsHost> элемент управления выполняет те же действия, как сочетание клавиш SHIFT + TAB. Если имеется принимающий фокус [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] управления, фокус перемещается за пределы <xref:System.Windows.Forms.Integration.WindowsFormsHost> элемента управления. Это поведение отличается от стандартного <xref:System.Windows.Forms.ContainerControl> в том, что нет перехода к последнему управления происходит. Если нет других элементов управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], принимающих фокус, фокус возвращается к последнему элементу управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] в последовательности табуляции.<br />-НАЖАТЫМИ клавиши со стрелками и Стрелка вправо от последнего элемента, содержащегося в <xref:System.Windows.Forms.Integration.WindowsFormsHost> элемент управления выполняет те же действия, как нажатие клавиши TAB. Если имеется принимающий фокус [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] управления, фокус перемещается за пределы <xref:System.Windows.Forms.Integration.WindowsFormsHost> элемента управления. Это поведение отличается от стандартного <xref:System.Windows.Forms.ContainerControl> в том, что переноса на первый элемент управления не происходит. Если нет других элементов управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], принимающих фокус, то фокус возвращается к первому элементу управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] в последовательности перехода.|Неприменимо.|  
|Клавиши быстрого доступа|Клавиши быстрого доступа работают как обычно, за исключением пунктов, оговоренных в столбце "Не поддерживается".|Повторяющиеся в различных технологиях клавиши быстрого доступа не работают как обычные повторяющиеся клавиши быстрого доступа. При дублировании клавиш быстрого доступа в различных технологиях по крайней мере для одного элемента управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] и одного элемента управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] клавиша быстрого доступа всегда присваивается элементу управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Фокус не переключается между элементами управления с одинаковыми клавишами быстрого доступа.|  
|Сочетание клавиш|Сочетания клавиш работают как обычно, за исключением пунктов, оговоренных в столбце "Не поддерживается".|Сочетания клавиш -   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], заданные на этапе предварительной обработки, всегда имеют приоритет перед сочетаниями клавиш [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Например, если у вас есть <xref:System.Windows.Forms.ToolStrip> было управлять с помощью сочетания клавиш CTRL + S определены и [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] привязан к CTRL + S, команда <xref:System.Windows.Forms.ToolStrip> управления всегда вызывается обработчик во-первых, независимо от фокуса.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]сочетания клавиш, которые обрабатываются <xref:System.Windows.Forms.Control.KeyDown> события обрабатываются последними в [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Можно предотвратить такое поведение путем переопределения [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] элемента управления <xref:System.Windows.Forms.Control.IsInputKey%2A> метода или обработка <xref:System.Windows.Forms.Control.PreviewKeyDown> событий. Вернуть `true` из <xref:System.Windows.Forms.Control.IsInputKey%2A> метод, или задать значение <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> свойства `true` в ваш <xref:System.Windows.Forms.Control.PreviewKeyDown> обработчика событий.|  
|AcceptsReturn, AcceptsTab и другие специфические свойства элементов управления|Свойства, изменяющие поведение по умолчанию сочетания работу в обычном режиме, при условии, что [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] управления переопределений <xref:System.Windows.Forms.Control.IsInputKey%2A> метод для возврата `true`.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]элементы управления, изменяющие стандартное поведение клавиатуры при обработке <xref:System.Windows.Forms.Control.KeyDown> события обрабатываются последними в узле [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] элемента управления. Так как эти элементы управления обрабатываются последними, они могут привести к непредвиденному поведению.|  
|События Enter и Leave|Если фокус не будет, в котором содержится <xref:System.Windows.Forms.Integration.ElementHost> управления, ввод и оставьте событий в обычном режиме при смене фокуса в одном <xref:System.Windows.Forms.Integration.WindowsFormsHost> элемента управления.|События Enter и Leave не вызываются при следующих переводах фокуса:<br /><br /> -Из за <xref:System.Windows.Forms.Integration.WindowsFormsHost> элемента управления.<br />-Из внутрь <xref:System.Windows.Forms.Integration.WindowsFormsHost> элемента управления.<br />-Вне <xref:System.Windows.Forms.Integration.WindowsFormsHost> элемента управления.<br />-Из [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] размещение элементов управления в <xref:System.Windows.Forms.Integration.WindowsFormsHost> управления <xref:System.Windows.Forms.Integration.ElementHost> элемента управления, размещенного внутри того же <xref:System.Windows.Forms.Integration.WindowsFormsHost>.|  
|Многопоточность|Поддерживаются все возможности многопоточности.|И технология [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], и технология [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] предполагают однопоточную модель параллелизма. Во время отладки вызовы объектов платформы из других потоков будут вызывать исключение для принудительного выполнения этого требования.|  
|Безопасность|Все сценарии взаимодействия требуют полного доверия.|Не допускаются сценарии взаимодействия с частичным доверием.|  
|Специальные возможности|Поддерживаются все сценарии специальных возможностей. Продукты вспомогательной технологии работают корректно, когда они используются для гибридных приложений, содержащих как элементы управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], так и элементы управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Неприменимо.|  
|буфер обмена|Все операции с буфером обмена работают обычным образом. Сюда относятся операции вырезания и вставки между элементами управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] и [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Неприменимо.|  
|Функция перетаскивания|Все операции перетаскивания работают обычным образом. Сюда относятся операции перетаскивания между элементами управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] и [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Неприменимо.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Размещение элементов управления WPF в Windows Forms  
 Если в элемент управления [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] вложен элемент управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], поддерживаются перечисленные ниже сценарии взаимодействия.  
  
-   Вложение одного или нескольких элементов управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] с помощью кода.  
  
-   Связывание страницы свойств с одним или несколькими вложенными элементами управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   Вложение одной или нескольких страниц [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] в форму.  
  
-   Запуск окна [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   Вложение формы с отношением "главный-подчиненный" с главным элементом [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] и подчиненными элементами [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   Вложение формы с отношением "главный-подчиненный" с главным элементом [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] и подчиненными элементами [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
-   Вложение пользовательских элементов управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   Вложение гибридных элементов управления.  
  
### <a name="ambient-properties"></a>Внешние свойства  
 Некоторые внешние свойства элементов управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] имеют эквиваленты [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Эти свойства окружения распространяются на вложенные [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] элементов управления и предоставляются как общие свойства на <xref:System.Windows.Forms.Integration.ElementHost> элемента управления. <xref:System.Windows.Forms.Integration.ElementHost> Управления переводит каждое [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] свойств окружения для его [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] эквивалент.  
  
 Дополнительные сведения см. в разделе [Сопоставление свойств Windows Forms и WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Поведение  
 В приведенной ниже таблице описаны возможности взаимодействия.  
  
|Поведение|Поддерживается|Не поддерживается|  
|--------------|---------------|-------------------|  
|Прозрачность|Отрисовка элемента управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] поддерживает прозрачность. Фон родительского элемента управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] может стать фоном вложенного элемента управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Неприменимо.|  
|Многопоточность|Поддерживаются все возможности многопоточности.|И технология [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], и технология [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] предполагают однопоточную модель параллелизма. Во время отладки вызовы объектов платформы из других потоков будут вызывать исключение для принудительного выполнения этого требования.|  
|Безопасность|Все сценарии взаимодействия требуют полного доверия.|Не допускаются сценарии взаимодействия с частичным доверием.|  
|Специальные возможности|Поддерживаются все сценарии специальных возможностей. Продукты вспомогательной технологии работают корректно, когда они используются для гибридных приложений, содержащих как элементы управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], так и элементы управления [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Неприменимо.|  
|буфер обмена|Все операции с буфером обмена работают обычным образом. Сюда относятся операции вырезания и вставки между элементами управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] и [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Неприменимо.|  
|Функция перетаскивания|Все операции перетаскивания работают обычным образом. Сюда относятся операции перетаскивания между элементами управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] и [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Неприменимо.|  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Пошаговое руководство. Размещение элемента управления Windows Forms в приложении WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [Пошаговое руководство. Размещение составного элемента управления Windows Forms в приложении WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Пошаговое руководство. Размещение составного элемента управления WPF в форме Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [Сопоставление свойств Windows Forms и WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)
