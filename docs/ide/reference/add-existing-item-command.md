---
title: Команда Add Existing Item
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d49f0fde7bbf13a1219296420b84970f4350860
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585708"
---
# <a name="add-existing-item-command"></a>Команда Add Existing Item
Добавляет существующий файл в текущее решение и открывает его.

## <a name="syntax"></a>Синтаксис

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Аргументы
`filename`\
Обязательный. Полный путь и имя файла с расширением для элемента, который нужно добавить в текущее решение. Если имя или путь файла содержат пробелы, нужно заключить весь путь в кавычки.

## <a name="switches"></a>Переключатели
/e: `editorname`\
Необязательный элемент. Имя редактора, в котором будет открыт файл. Если аргумент указан, но имя редактора не предоставляется, отображается диалоговое окно **Открыть с помощью**.

В синтаксической структуре аргумента /e:`editorname` имена редакторов используются в том виде, в каком они отображаются в диалоговом окне **Открыть с помощью**, с заключением в кавычки. Например, чтобы открыть таблицу стилей в редакторе исходного кода, необходимо ввести для аргумента /e:`editorname` следующую строку:

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Примечания
Когда вы вводите данные, функция автозавершения пытается определить правильный путь и правильное имя файла.

## <a name="example"></a>Пример
Этот пример добавляет файл Form1.frm в текущее решение.

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
