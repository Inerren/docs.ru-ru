---
title: "Разработка параметров"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7d49c4263517830f46b1416684c7d9b874cda4db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="parameter-design"></a>Разработка параметров
В этом разделе приведены общие рекомендации по разработке параметра, включая разделы с рекомендациями по проверке аргументов. Кроме того, вы должны обращаться к инструкциям, описанным в [именования параметров](../../../docs/standard/design-guidelines/naming-parameters.md).  
  
 **✓ СДЕЛАТЬ** использовать бы производный тип параметра, который предоставляет функциональные возможности, необходимые для элемента.  
  
 Например предположим, что требуется разработать метод, который перечисляет коллекцию и печатает каждого элемента на консоль. Такой метод должен принимать <xref:System.Collections.IEnumerable> как параметр, не <xref:System.Collections.ArrayList> или <xref:System.Collections.IList>, например.  
  
 **X не** использовать зарезервированные параметры.  
  
 При необходимости дальнейшего ввода данных на член в одной из будущих версий могут добавляться новой перегрузкой.  
  
 **X не** открытым методы, принимающие указатели, массивы указателей или многомерных массивов в качестве параметров.  
  
 Указатели и многомерные массивы являются довольно сложно использовать правильно. В большинстве случаев API-интерфейсы можно изменено таким образом, чтобы избежать создания этих типов в качестве параметров.  
  
 **СДЕЛАТЬ ✓** поместите все `out` параметров после всех по значению и `ref` параметров (за исключением массивы параметров), даже если это приводит к несогласованность параметров перегрузки в (см. [члена Перегрузка](../../../docs/standard/design-guidelines/member-overloading.md)).  
  
 `out` Параметров можно рассматривать как дополнительный возвращаемые значения и сгруппировать их метод подпись становится проще для понимания.  
  
 **✓ СДЕЛАТЬ** быть согласованы в именовании параметров при перегрузке членов или реализации интерфейсов.  
  
 Это лучше взаимодействует связь между методами.  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a>Выбор между Enum и логических параметров  
 **✓ СДЕЛАТЬ** использовать перечисления, если член будет иметь два или более логических параметров.  
  
 **X не** используйте логические значения, пока не будет точно знать, никогда не возникнет необходимость использования более двух значений.  
  
 Перечисления предоставляют некоторый запас будущих сложения значений, но следует иметь в виду возможное влияние добавления значения перечисления, которые описаны в [разработки перечисления](../../../docs/standard/design-guidelines/enum.md).  
  
 **✓ Попробуйте** с помощью логических значений для параметров конструктора, действительно два значения состояния и используются исключительно для инициализации свойства типа Boolean.  
  
### <a name="validating-arguments"></a>Проверка аргументов  
 **✓ СДЕЛАТЬ** проверить аргументы, передаваемые открытый, защищенный или явно реализованный членов. Исключение <xref:System.ArgumentException?displayProperty=nameWithType>, или одного из его подклассов, если проверка завершается с ошибкой.  
  
 Обратите внимание, что фактическая проверка не обязательно должен выполняться в сам открытого или защищенного члена. Он может произойти на более низком уровне в подпрограмме некоторые закрытым или внутренним. Самое главное заключается в, всей области, которые доступны для конечных пользователей, выполняет проверку аргументов.  
  
 **СДЕЛАТЬ ✓** throw <xref:System.ArgumentNullException> Если передается аргумент null и элемент не поддерживает аргументы null.  
  
 **✓ СДЕЛАТЬ** проверки для параметров перечислений.  
  
 Не предполагается, что аргументы enum будет находиться в диапазоне, определяемом перечисления. Среда CLR позволяет преобразовать любое целочисленное значение в значение перечисления, даже если значение не определено для enum.  
  
 **X не** использовать <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> диапазона перечисления проверяет.  
  
 **✓ СДЕЛАТЬ** Имейте в виду, что изменяемые аргументы могут были изменены после они были проверены.  
  
 Если член является влияет на безопасность, вы, рекомендуется создать копию, а затем проверить и обработать аргумент.  
  
### <a name="parameter-passing"></a>Передача параметров  
 С точки зрения конструктор framework есть три основные группы параметров: параметры, по значению `ref` параметров, и `out` параметров.  
  
 Если аргумент, переданный через параметр по значению, член получает копию фактический аргумент, передаваемый в. Если аргумент имеет тип значения, копию аргумента помещается в стек. Если аргумент является ссылочным типом, копии ссылки помещается в стек. Наиболее популярных языков среды CLR, например C#, VB.NET и C++, по умолчанию для передачи параметров по значению.  
  
 При передаче аргумента через `ref` параметр, член получает ссылку на фактический аргумент, передаваемый в. Если аргумент имеет тип значения, ссылка на аргумент помещается в стек. Если аргумент является ссылочным типом, ссылку на ссылку помещается в стек. `Ref`параметры могут использоваться, чтобы разрешить члена, который требуется изменить аргументы, передаваемые вызывающей стороной.  
  
 `Out`параметры аналогичны `ref` параметров имеются небольшие отличия. Параметр вначале считается неназначенным и не удается прочитать в тексте элемента перед его присваиванием какое-либо значение. Кроме того параметр должен быть назначен некоторого значения, до возвращения элемента.  
  
 **X ИЗБЕГАЙТЕ** с помощью `out` или `ref` параметров.  
  
 С помощью `out` или `ref` параметров разработчика требуется опыт работы с указателями, понимание отличия между типами значения и ссылочными типами и умение работать с методами с несколькими возвращаемыми значениями. Кроме того, разница между `out` и `ref` параметры далеко не все понимают. Архитекторы Framework проектирование для широкого использования, не следует ожидать пользователям разрабатывающим `out` или `ref` параметров.  
  
 **X не** передачи ссылочных типов по ссылке.  
  
 Существует несколько исключений правила, например метод, который может использоваться для замены ссылок.  
  
