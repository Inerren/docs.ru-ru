---
title: "&lt;legacyCorruptedStateExceptionsPolicy&gt; элемент"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e4379f6f38c886504905483cefd7c7a6bbd519ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ltlegacycorruptedstateexceptionspolicygt-element"></a>&lt;legacyCorruptedStateExceptionsPolicy&gt; элемент
Указывает, допускает ли среда управляемому коду перехватывать нарушения прав доступа и другие исключения поврежденного состояния.  
  
 \<configuration>  
\<Среда выполнения >  
\<legacyCorruptedStateExceptionsPolicy >  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`enabled`|Обязательный атрибут.<br /><br /> Указывает, что приложение будет перехватывать сбои поврежденного состояния исключения например нарушения прав доступа.|  
  
## <a name="enabled-attribute"></a>Атрибут enabled  
  
|Значение|Описание|  
|-----------|-----------------|  
|`false`|Приложение не будет перехватывать сбои поврежденного состояния исключения например нарушения прав доступа. Это значение по умолчанию.|  
|`true`|Приложение будет перехватывать сбои поврежденного состояния исключения например нарушения прав доступа.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|`configuration`|Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.|  
|`runtime`|Содержит сведения о привязке сборок и сборке мусора.|  
  
## <a name="remarks"></a>Примечания  
 В .NET Framework версии 3.5 и более ранних версий общеязыковая среда выполнения может управляемый код для перехвата исключений, созданные в результате поврежденных состояний процесса. Нарушение прав доступа является примером такого типа исключения.  
  
 Начиная с [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], управляемый код больше не перехватывает исключения в этих типов `catch` блоков. Однако можно переопределить это изменение и продолжить обработку исключений поврежденного состояния двумя способами:  
  
-   Задать `<legacyCorruptedStateExceptionsPolicy>` элемента `enabled` атрибут `true`. Этот параметр конфигурации применяется целиком к процессу и влияет на все методы.  
  
 -или-  
  
-   Применить <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> атрибут к методу, который содержит исключения `catch` блока.  
  
 Этот элемент конфигурации доступен только в [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] и более поздних версий.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как указать, что в приложении должно использоваться поведение до [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]и перехватывать все сбои поврежденного состояния исключения.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>См. также  
 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>  
 [Схема параметров среды выполнения](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Схема файла конфигурации](../../../../../docs/framework/configure-apps/file-schema/index.md)
