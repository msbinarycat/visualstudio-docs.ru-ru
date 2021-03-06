---
title: Пошаговое руководство. Привязка данных к элементам управления в области действий Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1543f872961d556674dd5ad6b3f5b8071d2d404b
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253883"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Пошаговое руководство. Привязка данных к элементам управления в области действий Excel
  В этом пошаговом руководстве демонстрируется привязка данных к элементам управления на панели действий в Microsoft Office Excel. Элементы управления показывают отношение «Основной/подробности» между таблицами в базе данных SQL Server.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 В данном пошаговом руководстве рассмотрены следующие задачи:

- Добавление элементов управления на лист.

- Создание элемента управления панели действий.

- Добавление привязанных к данным Windows Forms элементов управления в элемент управления панели действий.

- Отображение области действий при открытии приложения.

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Доступ к серверу с помощью образца базы данных Northwind SQL Server.

- Разрешения на чтение и запись в базу данных SQL Server.

## <a name="create-the-project"></a>Создание проекта
 Первым шагом является создание проекта книги Excel.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Создайте проект книги Excel с именем **панель Мои действия Excel**. В мастере выберите **создать новый документ**. Дополнительные сведения см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio откроет новую книгу Excel в конструкторе и добавит проект **панели "мои действия" Excel** в **Обозреватель решений**.

## <a name="add-a-new-data-source-to-the-project"></a>Добавление нового источника данных в проект

### <a name="to-add-a-new-data-source-to-the-project"></a>Добавление нового источника данных в проект

1. Если окно **Источники данных** не отображается, отобразите его с помощью команды **Просмотреть** > **другие** > **Источники данных**Windows в строке меню.

2. Выберите команду **Добавить новый источник данных** , чтобы запустить **Мастер настройки источника данных**.

3. Выберите **база данных** и нажмите кнопку **Далее**.

4. Выберите подключение данных к образцу базы данных Northwind SQL Server или добавьте новое соединение с помощью кнопки **создать подключение** .

5. Нажмите кнопку **Далее**.

6. Снимите флажок сохранить подключение, если оно выбрано, и нажмите кнопку **Далее**.

7. Разверните узел **таблицы** в окне **объекты базы данных** .

8. Установите флажок рядом с таблицей **поставщики** .

9. Разверните таблицу **продукты** и выберите **ProductName**, **КодПоставщика**, **QuantityPerUnit**и **UnitPrice**.

10. Нажмите кнопку **Готово**.

    Мастер добавит таблицу **поставщики** и таблицу **Products** в окно **Источники данных** . Он также добавляет в проект типизированный набор данных, видимый в **Обозреватель решений**.

## <a name="add-controls-to-the-worksheet"></a>Добавление элементов управления на лист
 Затем добавьте <xref:Microsoft.Office.Tools.Excel.NamedRange> элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> и элемент управления на первый лист.

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Добавление элемента управления NamedRange и элемента управления ListObject

1. Убедитесь, что книга " **Моя панель действий Excel** " открыта в конструкторе Visual Studio и `Sheet1` отображается.

2. В окне **Источники данных** разверните таблицу **поставщики** .

3. Щелкните стрелку раскрывающегося списка в узле **название компании** и выберите пункт **NamedRange**.

4. Перетащите **имя компании** из окна **Источники данных** в ячейку **a2** в `Sheet1`.

     Элемент управления с `CompanyNameNamedRange` именем создается, а текст \<CompanyName > отображается в ячейке **a2.** <xref:Microsoft.Office.Tools.Excel.NamedRange> В то же время <xref:System.Windows.Forms.BindingSource> в проект добавляются именованный `suppliersBindingSource`, адаптер таблицы и <xref:System.Data.DataSet> объект. Элемент управления привязан к <xref:System.Windows.Forms.BindingSource>, который, в свою очередь, привязан <xref:System.Data.DataSet> к экземпляру.

5. В окне **Источники данных** прокрутите вниз столбцы, находящиеся в таблице **поставщики** . В нижней части списка находится таблица **Products** ; Это связано с тем, что это дочерний элемент таблицы « **поставщики** ». Выберите таблицу **продукты** , а не ту, которая находится на том же уровне, что и таблица « **поставщики** », а затем щелкните появившуюся стрелку раскрывающегося списка.

