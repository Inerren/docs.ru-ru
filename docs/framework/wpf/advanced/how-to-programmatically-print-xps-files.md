---
title: "Как печатать файлы XPS программным способом"
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
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 949d92e8599ee083593cbd7f970a9b37d31970ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-programmatically-print-xps-files"></a>Как печатать файлы XPS программным способом
Можно использовать перегрузку <xref:System.Printing.PrintQueue.AddJob%2A> метод печать [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] файлов без открытия <xref:System.Windows.Controls.PrintDialog> или, в принципе, все [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] вообще.  
  
 Также можно напечатать [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] файлов с помощью многие <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> и <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> методы <xref:System.Windows.Xps.XpsDocumentWriter>. Дополнительные сведения см. в разделе [Печать документа XPS](http://msdn.microsoft.com/en-us/849555c8-0c4e-48c0-86bc-a5494c69b36c).  
  
 Другой способ печати [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] заключается в использовании <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> или <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A> методы <xref:System.Windows.Controls.PrintDialog> элемента управления. См. раздел [Вызов диалогового окна печати](../../../../docs/framework/wpf/advanced/how-to-invoke-a-print-dialog.md).  
  
## <a name="example"></a>Пример  
 Необходимо с помощью параметра три основных шага <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> метода, как показано ниже. Подробные сведения см. в примере.  
  
1.  Определите, является ли принтер принтером XPSDrv. (Дополнительные сведения о XPSDrv см. в разделе [Обзор печати](../../../../docs/framework/wpf/advanced/printing-overview.md).)  
  
2.  Если принтер не является принтером XPSDrv, задайте однопотоковое подразделение потока.  
  
3.  Создайте экземпляр сервера печати и объект очереди печати.  
  
4.  Вызовите метод, указав имя задания, файл для печати и <xref:System.Boolean> флаг, указывающий, будет ли XPSDrv-принтеров.  
  
 В приведенном ниже примере показано, как выполнить пакетную печать всех файлов [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] в каталоге. Несмотря на то, что приложение предлагает пользователю указать каталог, тремя параметрами <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> методу не требуются [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Его можно использовать в любом пути кода при условии, что вы знаете имя файла [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] и путь, который вы можете ему передать.  
  
 Тремя параметрами <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> перегруженная версия <xref:System.Printing.PrintQueue.AddJob%2A> должна выполняться в однопотоковом подразделении всякий раз, когда <xref:System.Boolean> параметр `false`, который требуется при использовании принтера не XPSDrv. Однако по умолчанию состояние подразделения для [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] многопотоковое. Данное значение по умолчанию должно быть обращено, поскольку в этом примере предполагается, что принтер не является принтером XPSDrv.  
  
 Изменить значение по умолчанию можно одним из двух способов. Один способ — просто добавьте <xref:System.STAThreadAttribute> (т. е»`[System.STAThreadAttribute()]`») непосредственно над первой строки приложения `Main` метод (обычно «`static void Main(string[] args)`»). Однако многие приложения требуют `Main` метод имеет состояние многопотокового подразделения, поэтому существует второй метод: Поместите вызов в <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> в отдельном потоке, состояние подразделения которого задано значение <xref:System.Threading.ApartmentState.STA> с <xref:System.Threading.Thread.SetApartmentState%2A>. В следующем примере используется второй метод.  
  
 Соответственно, пример начинается с создания экземпляра <xref:System.Threading.Thread> объекта и его передачи **PrintXPS** метод как <xref:System.Threading.ThreadStart> параметр. (Метод **PrintXPS** определяется ниже в этом примере.) Затем для потока устанавливается однопотоковое подразделение. Остальной код метода `Main` начинается с нового потока.  
  
 Основу этого примера составляет метод `static` **BatchXPSPrinter.PrintXPS**. После создания сервера и очереди печати метод предлагает пользователю выбрать каталог, содержащий файлы [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]. После того, как существование каталога и наличие в нем XPS-файлов будет проверено, метод добавляет каждый такой файл в очередь печати. В примере предполагается, что принтер является не XPSDrv, поэтому мы передаем `false` для последнего параметра <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> метод. В связи с этим метод проверит разметку [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] в файле и только после этого конвертирует его в язык описания страниц принтера. Если проверка завершается ошибкой, выдается исключение. Код в примере перехватит исключение, сообщит о нем пользователю, а затем перейдет к обработке следующего файла [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 Если вы используете принтер XPSDrv, последнему параметру можно присвоить значение `true`. В этом случае, поскольку [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] является языком описания страниц принтера, метод отправляет файл на принтер без проверки или преобразования в другой язык описания страниц. Если имеются сомнения во время разработки ли приложение будет использовать принтер XPSDrv, можно изменить приложение для его чтения <xref:System.Printing.PrintQueue.IsXpsDevice%2A> свойство и ветвь в соответствии с его находит.  
  
 Поскольку сразу после выпуска [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] и [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] будут доступны всего несколько принтеров XSPSDrv, принтер, который не является принтером XPSDrv, можно замаскировать. Для этого добавьте файл Pipelineconfig.xml в список файлов в следующем разделе реестра компьютера, на котором выполняется ваше приложение:  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\*\<PseudoXPSPrinter>*\DependentFiles  
  
 где  *\<PseudoXPSPrinter>* — это любая очередь печати. После этого компьютер необходимо перезагрузить.  
  
 Эта маскировка позволит передать `true` как последний параметр <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> без вызова исключения, но поскольку  *\<PseudoXPSPrinter >* не представляет собой принтера XPSDrv, будет печататься только мусор.  
  
 **Примечание.** Для простоты в приведенном выше примере то, является ли файл [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)], проверяется по наличию расширения XPS. При этом файлы [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] не обязательно должны иметь такое расширение. [isXPS.exe (isXPS Conformance Tool)](http://msdn.microsoft.com/library/bfbb433f-7ab6-417a-90f0-71443d76bcb3) является одним из способов проверки файла на соответствие [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  
  
## <a name="see-also"></a>См. также  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.AddJob%2A>  
 <xref:System.Threading.ApartmentState>  
 <xref:System.STAThreadAttribute>  
 [РАСШИРЕННЫЕ ХРАНИМЫЕ ПРОЦЕДУРЫ](http://www.microsoft.com/xps)  
 [Печать документа XPS](http://msdn.microsoft.com/en-us/849555c8-0c4e-48c0-86bc-a5494c69b36c)  
 [Управляемые и неуправляемые потоки](http://msdn.microsoft.com/en-us/db425c20-4b2f-4433-bf96-76071c7881e5)  
 [isXPS.exe (средство проверки соответствия isXPS)](http://msdn.microsoft.com/library/bfbb433f-7ab6-417a-90f0-71443d76bcb3)  
 [Документы в WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Общие сведения о печати](../../../../docs/framework/wpf/advanced/printing-overview.md)
