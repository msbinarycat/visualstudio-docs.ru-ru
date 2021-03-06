---
title: Создание директив using
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: f3b3435e10d6bb9a71fd16b9286759b136c167f4
ms.sourcegitcommit: ea5e02720d71185f8e27fbea205024371b0c7ceb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2020
ms.locfileid: "77544542"
---
# <a name="add-missing-usings-in-visual-studio"></a>Добавление пропущенных директив using в Visual Studio

Область применения этого формирования кода:

- C#

**Что?** Позволяет немедленно добавить необходимые импортированные элементы или [директива using](/dotnet/csharp/language-reference/keywords/using-directive) для скопированного и вставленного кода.

**Когда?** Часто приходится копировать существующий код из разных частей проекта или других источников и вставлять его в новый код. Это быстрое действие находит отсутствующие импортируемые элементы и директивы для скопированного и вставленного кода и запрашивает их добавление. Это исправление кода также может добавлять ссылки из проекта в проект.

**Зачем?** Так как это быстрое действие автоматически добавляет необходимые импортируемые элементы, вам не нужно вручную копировать директивы `using`, которые должны присутствовать в коде.

## <a name="add-missing-usings-refactoring"></a>Добавление пропущенного рефакторинга операторов using

1. Скопируйте код в одном файле и вставьте его в другой, не включая необходимые директивы `using`. Итоговая ошибка сопровождается исправлением кода, которое добавляет отсутствующие директивы `using`.

    > [!NOTE]
    > Это предложения нужно включить в разделе **Сервис > Параметры > Текстовый редактор > C# > Дополнительно > Директивы using**.

2. Нажмите клавиши CTRL+. чтобы открыть меню **Быстрые действия и рефакторинг**.

    ![Создание директив using](media/generate-using-codefix.png)

3. Выберите **using \<ваша ссылка\>;** , чтобы добавить отсутствующую ссылку.

    ![Результат создания директив using](media/generate-using-result.png)

## <a name="see-also"></a>См. также

- [Создание кода](../code-generation-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)
- [Советы для разработчиков .NET](../csharp-developer-productivity.md)
