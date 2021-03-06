---
title: "Практическое руководство. Определение маски ввода"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.MaskPropertyEditor
helpviewer_keywords: MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c136bd5bdacec04a011f728694550fb66ae6d897
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-set-the-input-mask"></a>Практическое руководство. Определение маски ввода
Элементе скрытого текстового поля является элементом поля расширенного текста, который поддерживает декларативный синтаксис для принятия или отклонения введенных пользователем данных. Установив свойство маски, можно указать допустимых входных данных без написания настраиваемую логику проверки в приложении. Дополнительные сведения см. в разделе «Примечания» <xref:System.Windows.Forms.MaskedTextBox> класса.  
  
## <a name="setting-the-mask-property-manually"></a>Установка свойства маски вручную  
 Если вы знакомы с символами, которые поддерживает свойство маски, можно ввести вручную. Сводка символов, которые поддерживает свойство маски, в разделе «Примечания» <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> свойство.  
  
#### <a name="to-set-the-mask-property-manually"></a>Чтобы задать свойство маски вручную  
  
1.  В **разработки** представление, выберите <xref:System.Windows.Forms.MaskedTextBox>.  
  
2.  В **свойства** окна, найдите <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> свойство.  
  
3.  Введите маску, которая требуется. Например, введите `###`.  
  
## <a name="using-the-input-mask-dialog-box"></a>С помощью диалогового окна маски ввода  
 Диалоговое окно маски ввода предоставляет несколько предопределенных масок ввода. Можно также изменить предопределенные маски или ввести собственную маску вручную.  
  
#### <a name="to-open-the-input-mask-dialog-box"></a>Чтобы открыть диалоговое окно маска ввода  
  
1.  В **разработки** представление, выберите <xref:System.Windows.Forms.MaskedTextBox>.  
  
    1.  Щелкните смарт-тег, чтобы открыть **задачи MaskedTextBox** панель.  
  
    2.  Нажмите кнопку **Установка маски**.  
  
     \- или -  
  
    1.  В **свойства** выберите <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> свойство.  
  
    2.  Нажмите кнопку с многоточием в столбце значений свойств.  
  
     **Маска ввода** откроется диалоговое окно.  
  
#### <a name="to-use-the-input-mask-dialog-box"></a>Чтобы воспользоваться диалоговым окном маска ввода  
  
1.  (Необязательно) Щелкните одну из стандартных масок в списке.  
  
2.  (Необязательно) Изменения в стандартные маски **маска** поле.  
  
3.  (Необязательно) Введите новую маску в **маска** поле. То есть используйте одну из стандартных масок нет.  
  
    > [!NOTE]
    >  В окне предварительного просмотра отобразится символы, которые пользователь видит в <xref:System.Windows.Forms.MaskedTextBox>. Эти символы имеются помогает пользователю правильно ввести данные.  
  
4.  Установите или снимите **использовать ValidatingType** флажок. **Использовать ValidatingType** флажок указывает, используется ли тип данных для проверки данных, введенных пользователем. Дополнительные сведения см. в описании свойства <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>.  
  
5.  Нажмите кнопку **ОК**.  
  
     Маска вводится в **маска** свойство в **свойства** окна.  
  
## <a name="see-also"></a>См. также  
 [Пример. Работа с элементом управления MaskedTextBox](../../../../docs/framework/winforms/controls/walkthrough-working-with-the-maskedtextbox-control.md)
