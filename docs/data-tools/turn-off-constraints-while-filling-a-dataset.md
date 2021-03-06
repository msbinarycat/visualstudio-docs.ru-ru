---
title: Отключение ограничений при заполнении набора данных
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 13cde04c3a10833c25fdc351d730b866f876e8da
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586137"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Отключение ограничений при заполнении набора данных

Если набор данных содержит ограничения (например, ограничения внешнего ключа), они могут вызывать ошибки, связанные с порядком операций, выполняемых с набором данных. Например, загрузка дочерних записей перед загрузкой связанных родительских записей может привести к нарушению ограничения и вызвать ошибку. После загрузки дочерней записи ограничение проверяет связанную родительскую запись и вызывает ошибку.

Если механизм, позволяющий временно приостановку ограничения, не существовал, при каждой попытке загрузить запись в дочернюю таблицу возникнет ошибка. Еще один способ приостановить все ограничения в наборе данных — с помощью <xref:System.Data.DataRow.BeginEdit%2A>и <xref:System.Data.DataRow.EndEdit%2A> свойств.

> [!NOTE]
> События проверки (например, <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.RowChanging>) не будут вызываться при отключенных ограничениях.

## <a name="to-suspend-update-constraints-programmatically"></a>Чтобы приостановить ограничения обновления программным способом

- В следующем примере показано, как временно отключить проверку ограничений в наборе данных.

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Приостановка ограничений обновления с помощью конструктор наборов данных

1. Откройте свой набор данных в **Конструкторе наборов данных**. Дополнительные сведения см. [в разделе Пошаговое руководство. Создание набора данных в конструктор наборов данных](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. В окне **Свойства** присвойте свойству <xref:System.Data.DataSet.EnforceConstraints%2A> значение `false`.

## <a name="see-also"></a>См. также:

- [Заполнение наборов данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Отношения в наборах данных](../data-tools/relationships-in-datasets.md)
