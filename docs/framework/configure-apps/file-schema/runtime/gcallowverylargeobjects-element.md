---
title: "&lt;gcAllowVeryLargeObjects&gt; элемент"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 49046c343ef749e597402f7e19a08fe1f2c98ca0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ltgcallowverylargeobjectsgt-element"></a>&lt;gcAllowVeryLargeObjects&gt; элемент
На 64 разрядных платформах позволяет использовать массивы, размер которых превышает 2 гигабайта (ГБ).  
  
 \<Конфигурация > элемент  
\<Среда выполнения > элемент  
\<gcAllowVeryLargeObjects > элемент  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`enabled`|Обязательный атрибут.<br /><br /> Указывает, включены ли массивы, которые больше, чем 2 ГБ в общий размер на 64-разрядных платформах.|  
  
## <a name="enabled-attribute"></a>Атрибут enabled  
  
|Значение|Описание|  
|-----------|-----------------|  
|`false`|Массивы с размером более 2 ГБ в общий размер не включены. Это значение по умолчанию.|  
|`true`|Массивы с размером более 2 ГБ в общий размер включены на 64-разрядных платформах.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|`configuration`|Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.|  
|`runtime`|Содержит сведения о параметрах инициализации среды выполнения.|  
  
## <a name="remarks"></a>Примечания  
 С помощью этого элемента в файле конфигурации приложения позволяет использовать массивы, размер которых превышает 2 ГБ, но не изменяет других ограничений на размер объекта и размер массива:  
  
-   Максимальное количество элементов в массиве является <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.  
  
-   Максимальный индекс в любой одного измерения — 2,147,483,591 (0x7FFFFFC7) для массивов байтов и массивы структур однобайтовых и 2,146,435,071 (0X7FEFFFFF) для других типов.  
  
-   Максимальный размер строк и другие не являющиеся массивами объектов не изменяется.  
  
> [!CAUTION]
>  Прежде чем включать эту функцию, убедитесь, что приложения содержат небезопасный код, который предполагается, что все массивы меньше, чем 2 ГБ. Например небезопасного кода, использующего массивы как буферов может быть уязвимо к переполнению буфера записывается на предположении, что массивы не может превышать 2 ГБ.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как включить эту функцию для приложения.  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>См. также  
 [Схема параметров среды выполнения](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Схема файла конфигурации](../../../../../docs/framework/configure-apps/file-schema/index.md)
