---
title: "&lt;loadFromRemoteSources&gt; элемент"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 959073381ef936fa7c0b248419c8529deaee969f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ltloadfromremotesourcesgt-element"></a>&lt;loadFromRemoteSources&gt; элемент
Указывает, следует ли предоставлять полный уровень доверия сборки из удаленных источников.  
  
> [!NOTE]
>  Если вы перешли на этот раздел из-за сообщения об ошибке в списке ошибок проекта Visual Studio или ошибку построения, в разделе [как: использовать сборку из Интернета в Visual Studio](http://msdn.microsoft.com/en-us/d8635b63-89a0-41aa-90f4-f351b2111070).  
  
 \<configuration>  
\<Среда выполнения >  
\<loadFromRemoteSources >  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`enabled`|Обязательный атрибут.<br /><br /> Указывает, следует ли предоставлять полный уровень доверия сборки, загруженной из удаленных источников.|  
  
## <a name="enabled-attribute"></a>Атрибут enabled  
  
|Значение|Описание|  
|-----------|-----------------|  
|`false`|Не предоставляйте полное доверие приложениям из удаленных источников. Это значение по умолчанию.|  
|`true`|Предоставить полное доверие приложениям из удаленных источников.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|`configuration`|Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.|  
|`runtime`|Содержит сведения о параметрах инициализации среды выполнения.|  
  
## <a name="remarks"></a>Примечания  
 В .NET Framework версии 3.5 и более ранних версий Если сборка загружена из удаленного расположения сборки будет выполняться частичным доверием с набором прав, который зависит от зоны, в которой она была загружена. Например, если вы загрузили сборку с веб-сайта, она была загружена в зону Интернета и получила набор разрешений Интернета. Другими словами она выполнялась в изолированной Интернета. При попытке запустить эту сборку в [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] и более поздних версиях возникает исключение, необходимо либо явным образом создать "песочницу" для сборки (см. [как: выполнение частично доверенного кода в изолированной среде](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)), или выполнить его с полным доверием.  
  
 Элемент `<loadFromRemoteSources>` позволяет указать, что сборки, выполнявшиеся с частичным доверием в предыдущих версиях платформы .NET Framework, в платформе [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] и более поздних версиях следует выполнять с полным доверием. По умолчанию удаленные сборки не выполняются в [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] и более поздних версиях. Удаленную сборку необходимо запускать с полным доверием или создать для нее изолированный домен <xref:System.AppDomain>.  
  
> [!NOTE]
>  В [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] сборки в общих папках локальной сети выполняются по умолчанию с полным доверием; нет необходимости включать элемент `<loadFromRemoteSources>`.  
  
> [!NOTE]
>  Если приложение скопировано из Интернета, оно помечается ОС Windows как веб-приложение, даже если находится на локальном компьютере. Это обозначение можно изменить, изменив свойства файла, или можно использовать `<loadFromRemoteSources>` элемент для предоставления сборке полное доверие. Также можно использовать метод <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A>, чтобы загрузить локальную сборку, которую операционная система пометила как загруженную из Интернета.  
  
 `enabled` Атрибута для этого элемента действует только в том случае, при отключении управления доступом для кода (CAS). По умолчанию политика разграничения доступа кода отключена в [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] и более поздних версиях. Если задать `enabled` для `true`, удаленным приложениям предоставляется полное доверие.  
  
 Если `<loadFromRemoteSources>``enabled` равно `true`, возникает исключение при следующих условиях:  
  
-   Поведение «песочницы» для текущего домена отличается от его поведения в [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]. Требуется отключить политики разграничения доступа кода и текущий домен не в песочницу.  
  
-   Загружаемая сборка не из `MyComputer` зоны.  
  
> [!NOTE]
>  Может возникнуть <xref:System.IO.FileLoadException> в приложении Windows Virtual PC, при попытке загрузить файл из связанного папки на данном компьютере. Эта ошибка также может возникнуть при попытке загрузить файл из папки, заданной через [служб удаленных рабочих столов](http://go.microsoft.com/fwlink/?LinkId=182775) (службы терминалов). Чтобы избежать этого исключения, задайте `enabled` для `true`.  
  
 Установка `<loadFromRemoteSources>` элемент `true` предотвращает это исключение вызывается. Позволяет указать, что вы не полагаетесь на CLR для "песочницы" загруженных сборок для обеспечения безопасности и что они будет разрешено выполняться как полный уровень доверия.  
  
> [!IMPORTANT]
>  Если сборки не должно выполняться с полным доверием, не задавайте этот элемент конфигурации. Вместо этого создайте изолированное <xref:System.AppDomain> для загрузки сборки.  
  
## <a name="configuration-file"></a>Файл конфигурации  
 Этот элемент обычно используется в файле конфигурации приложения, но может использоваться в других файлах конфигурации в зависимости от контекста. Дополнительные сведения см. в статье [несколько неявных использует из политики разграничения доступа кода: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) в блоге безопасность платформы .NET.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как предоставить полное доверие приложениям из удаленных источников.  
  
```xml  
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>См. также  
 [Более неявного использования политики разграничения доступа кода: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839)  
 [Практическое руководство. Выполнение не вполне безопасного кода в изолированной среде](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [Схема параметров среды выполнения](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Схема файла конфигурации](../../../../../docs/framework/configure-apps/file-schema/index.md)