6. В раскрывающемся списке выберите элемент **ListObject** , а затем перетащите таблицу **Products** в ячейку **A6** в `Sheet1`.

     Элемент управления с `ProductNameListObject` именем создается в ячейке **A6.** <xref:Microsoft.Office.Tools.Excel.ListObject> В то же время <xref:System.Windows.Forms.BindingSource> в проект добавляются имя `productsBindingSource` и адаптер таблицы. Элемент управления привязан к <xref:System.Windows.Forms.BindingSource>, который, в свою очередь, привязан <xref:System.Data.DataSet> к экземпляру.

7. Только C# для этого выберите **супплиерсбиндингсаурце** в области компонентов и измените значение свойства **модификаторы** на **internal** в окне **Свойства** .

## <a name="add-controls-to-the-actions-pane"></a>Добавление элементов управления на панель «действия»
 Далее вам понадобится элемент управления панели действий, имеющий поле со списком.

### <a name="to-add-an-actions-pane-control"></a>Добавление элемента управления панели действий

1. Выберите проект **области мои действия Excel** в **Обозреватель решений**.

2. В меню **Проект** выберите пункт **Добавить новый элемент**.

3. В диалоговом окне **Добавление нового элемента** выберите **элемент Панель действий**, назовите его **актионсконтрол**и нажмите кнопку **Добавить**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Добавление привязанных к данным Windows Forms элементов управления в элемент управления панели действий

1. На вкладках **Общие элементы управления** **панели элементов**перетащите <xref:System.Windows.Forms.ComboBox> элемент управления на панель действий.

2. Измените значение свойства **size** на **171, 21**.

3. Измените размер пользовательского элемента управления в соответствии с полем со списком.

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Привязка элемента управления на панели «действия» к данным
 В этом разделе вы настроите источник <xref:System.Windows.Forms.ComboBox> данных в том же источнике данных, <xref:Microsoft.Office.Tools.Excel.NamedRange> что и элемент управления на листе.

### <a name="to-set-data-binding-properties-of-the-control"></a>Задание свойств привязки данных элемента управления

1. Щелкните правой кнопкой мыши элемент управления панель действий и выберите команду **Просмотреть код**.

2. Добавьте следующий код в <xref:System.Windows.Forms.UserControl.Load> событие элемента управления панели действий.

     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]

3. В C#необходимо создать обработчик событий для `ActionsControl`. Этот код можно поместить в `ActionsControl` конструктор. Дополнительные сведения о создании обработчиков событий см. [в разделе как Создание обработчиков событий в проектах](../vsto/how-to-create-event-handlers-in-office-projects.md)Office.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]

## <a name="show-the-actions-pane"></a>Отображение панели "действия"
 Панель действий не отображается, пока элемент управления не будет добавлен во время выполнения.

#### <a name="to-show-the-actions-pane"></a>Отображение панели «действия»

1. В **Обозреватель решений**щелкните правой кнопкой мыши *ThisWorkbook. vb* или *ThisWorkbook.CS*и выберите пункт **Просмотреть код**.

2. Создайте новый экземпляр пользовательского элемента управления в `ThisWorkbook` классе.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]

3. В обработчике `ThisWorkbook`событий объекта добавьте элемент управления на панель действия. <xref:Microsoft.Office.Tools.Excel.Workbook.Startup>

     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]

## <a name="test-the-application"></a>Тестирование приложения
 Теперь можно протестировать документ, чтобы убедиться, что панель действий открывается при открытии документа и что элементы управления имеют связь «основной/подробности».

### <a name="to-test-your-document"></a>Проверка документа

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. Убедитесь, что панель действия видна.

3. Выберите компанию в списке. Убедитесь, что название компании указано в <xref:Microsoft.Office.Tools.Excel.NamedRange> элементе управления и что сведения о продукте перечислены <xref:Microsoft.Office.Tools.Excel.ListObject> в элементе управления.

4. Выберите различные компании, чтобы убедиться, что название компании и сведения о продукте изменяются соответствующим образом.

## <a name="next-steps"></a>Следующие шаги
 Ниже приводятся некоторые из возможных последующих задач.

- Привязка данных к элементам управления в Word. Дополнительные сведения см. в разделе [Пошаговое руководство: Привязка данных к элементам управления на панели](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)действий Word.

- Развертывание проекта. Дополнительные сведения см. в статье [развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>См. также
- [Обзор панели действий](../vsto/actions-pane-overview.md)
- [Практическое руководство. Управление макетом элемента управления на панелях действий](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
