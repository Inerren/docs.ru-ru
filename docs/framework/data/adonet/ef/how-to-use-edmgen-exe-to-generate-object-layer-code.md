---
title: "Практическое руководство. Использование EdmGen.exe для создания кода объектного уровня"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4abb20ca2ff26fa4e2105bae87274028592aa510
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a>Практическое руководство. Использование EdmGen.exe для создания кода объектного уровня
В этом разделе показано, как использовать [генератор модели EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) сформировать код уровня объекта на основе CSDL-файла.  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Создание кода уровня объекта для модели School в проекте Visual Basic с помощью EdmGen.exe  
  
1.  Создайте базу данных School. Дополнительные сведения см. в разделе [Создание образца базы данных School](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Создайте модель School или получите файл School.csdl. Дополнительные сведения см. в разделе [как: использование EdmGen.exe для создания модели и сопоставления файлов](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3.  Выполните в командной строке следующую команду (введя ее без разрывов строк):  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a>Создание кода уровня объектов для модели School в проекте С# с помощью программы EdmGen.exe  
  
1.  Создайте базу данных School. Дополнительные сведения см. в разделе [Создание образца базы данных School](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Создайте модель School или получите файл School.csdl. Дополнительные сведения см. в разделе [как: использование EdmGen.exe для создания модели и сопоставления файлов](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3.  Выполните в командной строке следующую команду (введя ее без разрывов строк):  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a>См. также  
 [Моделирование и сопоставление](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [Как: вручную настроить проект Entity Framework](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [Средства работы с моделью EDM ADO.NET](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [Как: заранее создать представления для повышения производительности запросов](http://msdn.microsoft.com/en-us/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [Как: использование EdmGen.exe для создания файлов модели и сопоставления](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
