---
title: Практическое руководство. Использование окна дизассемблирования | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.disassembly
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c25c3cdeb96abacb4123b2d0a851ac3d4acb0cd5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696145"
---
# <a name="how-to-use-the-disassembly-window"></a>Практическое руководство. Использование окна дизассемблирования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта функция доступна только в том случае, если включена отладка на уровне адреса **параметры** диалоговом окне **Отладка** узла. Она недоступна для отладки скриптов и SQL.  
  
 В окне **Дизассемблированный код** отображается код сборки, соответствующий инструкциям, созданным компилятором. При отладке управляемого кода эти инструкции ассемблера соответствуют присущему данному объекту коду, созданному компилятором JIT, а не промежуточному языку (MSIL), созданному компилятором Visual Studio.  
  
 В дополнение к инструкциям ассемблера в окне **Дизассемблированный код** могут отображаться следующие сведения:  
  
- Адреса в памяти, где располагается каждая из инструкций. Для приложений это фактические адреса в памяти. Для кода, написанного на Visual Basic, C#, и для управляемого кода это смещение относительно начала функции.  
  
- Исходный код, из которого получается код сборки.  
  
- Байты кода - байтовое представление реальных инструкций компьютера или языка MSIL.  
  
- Символьные имена для адресов памяти.  
  
- Номера строк, соответствующие исходному коду.  
  
  Инструкции на языке ассемблера состоят из мнемоник, представляющих собой сокращения имен инструкций и символы, обозначающие переменные, регистры и константы. Каждая инструкция машинного кода представляется одной мнемоникой ассемблера, за которой, как правило, следует одна или несколько переменных, регистров или констант.  
  
  Чтобы в полном объеме использовать преимущества работы с окном Дизассемблированный код, изучите хорошую книгу по программированию на языке ассемблера. Подробное обсуждение вопросов, связанных с программированием на языке Ассемблер, не входит в задачи данного раздела.  
  
  Поскольку код ассемблера в большой степени основывается на использовании регистров процессора или, в случае управляемого кода, регистров общеязыковой среды выполнения, часто вместе с окном Дизассемблированный код следует использовать окно Регистры, позволяющее проверять содержимое регистров.  
  
  Возможно, у вас не возникнет желания или необходимости просматривать инструкции машинного кода, представленные в числовой форме, вместо кода ассемблера. Однако при желании можно для этой цели использовать окно Память или выбрать Байты кода из контекстного меню окна Дизассемблированный код"  
  
> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-disassembly-window"></a>Чтобы отобразить окно Дизассемблированный код  
  
- На **Отладка** меню, выберите **Windows**и нажмите кнопку **Дизассемблированный код**.  
  
     Отладчик должен быть запущен либо находиться в режиме приостановки выполнения.  
  
### <a name="to-turn-optional-information-on-or-off"></a>Чтобы включить или отключить дополнительные сведения  
  
- Щелкните правой кнопкой мыши **Дизассемблированный код** окна и установите или снимите в контекстном меню соответствующие флажки.  
  
     Желтая стрелка, расположенная в левом поле, отмечает размещение текущей точки выполнения. Для присущего данному объекту кода это соответствует счетчику команд ЦП. В этом расположении отображается следующая инструкция, которая будет выполнена в программе.  
  
     Дополнительные сведения см. в разделе [разбиение по страницам вверх или вниз по содержимому памяти](../debugger/how-to-page-up-or-down-in-memory.md).  
  
## <a name="see-also"></a>См. также  
 [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)   
 [Практическое руководство. Использование окна регистров](../debugger/how-to-use-the-registers-window.md)
