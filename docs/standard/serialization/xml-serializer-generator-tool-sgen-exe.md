---
title: "Инструмент создания XML-сериализатора (Sgen.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 41f71519ee8945ae93b85e7f6ac2725bf50d4913
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="xml-serializer-generator-tool-sgenexe"></a>Инструмент создания XML-сериализатора (Sgen.exe)
Генератор XML-сериализатора создает сборку сериализации XML для типов в указанной сборке, чтобы повысить производительность при запуске <xref:System.Xml.Serialization.XmlSerializer> во время сериализации или десериализации объектов указанных типов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sgen [options]  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|------------|-----------------|  
|**/a**[**ssembly**]**:***имя_файла*|Создает код сериализации для всех типов, содержащихся в сборке, или исполняемого файла *имя_файла*. Можно указать только одно имя файла. Если этот аргумент повторяется, используется последнее имя файла.|  
|**/c[ompiler]:** *параметры*|Задает параметры, которые следует передать компилятору C#. Поддерживаются все параметры csc.exe по мере их передачи компилятору. Этот параметр можно использовать для указания того, что сборка должна быть подписана, и для указания файла ключа.|  
|**/d**[**ebug**]|Создает образ, который может использоваться с отладчиком.|  
|**/f[orce]**|Принудительно перезаписывает существующую сборку с одинаковым именем. Значение по умолчанию — **false**.|  
|**/help или /?**|Отображает синтаксис команд и параметров программы.|  
|**/k**[**eep**]|Предотвращает удаление созданных исходных файлов и других временных файлов после их компиляции в сборку сериализации. Этот параметр можно использовать, чтобы определить, создает ли инструмент код сериализации для определенного типа.|  
|**/n**[**ologo**]|Отключает отображение эмблемы Майкрософт при запуске.|  
|**/o**[**ut**]**:***путь*|Определяет каталог, в которой сохраняется созданная сборка. **Примечание**. Имя созданной сборки представляет собой имя входной сборки и "xmlSerializers.dll".|  
|**/p**[**roxytypes**]|Создает код сериализации только для типов прокси XML-веб-службы.|  
|**/r**[**eference**]**:***файлы_сборки*|Задает сборки, на которые ссылаются типы, требующие XML-сериализации. Принимает несколько файлов сборки, которые разделяются запятыми.|  
|**/s**[**ilent**]|Запрещает отображение сообщений об успешно выполненных операциях.|  
|**/t**[**ype**]**:***тип*|Создает код сериализации только для указанного типа.|  
|**/v**[**erbose**]|Отображает подробную выходную информацию для отладки. Содержит список типов из целевой сборки, которые невозможно сериализовать с помощью <xref:System.Xml.Serialization.XmlSerializer>.|  
|**/?**|Отображает синтаксис команд и параметров программы.|  
  
## <a name="remarks"></a>Примечания  
 Если генератор XML-сериализатора не используется, <xref:System.Xml.Serialization.XmlSerializer> создает код сериализации и сборку сериализации для каждого типа при каждом запуске приложения. Для повышения производительности при запуске XML-сериализации используйте инструмент Sgen.exe, чтобы создать такие сборки заранее. Эти сборки можно развернуть вместе с приложением.  
  
 Инструмент создания XML-сериализатора также повышает производительность клиентов, использующих прокси XML-веб-служб для связи с серверами, поскольку производительность процесса сериализации не снижается при первой загрузке типа.  
  
 Эти созданные сборки нельзя использовать на стороне сервера веб-службы. Этот инструмент предназначен только для клиентов веб-служб и сценариев ручной сериализации.  
  
 Если сборка, содержащая сериализуемый тип, называется "MyType.dll", связанная сборка сериализации будет называться "MyType.XmlSerializers.dll".  
  
## <a name="examples"></a>Примеры  
 Следующая команда создает сборку с именем "Data.XmlSerializers.dll" для сериализации всех типов, содержащихся в сборке с именем "Data.dll".  
  
```  
sgen Data.dll   
```  
  
 Код, для которого требуется сериализация и десериализация типов в Data.dll, может содержать ссылки на сборку Data.XmlSerializers.dll.  
  
## <a name="see-also"></a>См. также  
 [Инструменты](../../../docs/framework/tools/index.md)  
 [Обзор веб-служб XML](http://msdn.microsoft.com/en-us/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d)  
 [Командные строки](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
