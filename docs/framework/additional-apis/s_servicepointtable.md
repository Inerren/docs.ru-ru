---
title: "Поле ServicePointManager.s_ServicePointTable"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type: apiref
api_name: System.Net.ServicePointManager.s_ServicePointTable
api_location: System.dll
api_type: Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2f12a8ba4d2b84e5b5d73d26199adf687a95a2df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="servicepointmanagersservicepointtable-field"></a>ServicePointManager.s\_ServicePointTable поля

`ServicePointManager.s_ServicePointTable`— <xref:System.Collections.Hashtable> , содержащая список активных подключений HTTP (<xref:System.Net.ServicePoint>s) в <xref:System.AppDomain>.

## <a name="syntax"></a>Синтаксис
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> `ServicePointManager.s_ServicePointTable` Поля является закрытым и не предназначены для непосредственного использования в коде.
> 
> Корпорация Майкрософт не поддерживает использование этого поля в реальном приложении ни при каких обстоятельствах.

## <a name="requirements"></a>Требования

**Пространство имен:**<xref:System.Net>

**Сборка:** системы (в System.dll)

**Версии платформы .NET framework:** доступно с версии 2.0.
