---
title: Закомментирование кода
description: В этой статье описывается использование комментариев в редакторе исходного кода Visual Studio для Mac
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 2966d8b89a2609d3fbfc2b6b4561288433641ca1
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693109"
---
# <a name="comments"></a>Комментарии

При отладке кода или экспериментировании с ним может оказаться полезным комментировать блоки кода как временно, так и в долгосрочной перспективе.

Чтобы оставить комментарий к целому блоку кода, сделайте следующее:

* Выделите код и выберите пункт **Закомментировать или раскомментировать строку** в контекстном меню

OR

* Используйте сочетание клавиш `cmd + /` для выделенного кода.

Эти методы позволяют закомментировать или раскомментировать разделы кода. В файлах C# можно добавить дополнительные уровни комментариев для строк, что позволяет закомментировать или раскомментировать области кода, сохранив фактические комментарии:

![Многоуровневые комментарии](media/source-editor-image8.png)

Комментарии также удобно использовать при документировании кода для разработчиков, которые могут столкнуться с ним в будущем. Обычно они выполняются в виде многострочных комментариев, которые в каждом языке добавляются следующим образом:

**C#**

```csharp
/*
 This is a multi-line
 comment in C#
*/
```

**F#**

```fsharp
(*
 This is a multi-line
  comment in F#
*)
```

## <a name="see-also"></a>См. также

- [Закомментирование кода (Visual Studio в Windows)](/visualstudio/ide/quickstart-editor#comment-out-code)