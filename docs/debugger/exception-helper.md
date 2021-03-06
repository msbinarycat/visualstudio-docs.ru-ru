---
title: Проверка исключения — Visual Studio | Документация Майкрософт
ms.date: 1/18/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- exception helper, debugger, exception
- debugging [Visual Studio], exception helper, Examine an exception
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2dae1609486ec4f3462be89b0526467dd7414647
ms.sourcegitcommit: 8cbced0fb46959a3a2494852df1e41db1177a26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/29/2020
ms.locfileid: "76829759"
---
# <a name="inspect-an-exception-using-the-exception-helper"></a>Проверка исключения с помощью вспомогательного приложения исключения 

Работа с исключениями является распространенной проблемой, независимо от вашей технологии или уровня опыта. Это может стать неприятной проблемой, почему исключения вызывают проблемы в коде. При отладке исключения в Visual Studio мы хотим уменьшить это разочарование, предоставив сведения об исключении, которые помогут вам быстрее отладить проблему.

![Помощник по исправлению ошибок](media/debugger-exception-helper-default.png)

## <a name="pause-on-the-exception"></a>Приостановить исключение
Когда отладчик прерывает работу при возникновении исключения, справа от этой строки кода появляется значок ошибки исключения. Рядом со значком исключения появится вспомогательный метод немодального исключения.

![Вспомогательный метод исключения рядом со строкой кода](media/debugger-exception-helper-locerror.png)

## <a name="inspect-exception-info"></a>Проверка сведений об исключении
Вы можете мгновенно прочитать тип исключения и сообщение об исключении в вспомогательном методе исключения, а также определить, было ли исключение вызвано или необработанным. Чтобы проверить и просмотреть свойства объекта исключения, щелкните ссылку **View Details (просмотреть сведения** ).

## <a name="analyze-null-references"></a>Анализ пустых ссылок
Начиная с Visual Studio 2017, для .NET и C/C++ Code при попадании в `NullReferenceException` или `AccessViolation`в вспомогательном приложении исключения отображаются данные анализа со значением NULL. Анализ отображается в виде текста под сообщением об исключении. На рисунке ниже информация отображается как "**s** имел значение null".

![Вспомогательный метод исключения NULL Analysis](media/debugger-exception-helper-default.png)


> [!NOTE]
> Для анализа пустых ссылок в управляемом коде требуется .NET версии 4.6.2. Анализ значений NULL сейчас не поддерживается для универсальная платформа Windows (UWP) и других приложений .NET Core. Он доступен только во время отладки кода, не имеющего оптимизаций JIT-кода.

## <a name="configure-exception-settings"></a>Настройка параметров исключений 
Можно настроить отладчик на прерывание при появлении исключения текущего типа из раздела **параметры исключений** в вспомогательном приложении исключения. Если отладчик приостанавливается при возникновении исключения, можно использовать флажок, чтобы отключить прерывание для этого типа исключения при возникновении в будущем. Если вы не хотите прерывать это конкретное исключение при возникновении в этом конкретном модуле, установите флажок рядом с именем модуля ( **за исключением случаев, когда вызвано из:** ) в окне **параметры исключений** . 

## <a name="inspect-inner-exceptions"></a>Проверка внутренних исключений 
Если исключение содержит внутренние исключения ([InnerException](https://docs.microsoft.com/dotnet/api/system.exception.innerexception), их можно просмотреть в вспомогательном методе исключения. При наличии нескольких исключений можно перемещаться между ними с помощью стрелок влево и вправо, расположенных над стеком вызовов.

![Вспомогательное приложение исключения с внутренним исключением](media/debugger-exception-helper-innerexception.png)

## <a name="inspect-rethrown-exceptions"></a>Проверка повторно созданных исключений
В случаях, когда исключение было `thrown` в помощнике по исключению отображается стек вызовов из первого момента возникновения исключения. Если исключение было создано несколько раз, отображается только стек вызовов из исходного исключения.

![Вспомогательное приложение исключения с повторно созданными исключениями](media/debugger-exception-helper-innerexception.png)

## <a name="share-a-debug-session-with-live-share"></a>Совместное использование сеанса отладки с Live Share
Из помощника по исключениям можно запустить сеанс [Live Share](https://docs.microsoft.com/visualstudio/liveshare/) , используя **сеанс Start Live Share.** .. Любой, кто присоединился к сеансу Live Share, может видеть вспомогательное средство исключения вместе с другими отладочными сведениями.
