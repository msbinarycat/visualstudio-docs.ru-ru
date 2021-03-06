---
title: Отображение связанных данных в приложениях WPF
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6ab1301e421f8326cf4cdda97556ecb19e394c29
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586683"
---
# <a name="display-related-data-in-wpf-applications"></a>Отображение связанных данных в приложениях WPF

В некоторых приложениях может потребоваться работа с данными, поступающими из нескольких таблиц или сущностей, которые связаны друг с другом в связи типа «родители-потомки». Например, может потребоваться отобразить сетку, отображающую клиентов из `Customers` таблицы. Когда пользователь выбирает конкретного клиента, в другой сетке отображаются заказы этого клиента из связанной таблицы `Orders`.

Можно создавать элементы управления с привязкой к данным, отображающие связанные данные, перетаскивая элементы из окна **Источники данных** в конструктор WPF.

## <a name="to-create-controls-that-display-related-records"></a>Создание элементов управления, отображающих связанные записи

1. Чтобы открыть окно **Источники данных**, щелкните пункт **Показать источники данных** в меню **Данные**.

2. Выберите команду **Добавить новый источник данных** и выполните **Мастер настройки источника данных**.

3. Откройте конструктор WPF и убедитесь, что конструктор содержит контейнер, который является допустимой целью перетаскивания для элементов в окне **Источники данных** .

     Дополнительные сведения о допустимых целевых объектах перетаскивания см. [в разделе Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

4. В окне **Источники данных** разверните узел, представляющий родительскую таблицу или объект в связи. Родительская таблица или объект находится на стороне "один" связи "один ко многим".

5. Перетащите родительский узел (или все отдельные элементы родительского узла) из окна **Источники данных** на допустимую цель перетаскивания в конструкторе.

     Visual Studio создает код XAML, который создает новые элементы управления с привязкой к данным для каждого перетаскиваемого элемента. XAML также добавляет новый <xref:System.Windows.Data.CollectionViewSource> для родительской таблицы или объекта в ресурсы целевого объекта перетаскивания. Для некоторых источников данных Visual Studio также создает код для загрузки данных в родительскую таблицу или объект. Дополнительные сведения см. [в разделе Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. В окне **Источники данных** выберите связанную дочернюю таблицу или объект. Связанные дочерние таблицы и объекты отображаются в виде развертываемых узлов в нижней части списка данных родительского узла.

7. Перетащите дочерний узел (или все отдельные элементы дочернего узла) из окна **Источники данных** на допустимую цель перетаскивания в конструкторе.

     Visual Studio создает код XAML, который создает новые элементы управления с привязкой к данным для каждого перетаскиваемого элемента. XAML также добавляет новый <xref:System.Windows.Data.CollectionViewSource> для дочерней таблицы или объекта в ресурсы целевого объекта перетаскивания. Этот новый <xref:System.Windows.Data.CollectionViewSource> привязан к свойству родительской таблицы или объекта, которые вы только что перетащили в конструктор. Для некоторых источников данных Visual Studio также создает код для загрузки данных в дочернюю таблицу или объект.

     На следующем рисунке показана таблица **Orders** таблицы **Customers** набора данных в окне **Источники данных** .

     ![Окно “Источники данных”, демонстрирующее отношение](../data-tools/media/datasources2.gif)

## <a name="see-also"></a>См. также:

- [Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Создание таблиц подстановки в приложениях WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)
