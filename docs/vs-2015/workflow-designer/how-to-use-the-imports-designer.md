---
title: Как использовать конструктор Imports | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 47b5055cca0b00e7fdec49947df13b473a090aaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659087"
---
# <a name="how-to-use-the-imports-designer"></a>Как использовать конструктор импорта
Конструктор импорта позволяет вводить пространства имен для типов, используемых в выражениях. Подобно **импорту** или **использованию** ключевых слов в Visual Basic .NET и C#, указание пространств имен в конструкторе Imports позволяет просто ввести имя типа в выражение, а не полное имя типа версии.

 Конструктор импорта реагирует на изменения в пользовательском интерфейсе и изменения, выполняемые при сохранении рабочего процесса. Во время сохранения рабочего процесса, пространства имен автоматически добавляются в конструктор импорта. В число этих требований входят следующие:

- Пространства имен для всех типов, используемых в декларациях переменных и аргументов.

- Пространства имен для всех типов, используемых в выражениях.

- Все остальные пространства имен, необходимые для сериализации рабочего процесса (например, пространства имен, используемые настраиваемыми действиями, перенесенными в рабочий процесс).

  При сохранении рабочего процесса можно заметить, что некоторые удаленные вручную пространства имен автоматически повторно добавляются в конструктор импорта, вследствие логики, описанной в предыдущем списке.

### <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>Добавление пространства имен в список импортированных пространств имен

1. Откройте сервисное приложение рабочего процесса WCF, консольное приложение рабочего процесса, проект библиотеки действий в [!INCLUDE[vs2010](../includes/vs2010-md.md)] или повторно размещенное приложение рабочего процесса.

2. Щелкните **Imports (импорт** ) в нижней части основного холста. Отобразится конструктор импорта.

3. Введите или выберите пространство имен из элемента управления «Раскрывающийся список» вверху конструктора импорта.

     При вводе отобразится список допустимых пространств имен, соответствующих введенным символам.

4. Нажмите клавишу **Ввод** , чтобы добавить пространство имен в список.

5. Если необходимо удалить пространство имен из списка, выберите пространство имен и нажмите клавишу **Delete** на клавиатуре. Обратите внимание, что пространство имен можно удалять только в случае, если пространство имен недействительно по какой-либо причине, например если проект больше не ссылается на сборку, содержащую пространство имен.