---
title: "Элемент &lt;localClientSettings&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cabde7eb9dd122c2f7060b2f2e2c16f5949dc1f3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="ltlocalclientsettingsgt-element"></a>Элемент &lt;localClientSettings&gt;
Задает параметры безопасности локального клиента для этой привязки.  
  
 \<system.serviceModel >  
\<привязки >  
\<customBinding >  
\<Привязка >  
\<Безопасность >  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<security>  
   <localClientSettings cacheCookies="Boolean"  
      cookieRenewalThresholdPercentage="Integer"  
      detectReplays="Boolean"  
      maxClockSkew="TimeSpan"  
      maxCookieCachingTime="TimeSpan"  
      reconnectTransportOnFailure="Boolean"  
      replayCacheSize="Integer"  
      replayWindow="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      timestampValidityDuration="TimeSpan" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`cacheCookies`|Логическое значение, указывающее, включено ли кэширование файлов cookie. Значение по умолчанию — `false`.|  
|`cookieRenewalThresholdPercentage`|Целое число, задающее максимальный процент файлов cookie, которые могут обновляться. Это значение должно быть в диапазоне от 0 до 100 включительно. Значение по умолчанию — 90.|  
|`detectReplays`|Логическое значение, показывающее, будут ли атаки с повторением обнаружены и ликвидированы на канале автоматически. Значение по умолчанию — `false`.|  
|`maxClockSkew`|Значение типа <xref:System.TimeSpan>, указывающее максимальный разброс времени между системными часами взаимодействующих сторон. Значение по умолчанию - 00:05:00.<br /><br /> Если задано значение по умолчанию, получатель принимает сообщения с отметками времени отправки, которое на пять минут раньше или позже времени получения сообщения. Сообщения, которые не прошли проверку времени отправки, отклоняются. Данная настройка используется в сочетании с атрибутом `replayWindow`.|  
|`maxCookieCachingTime`|Значение <xref:System.TimeSpan>, которое задает максимальное время существования файлов cookie. Значение по умолчанию - 10675199.02:48:05.4775807.|  
|`reconnectTransportOnFailure`|Логическое значение, указывающее, будет ли после транспортных сбоев выполняться попытка восстановления подключений, использующих режим обмена сообщениями WS-Reliable. По умолчанию используется значение `true`, что означает бесконечное число попыток повторного подключения. Цикл нарушается при возникновении тайм-аута бездействия, в результате чего канал вызывает исключение при невозможности повторного подключения.|  
|`replayCacheSize`|Положительное целое число, указывающее количество кэшированных параметров nonce, используемых для определения ответов. При превышении лимита самые старые параметры nonce удаляются, и создаются новые параметры nonce для новых сообщений. Значение по умолчанию — 500000.|  
|`replayWindow`|Значение типа <xref:System.TimeSpan>, которое указывает срок действия параметров nonce отдельного сообщения.<br /><br /> По истечении данного срока сообщение с тем же параметром nonce, что и у сообщения, отправленного ранее, приниматься не будет. Данный атрибут используется вместе с атрибутом `maxClockSkew` в целях предотвращения атак с повторением передачи пакетов. Злоумышленник может повторно отправить сообщение после закрытия окна повторной отправки сообщения. Данное сообщение, тем не менее, не пройдет проверку `maxClockSkew`, в результате которой отклоняются сообщения с отметками времени отправки, превышающими указанный период до или после времени получения сообщения.|  
|`sessionKeyRenewalInterval`|Значение <xref:System.TimeSpan>, которое задает интервал времени, по истечении которого инициатор будет обновлять ключ сеанса безопасности. Значение по умолчанию - 10:00:00.|  
|`sessionKeyRolloverInterval`|Значение <xref:System.TimeSpan>, которое задает интервал времени, в течение которого предыдущий сеансовый ключ остается действительным для входящих сообщений, пока выполняется обновление ключа. Значение по умолчанию - 00:05:00.<br /><br /> Во время обновления ключа отправка сообщения клиентом и сервером всегда должна выполняться с помощью самого последнего доступного ключа. Обе стороны принимают входящие сообщения, защищенные с помощью предыдущего сеансового ключа, вплоть до истечения времени смены ключа.|  
|`timestampValidityDuration`|Положительное значение типа <xref:System.TimeSpan>, указывающее срок действия отметки времени. Значение по умолчанию - 00:15:00.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Нет  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<Безопасность >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Задает параметры безопасности для пользовательской привязки.|  
|[\<secureConversationBootstrap >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Задает значения по умолчанию, используемые для инициализации службы безопасного обмена данными.|  
  
## <a name="remarks"></a>Примечания  
 Параметры являются локальными, в том смысле, что они не наследуются от политики безопасности службы.  
  
## <a name="see-also"></a>См. также  
 <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Привязки](../../../../../docs/framework/wcf/bindings.md)  
 [Расширение привязок](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Пользовательские привязки](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Как: Создание пользовательской привязки, с использованием элемента SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Безопасность пользовательской привязки](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
