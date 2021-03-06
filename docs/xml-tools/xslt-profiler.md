---
title: Производительность XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79d865a426af2c089bfcc6bd1e733b4ecc185077
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592286"
---
# <a name="the-xslt-profiler"></a>Профилировщик XSLT

Профилировщик XSLT создает подробные отчеты о производительности XSLT, помогающие измерять, оценивать и выявлять проблемы в XSLT коде, связанные с производительностью. Профилировщик XSLT содержит полезные подсказки по оптимизации таблиц стилей XSL и XSLT. Для приложений XSLT, требующих максимальной производительности, данное средство может стать незаменимым.

Профилировщик XSLT входит в состав Visual Studio и доступен в меню **XML** .

![Профилировщик XSLT](../xml-tools/media/profile-xslt-menu.png)

> [!NOTE]
> Профилировщик XSLT доступен только в выпуске Visual Studio Enterprise Edition.

## <a name="create-a-performance-report"></a>Создание отчета о производительности

1. Откройте XSLT-документ в редакторе Visual Studio.

2. В строке меню выберите **XML-**  > **Профиль XSLT**.

3. Предоставьте входной XML документ. Если XML-документ до сих пор не был открыт, появится приглашение открыть файл.

   Начнется анализ и индикатор выполнения в редакторе будет отображать прогресс. Выходные данные XSLT также видимы.

4. После завершения сеанса анализа производительности просмотрите отчет о производительности, чтобы проанализировать производительность XSLT.

## <a name="get-all-available-views"></a>Получить все доступные представления

1. Щелкните раскрывающийся список **Текущее представление** , чтобы получить все доступные представления.

2. Выберите параметр **представление сводки** в раскрывающемся списке **Текущее представление** . По умолчанию отчет о производительности отображается в представлении " **Сводка**". Это представление является отправной точкой для определения проблем производительности XSLT-документов. В **представлении "Сводка** " перечислены следующие точки данных.

   - Наиболее часто вызываемые функции

   - Функции с максимальным объемом индивидуальной работы

   - Функции с наибольшим временем выполнения

   По умолчанию каждая точка данных имеет три столбца: имя функции, количество вызовов в абсолютном значении и процентное отношение вызовов названной функции к общему числу вызовов функции. С каждой точки данных в **представлении "Сводка**" можно перейти к более подробным представлениям, щелкнув точки данных функции правой кнопкой мыши.

3. Выберите параметр **представление функции** в раскрывающемся списке **Текущее представление** . В **представлении "функция** " перечислены функции, вызываемые во время профилирования. Щелкнув имя столбца, можно сортировать данные. По умолчанию отображаются следующие столбцы:

    - **Имя функции**

    - **Затраченное инклюзивное время**

    - **% затраченного эксклюзивного времени**

    - **Инклюзивное время приложения**

    - **Эксклюзивное время приложения**

    - **Число вызовов**

   Все столбцы времени отображаются в абсолютном и процентном значениях. Термин **эксклюзивный** относится к общему времени, затраченному на выполнение функцией эксклюзивного времени, потраченного другими функциями, вызванными во время выполнения этой функции.

   Термин **инклюзивный** относится к общему времени, затраченному на выполнение функции, включая время выполнения всех вызываемых функций, а также от того, вызывают ли какие-либо из этих функций другие функции.

## <a name="select-callercallee-view"></a>Выберите представление «Вызывающий/вызываемый»

Выберите представление " **вызывающий/вызываемый** " в раскрывающемся списке **Текущее представление** . Представление " **вызывающий/вызываемый** " имеет следующие три различных части:

- **Функции, которые вызвали**: все функции, которые вызывали определенную функцию, перечислены в верхней части представления.

- **Текущая функция**: конкретная вызываемая функция указана в средней части представления.

- **Функции, которые были вызваны**: все функции, которые были вызваны конкретной функцией, перечислены в нижней части представления.

Если функция по имени `SyncToNavigator` появится в средней части представления, то все функции, вызывавшие функцию `SyncToNavigator`, будут отображены в верхней части представления, а все функции, которые вызывались функцией `SyncToNavigator`, будут отображены в нижней части представления.

- Можно изменить функцию в средней части представления, дважды щелкнув любую из функций, перечисленных в двух других частях представления. Представление обновится автоматически, чтобы отобразить произведенные изменения.

- Можно также сортировать данные, щелкая имена столбцов.

## <a name="select-call-tree-view"></a>Выбор представления "дерево вызовов"

- Выберите **представление "дерево вызовов** " в раскрывающемся списке **Текущее представление** . Данное представление является древовидным представлением выполнения программы.

   В **представлении "дерево вызовов** " в качестве имени процесса отображается корень дерева. Функции являются узлами дерева. Данное представление позволяет углубляться в конкретные трассировки вызовов и анализировать, какие из трассировок оказывают большее влияние на производительность. Представление аналогично **представлению стека вызовов** , доступному во время отладки. Помимо столбцов в **представлении "функция**" в **представлении "дерево вызовов**" имеется дополнительный столбец для отображения **имени модуля**.

- Выберите **метки** в раскрывающемся списке **Текущее представление** .

   Профилировщик XSLT содержит метки, которые отображаются в потоке сбора данных со связанным комментарием. Метки представляют собой места в коде, имеющие счетчики. Когда профилировщику XSLT поставлена задача сбора счетчиков производительности XSLT, счетчики собираются каждый раз, когда одна из этих меток выполняется. Данные отображаются в таблице, содержащей **идентификатор метки**, **имя метки** (**Начальная программа**, **Конечная программа**) и **отметку времени**. Метки не суммируются и отображаются в хронологическом порядке в **представлении "метки** " отчета о производительности.

## <a name="select-modules-in-the-current-view"></a>Выбор модуля в текущем представлении.

- Выберите **модули** в раскрывающемся списке **Текущее представление** .

   Представление модулей - это плоский список всех функций, агрегированных на уровне модуля. Чтобы отобразить или свернуть данные о производительности модуля, следует отобразить или закрыть имя модуля. Щелкнув имя столбца, можно сортировать данные. По умолчанию существуют абсолютные и процентные показатели **затраченного инклюзивного времени**, **затраченное эксклюзивное**время, **инклюзивное**время приложения, **эксклюзивное время приложения**и **число вызовов**.

- Выберите **процесс** в раскрывающемся списке **Текущее представление** .

   В представлении "процесс" отображается таблица, содержащая **идентификатор процесса**, **имя процесса**, **время начала**и **время окончания**. Данные можно сортировать, щелкая имена столбцов.

## <a name="see-also"></a>См. также:

- [Пошаговое руководство. Использование иерархии XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)
