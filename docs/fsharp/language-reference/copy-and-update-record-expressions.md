---
title: "Копирование и обновление записей выражения (F #)"
description: "Дополнительные сведения о записи указанного поля «копирование и обновление записей выражение» копирует существующие записи, обновления, а также возвращает обновленной записи."
keywords: "visual f#, f#, функциональное программирование"
author: ChrSteinert
ms.author: phcart
ms.date: 06/04/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b5fc4ef0-64eb-4272-96a7-bb4dffbb634a
ms.openlocfilehash: 2eb51842b678780a1d6da96e237ebb92d1ea5cec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="copy-and-update-record-expressions"></a>Копирование и обновление выражений записей

Объект *копирование и обновление записей выражение* выражение, которое копирует существующую запись, затем обновляет указанные поля и возвращает обновленной записи.


## <a name="syntax"></a>Синтаксис

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a>Примечания
Записи являются неизменяемыми, по умолчанию, таким образом, что нет обновления для существующей записи невозможно. Для создания обновленной записи все поля записи бы быть определен повторно. Чтобы упростить процесс *копирование и обновление записей выражение* может использоваться. Это выражение принимает существующей записи, создает новый того же типа, используя указанные поля из выражения и отсутствует поле, указанное выражение.
Это полезно в том случае, если необходимо скопировать существующую запись и при необходимости измените значения полей.

Созданная запись занять для экземпляра.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Если нужно обновить только на поля этой записи, можно использовать *копирование и обновление записей выражение* следующим образом:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>См. также
[Записи](records.md)

[Справочник по языку F#](index.md)
