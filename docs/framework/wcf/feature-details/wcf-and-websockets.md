---
title: "WCF и WebSockets"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 225bff20f514a653382f01becf133659dec4c5f0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-and-websockets"></a>WCF и WebSockets
В .NET Framework версии 4.5 добавлена поддержка WebSockets в службах Windows Communication Foundation.  WebSockets - это эффективная, основанная на стандартах технология, обеспечивающая двусторонний обмен сообщениями через стандартные HTTP-порты 80 и 443. Использование стандартных HTTP-портов позволяет WebSockets устанавливать связь по сети через посредников.  Были добавлены две стандартные привязки для поддержки обмена данными через транспорт WebSocket. <xref:System.ServiceModel.NetHttpBinding> и <xref:System.ServiceModel.NetHttpsBinding>. Специальные параметры WebSockets можно настроить на <xref:System.ServiceModel.Channels.HttpTransportBindingElement> , обратившись к <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> свойство.
  
## <a name="in-this-section"></a>Содержание  
 [Использование NetHttpBinding](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 Описывает <xref:System.ServiceModel.NetHttpBinding> и его настройку.  
  
 [Как: создание службы WCF, обменивающейся данными через WebSockets](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 Описывает процесс создания службы WCF, обменивающейся данными через Websockets.  
  
## <a name="reference"></a>Ссылка  
  
## <a name="related-sections"></a>Связанные разделы