### <a name="members-with-variable-number-of-parameters"></a>Члены с переменным количеством параметров  
 Члены, которые могут принимать переменное число аргументов выражаются, предоставляя параметр массива. Например <xref:System.String> предоставляет следующий метод:  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 Пользователь может затем вызвать <xref:System.String.Format%2A?displayProperty=nameWithType> метод следующим образом:  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 Добавление ключевого слова params C# к параметру массива изменения параметра на параметр params, так называемые массива и предоставляет ярлык для создания временного массива.  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 Это дает пользователю возможность вызвать метод путем передачи массива элементов непосредственно в списке аргументов.  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 Обратите внимание, что ключевого слова params могут добавляться только в качестве последнего параметра в списке параметров.  
  
 **✓ Попробуйте** Добавление ключевого слова params параметров массива, если ожидается, что конечных пользователей для передачи массивов с небольшим числом элементов. Если ожидается, что большое количество элементов будут передаваться общих сценариев, пользователи, скорее всего, не будет передавать эти встроенные элементы все равно, и ключевого слова params не требуется.  
  
 **X ИЗБЕГАЙТЕ** использование массивов params в том случае, если вызывающий объект будет почти всегда уже входные данные в виде массива.  
  
 Например элементы с помощью параметров-массивов байтов практически никогда не называется путем передачи отдельных байтов. По этой причине параметров массива байтов в .NET Framework следует использовать ключевого слова params.  
  
 **X не** используйте массивы params, если массив изменен членом, принимающим параметр params массива.  
  
 Из-за того, что многие компилятор преобразует аргументы для члена во временный массив во время вызова массив может быть временным объектом и таким образом будут потеряны все изменения в массив.  
  
 **✓ Попробуйте** с помощью ключевого слова params в простой перегрузке, даже если более сложная перегрузка не может использовать его.  
  
 Спросите себя, если пользователи ценят, с массивом параметров в одной перегрузке, даже если это не было все перегрузки.  
  
 **✓ СДЕЛАТЬ** попытайтесь Упорядочить параметры, чтобы сделать возможным использование ключевого слова params.  
  
 **✓ Попробуйте** предусматривать особые перегрузки и ветви кода для вызовов с небольшим числом аргументов в API-интерфейсы важна высокая производительность.  
  
 Это позволяет избежать создания объектов массива, при вызове API с небольшим числом аргументов. Имена параметров формы путем установки единственном параметра массива и добавление числовой суффикс.  
  
 Следует только для этого при для особых случаев путь весь код, не просто создать массив и вызвать метод с более общими.  
  
 **✓ СДЕЛАТЬ** Имейте в виду, null может быть передан в качестве аргумента массива params.  
  
 Следует проверить, что массив не является null перед обработкой.  
  
 **X не** использовать `varargs` методы, также известный как кнопку с многоточием.  
  
 Некоторые языки среды CLR, например C++, поддерживает альтернативные соглашение для передачи вызывается списки параметров переменных `varargs` методы. Соглашение о следует не используется в платформах, так как он не является CLS-совместимым.  
  
### <a name="pointer-parameters"></a>Параметры-указатели  
 В общем случае указатели не должны отображаться в общую контактную зону framework хорошо спроектированной управляемого кода. В большинстве случаев, должны инкапсулироваться указатели. Однако в некоторых случаях указатели являются обязательными в целях взаимодействия, и с использованием указателей в таких случаях подходит.  
  
 **✓ СДЕЛАТЬ** предоставляют альтернативный для любого элемента, который принимает указатель в качестве аргумента, так как указатели не являются CLS-совместимыми.  
  
 **X ИЗБЕГАЙТЕ** затратного контроля аргументов указатель аргументов.  
  
 **✓ СДЕЛАТЬ** соглашениям общих указателей при разработке члены с указателями.  
  
 Например нет необходимости для передачи начальный индекс, так как для достижения такого же результата можно использовать простые расчеты с указателями.  
  
 *Фрагменты © 2005, 2009 корпорации Майкрософт. Все права защищены.*  
  
 *Перепечатываются разрешении Пирсона для образовательных учреждений, Inc. из [Framework рекомендации по проектированию: условные обозначения, стили и шаблоны для библиотеки .NET для повторного использования, 2-е издание](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina и Брэд Абрамс, опубликованные 22 октября 2008 г., Addison-Wesley Professional в составе ряда разработки Microsoft Windows.*  
  
## <a name="see-also"></a>См. также  
 [Рекомендации по разработке членов](../../../docs/standard/design-guidelines/member.md)  
 [Рекомендации по проектированию на основе Framework](../../../docs/standard/design-guidelines/index.md)
