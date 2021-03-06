---
title: 'Ошибка: не удается задать точку останова в данных | Документация Майкрософт'
ms.date: 12/3/2019
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unable_to_set_data_breakpoint
dev_langs:
- CSharp
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, data breakpoint
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: wardengnaw
ms.author: waan
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 18fa63f2a6f4b6d789bad6f813cb3956a636a2d2
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404090"
---
# <a name="troubleshooting-data-breakpoint-errors"></a>Устранение ошибок точек останова в данных
На этой странице приведено пошаговое руководство по устранению распространенных ошибок, возникающих при использовании команды "прерывать при изменении значения".

## <a name="diagnosing-unable-to-set-data-breakpoint-errors"></a>Диагностика ошибок "не удается задать точку останова для данных"
> [!IMPORTANT]
> Точки останова управляемых данных поддерживаются в .NET Core 3,0 и выше. Последнюю версию можно скачать [здесь](https://dotnet.microsoft.com/download).

Ниже приведен список ошибок, которые могут возникнуть при использовании точек останова управляемых данных. Они содержат дополнительное объяснение того, почему происходит ошибка и возможные решения или обходные пути для устранения ошибки.

- *"Версия .NET, используемая целевым процессом, не поддерживает точки останова по данным. Для точек останова по данным требуется .NET Core 3.0 + на базе x86 или x64. "*

    - Поддержка точек останова управляемых данных, которые началися в .NET Core 3,0. В настоящее время он не поддерживается в .NET Framework или версии .NET Core в 3,0. 
    
    - **Решение**. решение заключается в обновлении проекта до .net Core 3,0.

- *"Значение не может быть найдено в управляемой куче и не может быть записано".*
    - Переменная, объявленная в стеке.
        - Мы не поддерживаем заданием точек останова для переменных, созданных в стеке, так как эта переменная будет недействительной после выхода из функции.
        - **Обходное решение**. Установите точки останова в строках, где используется переменная.

    - "Прерывать при изменении значения" для переменной, которая не разворачивается из раскрывающегося списка.
        - Отладчику необходимо внутренне узнать объект, содержащий поле, которое необходимо отслеживанию. Сборщик мусора может переместить объект в куче, поэтому отладчику потребуется знать объект, содержащий переменную, которую необходимо отвестиь. 
        - **Обходное решение**. Если вы используете метод в объекте, для которого нужно задать точку останова по данным, перейдите на один кадр вверх и используйте окно `locals/autos/watch`, чтобы развернуть объект и задать точку останова для данных в нужном поле.

- *"Точки останова для данных не поддерживаются для статических полей или статических свойств".*
    
    - Статические поля и свойства в данный момент не поддерживаются. Если вы заинтересованы в этой функции, оставьте [отзыв](#provide-feedback).

- *«Поля и свойства структур не могут быть отслеживаниями».*

    - Поля и свойства структур не поддерживаются в данный момент. Если вы заинтересованы в этой функции, оставьте [отзыв](#provide-feedback).

- *"Значение свойства изменилось и больше не может быть отслеживанием".*

    - Свойство может изменить то, как оно вычислено во время выполнения, и если это происходит, то число переменных, от которых зависит свойство, увеличивается и может превышать аппаратное ограничение. См. раздел `"The property is dependent on more memory than can be tracked by the hardware."` ниже.

- *"Свойство зависит от большего объема памяти, чем может быть записано оборудованием".*
    
    - Каждая архитектура имеет заданное количество байтов и точек останова по данным оборудования, которое может поддерживаться, а свойство, для которого требуется задать точку останова, превысило это ограничение. Сведения о том, сколько аппаратно поддерживаемых точек останова данных и байт доступны для используемой архитектуры, см. в таблице [ограничения оборудования для точек останова данных](#data-breakpoint-hardware-limitations) . 
    - **Обходное решение**. Задайте точку останова по значению, которое может измениться в свойстве.

- *"Точки останова в данных не поддерживаются при использовании C# устаревшего средства оценки выражений".*

    - Точки останова в данных поддерживаются только в нестандартном C# вычислителе выражений. 
    - **Решение**. вы отключите средство оценки C# устаревших выражений, перейдя в `Debug -> Options` затем в разделе `Debugging -> General` снять флажок `"Use the legacy C# and VB expression evaluators"`.

## <a name="data-breakpoint-hardware-limitations"></a>Ограничения на оборудование для точки останова в данных

Архитектура (Конфигурация платформы), в которой выполняется программа, имеет ограниченное количество точек останова аппаратных данных, которые он может использовать. В таблице ниже показано, сколько регистров можно использовать для каждой архитектуры.

| Архитектура | Число точек останова в данных, поддерживаемых оборудованием | Максимальный размер в байтах|
| :-------------: |:-------------:| :-------------:|
| x86 | 4 | 4 |
| x64 | 4 | 8 |
| ARM | 1 | 4 |
| ARM64 | 2 | 8 |

## <a name="provide-feedback"></a>Предоставление отзыва
При возникновении каких-либо проблем или предложений по этой функции сообщите нам об этом с помощью справки > Отправить отзыв > [сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio.md) в интегрированной среде разработки или в [сообществе разработчиков](https://developercommunity.visualstudio.com/).

## <a name="see-also"></a>См. также:
- [Использование команды "прерывать при изменении значения" в .NET Core 3,0](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).
- [Девблог: break при изменении значения: точки останова по данным для .NET Core в Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/break-when-value-changes-data-breakpoints-for-net-core-in-visual-studio-2019/)
