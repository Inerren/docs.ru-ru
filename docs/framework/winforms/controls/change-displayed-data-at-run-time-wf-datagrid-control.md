---
title: "Практическое руководство. Изменение данных, отображаемых во время выполнения, в элементе управления DataGrid в Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45772035a7f2229ca0e0320ee9b65eb128c4fc32
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Практическое руководство. Изменение данных, отображаемых во время выполнения, в элементе управления DataGrid в Windows Forms
> [!NOTE]
>  Элемент управления <xref:System.Windows.Forms.DataGridView> заменяет элемент управления <xref:System.Windows.Forms.DataGrid> и расширяет его функциональные возможности; однако при необходимости элемент управления <xref:System.Windows.Forms.DataGrid> можно сохранить для обратной совместимости и использования в будущем. Дополнительные сведения см. в разделе [Различия элементов управления DataGridView и DataGrid в Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 После создания формы Windows <xref:System.Windows.Forms.DataGrid> с помощью функции времени разработки, вы также можете динамического изменения элементов управления <xref:System.Data.DataSet> объекта сетки во время выполнения. Это может быть изменение как отдельных значений таблицы или источник данных, привязанного к <xref:System.Windows.Forms.DataGrid> элемента управления. Изменение отдельных значений выполняется с помощью <xref:System.Data.DataSet> объекта, не <xref:System.Windows.Forms.DataGrid> элемента управления.  
  
### <a name="to-change-data-programmatically"></a>Изменение данных программными средствами  
  
1.  Выберите требуемую таблицу из <xref:System.Data.DataSet> объекта и нужную строку и поле в таблице и укажите в ячейке новое значение.  
  
    > [!NOTE]
    >  Чтобы указать в первой таблице <xref:System.Data.DataSet> или первой строки таблицы, укажите 0.  
  
     В следующем примере показано, как изменить вторую запись первой строки первой таблицы набора данных, щелкнув `Button1`. <xref:System.Data.DataSet> (`ds`) И таблиц (`0` и `1`) были созданы ранее.  
  
    ```vb  
    Protected Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       ds.tables(0).rows(0)(1) = "NewEntry"  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       ds.Tables[0].Rows[0][1]="NewEntry";  
    }  
    ```  
  
    ```cpp  
    private:   
       void button1_Click(System::Object^ sender, System::EventArgs^ e)  
       {  
          dataSet1->Tables[0]->Rows[0][1] = "NewEntry";  
       }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Поместите следующий код в конструктор формы для регистрации обработчика событий.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     При своем выполнении можно использовать <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> метод привязки <xref:System.Windows.Forms.DataGrid> управления для источника данных. Например, могут иметь несколько [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] элементами управления данными, каждый подключен к другой базе данных.  
  
### <a name="to-change-the-datasource-programmatically"></a>Чтобы изменить источник данных программными средствами  
  
1.  Задать <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> метод имя источника данных и вы хотите привязать к таблице.  
  
     Приведенный ниже показано, как изменить исходную дату с помощью <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> метод [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] управления данными (adoPubsAuthors), который подключен к таблице Authors базы данных Pubs.  
  
    ```vb  
    Private Sub ResetSource()  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors")  
    End Sub  
    ```  
  
    ```csharp  
    private void ResetSource()  
    {  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors");  
    }  
    ```  
  
    ```cpp  
    private:  
       void ResetSource()  
       {  
          dataGrid1->SetDataBinding(adoPubsAuthors, "Authors");  
       }  
    ```  
  
## <a name="see-also"></a>См. также  
 [Наборы данных ADO.NET](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 [Практическое руководство. Удаление или скрытие столбцов элемента управления DataGridView в Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [Практическое руководство. Добавление таблиц и столбцов в элемент управления DataGrid в Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [Практическое руководство. Привязка элемента управления DataGrid в Windows Forms к источнику данных](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
