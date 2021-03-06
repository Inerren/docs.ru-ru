---
title: "Практическое руководство. Приостановка выполнения службы Windows (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
f1_keywords: ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
caps.latest.revision: "17"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: d44358d3f76f50a06ede5e7d720f4f48d80893de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a>Практическое руководство. Приостановка выполнения службы Windows (Visual Basic)
В этом примере используется <xref:System.ServiceProcess.ServiceController> компонента, чтобы приостановить службу IIS Admin на локальном компьютере.  
  
## <a name="example"></a>Пример  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 Этот пример кода также доступен в качестве фрагмента кода IntelliSense. В средстве выбора фрагмента кода он находится в **операционная система Windows > службы Windows**. Дополнительные сведения см. в статье [Фрагменты кода](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
-   Ссылка проекта System.serviceprocess.dll.  
  
-   Доступ к членам пространства имен <xref:System.ServiceProcess>. Добавьте оператор `Imports`, если в коде не используются полные имена членов. Дополнительные сведения см. в статье [Оператор Imports (пространство имен .NET и тип)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A> Свойство <xref:System.ServiceProcess.ServiceController> класса — локальный компьютер по умолчанию. Чтобы обратиться к службам Windows на другом компьютере, измените <xref:System.ServiceProcess.ServiceController.MachineName%2A> на имя этого компьютера.  
  
 При следующих условиях возможно возникновение исключения:  
  
-   Служба не может быть приостановлена. (<xref:System.InvalidOperationException>)  
  
-   Произошла ошибка при обращении к API-интерфейсу системы. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 Управление службами на компьютере может быть ограничен с помощью <xref:System.ServiceProcess.ServiceControllerPermissionAccess> для задания разрешений в <xref:System.ServiceProcess.ServiceControllerPermission>.  
  
 Доступ к сведениям служб может быть ограничен с помощью <xref:System.Security.Permissions.PermissionState> для задания разрешений в <xref:System.Security.Permissions.SecurityPermission>.  
  
## <a name="see-also"></a>См. также  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>  
 [Как: возобновление выполнения службы Windows (Visual Basic)](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
