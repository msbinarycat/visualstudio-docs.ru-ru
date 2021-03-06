---
title: Редактирование таблиц стилей XSLT | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e1669affa89c91ca3ae1958c22ff3ec4d56bb8c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670954"
---
# <a name="editing-xslt-style-sheets"></a>Редактирование таблиц стилей XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Редактор XML может также использоваться для редактирования таблиц стилей XSLT. Можно воспользоваться преимуществами стандартных возможностей редактора, таких как технология IntelliSense, структурирование, XML-фрагменты и др. Кроме того, имеются новые возможности, облегчающие разработку на языке XSLT.

## <a name="xslt-features"></a>Возможности XSLT
 В следующей таблице описаны функции, доступные только при работе с таблицами стилей XSLT.

 **Выделение синтаксиса** Ключевые слова XSLT, такие как `template`, `match` и т. д., отображаются в цвете ключевого слова XSLT, заданном параметрами « **шрифты» и «цвета** ».

 **Волнистые** подчеркивания Редактор XML использует установленный файл XSLT. XSD для проверки таблиц стилей XSLT. Ошибки проверки подчеркнуты синей волнистой линией. Редактор XML также компилирует таблицу стилей в фоновом режиме и сообщает об ошибках и предупреждениях компилятора с помощью подчеркивания волнистыми линиями в соответствующих местах.

 **Поддержка блоков сценариев** Код в блоках сценариев поддерживается отладчиком XSLT, поэтому можно задавать точки останова и выполнять код блока сценария.

 **Просмотр выходных данных XSLT** Можно выполнить преобразование XSL и просмотреть выходные данные в редакторе XML. Дополнительные сведения см. в разделе [инструкции. выполнение преобразования XSLT из редактора XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

 **Отладка XSLT** Можно запустить отладчик XSLT из XSLT-файла в редакторе XML. Отладчик поддерживает установку точек останова в XSLT-файле, просмотр состояния выполнения XSLT и т. д. При проведении указателя над переменной XSLT появляется подсказка со значением переменной. Отладчик можно использовать для отладки таблицы стилей или отладки преобразования скомпилированного XSL-файла, вызванного из другого приложения. Дополнительные сведения см. в разделе [Отладка XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>См. также раздел
 [XML-редактор](../xml-tools/xml-editor.md)
