---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9dab9115c31e538bd28583b9f0591ae0c9611e2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Указывает, что свойство можно осуществлять запись, но не читать.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="rules"></a>Правила  
 **Контекст объявления.** `WriteOnly` можно использовать только на уровне модуля. Это означает, что контекст объявления для `WriteOnly` свойства должен быть классом, структурой или модуля и не может быть исходным файлом, пространством имен или процедуры.  
  
 Можно объявить свойство как `WriteOnly`, но не переменной.  
  
## <a name="when-to-use-writeonly"></a>Когда следует использовать WriteOnly  
 Иногда требуется, чтобы иметь возможность установить значение, но не открывал его код-потребитель. Например конфиденциальные данные, такие как социальных регистрационный номер или пароль, должен быть защищены от доступа из любого компонента, который не был указан. В этих случаях можно использовать `WriteOnly` свойство для задания значения.  
  
> [!IMPORTANT]
>  При определении и использовать `WriteOnly` свойства, рассмотрим следующие дополнительные защитные меры:  
  
-   **Переопределение.** Если свойство является членом класса, разрешить его значение по умолчанию [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), а не объявлять `Overridable` или `MustOverride`. Это предотвращает нежелательный доступ с помощью переопределения в производном классе.  
  
-   **Уровень доступа.** Если навести свойства конфиденциальные данные в одну или несколько переменных, объявите их [закрытый](../../../visual-basic/language-reference/modifiers/private.md) , чтобы к ним можно обращаться никакой другой код.  
  
-   **Шифрование.** Хранить все конфиденциальные данные в зашифрованном виде, а не в виде обычного текста. Если вредоносный код каким-то получает доступ к этой области памяти, это сложнее использовать данные. Шифрование также полезен, если это необходимо для сериализации конфиденциальных данных.  
  
-   **Сброс.** Когда класс, структура или модуль, определяющие свойство завершается, сброс конфиденциальные данные, другие значения имеют смысла или значения по умолчанию. Это обеспечивает дополнительную защиту компьютера при освобождении этой области памяти для общего доступа.  
  
-   **Сохраняемость.** Не сохраняются никакие конфиденциальные данные на диск, если этого можно избежать. Кроме того не записывать конфиденциальные данные в буфер обмена.  
  
 `WriteOnly` Модификатор может использоваться в этом контексте:  
  
 [Оператор Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>См. также  
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [Закрытые](../../../visual-basic/language-reference/modifiers/private.md)  
 [Ключевые слова](../../../visual-basic/language-reference/keywords/index.md)
