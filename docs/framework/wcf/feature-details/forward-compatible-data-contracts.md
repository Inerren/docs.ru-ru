---
title: "Контракты данных, совместимые с любыми будущими изменениями"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: data contracts [WCF], forward compatibility
ms.assetid: 413c9044-26f8-4ecb-968c-18495ea52cd9
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ef25e349ca6245ff3247f3a136d9a950d03d81d5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="forward-compatible-data-contracts"></a>Контракты данных, совместимые с любыми будущими изменениями
Одной из функций системы контрактов данных [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] является развитие контрактов без внесения критических изменений. Это значит, что клиент, использующий старую версию контракта данных, может взаимодействовать со службой, использующей новую версию того же контракта данных, или клиент, использующий новую версию контракта данных, может взаимодействовать со службой, использующей старую версию того же контракта данных. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Советы и рекомендации: управление версиями контракта данных](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
 Большинство возможностей управления версиями можно применять по мере необходимости при создании новых версий существующего контакта данных. Тем не менее одну функцию управления версиями *циклической обработки*, должны быть построены в тип из первой версии для правильной работы.  
  
## <a name="round-tripping"></a>Полная совместимость версий  
 Полная совместимость версий обеспечивается, когда данные передаются от новой версии к старой и снова в новую версию контракта данных. Полная совместимость версий гарантирует сохранение всех данных. Включение полной совместимости версий обеспечивает прямую совместимость типа с любыми будущими изменениями, поддерживаемыми моделью управления версиями контрактов данных.  
  
 Полная совместимость версий для определенного типа возможна только в том случае, если этот тип реализует интерфейс <xref:System.Runtime.Serialization.IExtensibleDataObject>. Интерфейс имеет одно свойство: <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> (возвращение типа <xref:System.Runtime.Serialization.ExtensionDataObject>). Это свойство сохраняет любые данные из будущих версий контракта данных, неизвестные в текущей версии.  
  
### <a name="example"></a>Пример  
 Ниже представлен контракт данных, который не обладает прямой совместимостью с будущими изменениями.  
  
 [!code-csharp[C_DataContract#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#7)]
 [!code-vb[C_DataContract#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#7)]  
  
 Чтобы тип был совместим с будущими изменениями (такими как добавление нового члена данных с именем "phoneNumber"), необходимо реализовать интерфейс <xref:System.Runtime.Serialization.IExtensibleDataObject>.  
  
 [!code-csharp[C_DataContract#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#8)]
 [!code-vb[C_DataContract#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#8)]  
  
 Если инфраструктура [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] встречает данные, которые не являются частью исходного контракта данных, данные сохраняются в свойстве и хранятся в нем. Обработка данных выполняется только во временном хранилище. Если объект возвращается в место создания, также возвращаются исходные (неизвестные) данные. Следовательно, данные совершают круговой путь к исходной конечной точке и из нее без потерь. Однако следует помнить, что если в исходной конечной точке необходимо выполнить обработку данных, этого не произойдет, и конечная точка должна будет каким-либо образом обнаружить и применить изменение.  
  
 Тип <xref:System.Runtime.Serialization.ExtensionDataObject> не содержит открытых методов или свойств. Таким образом, невозможно получить прямой доступ к данным, хранящимся внутри свойства <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>.  
  
 Функцию полной совместимости версий можно отключить, присвоив свойству `ignoreExtensionDataObject` значение `true` в конструкторе <xref:System.Runtime.Serialization.DataContractSerializer> или присвоив свойству <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> значение `true` для атрибута <xref:System.ServiceModel.ServiceBehaviorAttribute>. Если эта функция выключена, десериализатор не будет заполнять свойство <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>, а сериализатор не будет выпускать содержимое свойства.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 <xref:System.Runtime.Serialization.ExtensionDataObject>  
 [Управление версиями контракта данных](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [Рекомендации. Управление версиями контракта данных](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
