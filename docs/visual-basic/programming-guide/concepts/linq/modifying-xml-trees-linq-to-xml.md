---
title: "Изменение деревьев XML (LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de66788186f3ffd09560d8eacdebbbaa5edf067c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a>Изменение деревьев XML (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] служит для хранения XML-дерева в памяти. После загрузки или синтаксического анализа XML-дерева из источника [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] позволяет изменить это дерево, после чего его можно сериализовать, сохранив, например, в файл или отправив на удаленный сервер.  
  
 При изменении дерева на месте используются такие методы, как <xref:System.Xml.Linq.XContainer.Add%2A>.  
  
 Однако существует другой подход, который заключается в использовании функционального построения для создания нового дерева другой формы. В зависимости от типов изменений, которые необходимо внести в XML-дерево, а также в зависимости от размера самого дерева, этот подход может быть более надежным и простым для разработки. В первом разделе этой части приведено сравнение обоих подходов.  
  
## <a name="in-this-section"></a>Содержание  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Сравнение изменения дерева XML в памяти с Функциональное сборка (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md)|Сравниваются изменение XML-дерева в памяти и функциональное построение.|  
|[Добавление элементов, атрибутов и узлов в XML-дерева (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|Приводятся сведения о добавлении элементов, атрибутов или узлов к XML-дереву.|  
|[Изменение элементов, атрибутов и узлов в дереве XML](../../../../visual-basic/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|Приводятся сведения о добавлении существующих элементов, атрибутов или узлов.|  
|[Удаление элементов, атрибутов и узлов из XML-дерева (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|Приводятся сведения об удалении элементов, атрибутов или узлов из XML-дерева.|  
|[Обслуживание пар "имя значение" (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|Приводится описание того, как следует поддерживать сведения о приложении, которые лучше всего хранятся в парах «имя-значение», например сведения о настройках или глобальные настройки.|  
|[Как: изменить пространство имен для всего дерева XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|Показывается, как переместить XML-дерево из одного пространства имен в другое.|  
  
## <a name="see-also"></a>См. также  
 [Руководство по программированию (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
