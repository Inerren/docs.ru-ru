---
title: "Практическое руководство. Получение свойств объекта системы печати без отражения"
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
helpviewer_keywords: PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2f6015d25ee8868fe9b4c6dcf3bf145d413521e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a>Практическое руководство. Получение свойств объекта системы печати без отражения
Использование отражения для перечисления свойств (и типов этих свойств) в объекте может снизить производительность приложения. <xref:System.Printing.IndexedProperties> Пространство имен служит для передачи этой информации с помощью отражения.  
  
## <a name="example"></a>Пример  
 Ниже приведены действия по созданию.  
  
1.  Создайте экземпляр типа. В следующем примере тип — <xref:System.Printing.PrintQueue> , поставляемый с [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], но почти те же код должен работать для типов, производных от <xref:System.Printing.PrintSystemObject>.  
  
2.  Создание <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> по типу <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>. <xref:System.Collections.DictionaryEntry.Value%2A> Каждой записи в этом словаре является объектом одного из типов, производных от <xref:System.Printing.IndexedProperties.PrintProperty>.  
  
3.  Перечислять элементы словаря. Для каждого из них выполните следующие действия.  
  
4.  Приведите значение каждого элемента в <xref:System.Printing.IndexedProperties.PrintProperty> и использовать его для создания <xref:System.Printing.IndexedProperties.PrintProperty> объекта.  
  
5.  Получить тип <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> каждого из <xref:System.Printing.IndexedProperties.PrintProperty> объекта.  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.Printing.IndexedProperties.PrintProperty>  
 <xref:System.Printing.PrintSystemObject>  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [Документы в WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Общие сведения о печати](../../../../docs/framework/wpf/advanced/printing-overview.md)
