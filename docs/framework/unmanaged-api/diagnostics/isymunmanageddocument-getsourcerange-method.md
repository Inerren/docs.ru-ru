---
title: "Метод ISymUnmanagedDocument::GetSourceRange"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetSourceRange
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6c47f1f491b184e9abe9d56d0729100b0d9b36a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a>Метод ISymUnmanagedDocument::GetSourceRange
Возвращает заданный диапазон внедренного источника в заданный буфер. Размер буфера должен быть достаточно велик для хранения источника.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
#### <a name="parameters"></a>Параметры  
 `startLine`  
 [in] Начальная строка текущего документа.  
  
 `startColumn`  
 [in] Начальный столбец текущего документа.  
  
 `endLine`  
 [in] Последняя строка в текущем документе.  
  
 `endColumn`  
 [in] Последний столбец в текущем документе.  
  
 `cSourceBytes`  
 [in] Размер источника в байтах.  
  
 `pcSourceBytes`  
 [out] Указатель на переменную, которая получает размер источника.  
  
 `source`  
 [out] Размер и длина указанного диапазона исходного документа, в байтах.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение S_OK, если метод выполнен успешно.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс ISymUnmanagedDocument](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
