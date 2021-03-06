---
title: "Практическое руководство. Добавление несколько наборов параметров в приложение на C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec541a8f83990eec79226be7fb4880ef8dda639d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>Практическое руководство. Добавление несколько наборов параметров в приложение на C# #
В некоторых случаях может потребоваться иметь несколько наборов параметров в приложение. Например если вы разрабатываете приложения там, где ожидается определенная группа параметров для часто меняются, можно порекомендовать разделяйте их все в одном файле, чтобы его можно заменить, изменяя другие параметры. Visual Studio позволяет добавлять несколько наборов параметров в проект. Дополнительные наборы параметров может осуществляться с помощью объекта "Properties.Settings".  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a>Чтобы добавить дополнительный набор параметров в приложение  
  
1.  В меню **Проект** выберите команду **Добавить новый элемент**. Откроется диалоговое окно **Добавление нового элемента**.  
  
2.  В **Добавление нового элемента** выберите **файл параметров**, введите имя для файла и нажмите кнопку **добавить** для добавления в решение новый файл параметров.  
  
3.  В **обозревателе решений**, перетащите новый файл параметров в **свойства** папки. Благодаря этому новые параметры будут доступны в коде.  
  
4.  Добавить и использовать параметры в этом файле, как и любой другой файл параметров. Эта группа параметров с помощью объекта Properties.Settings доступны.  
  
## <a name="see-also"></a>См. также  
 [Использование параметров приложения и параметров пользователя](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Общие сведения о параметрах приложений](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
