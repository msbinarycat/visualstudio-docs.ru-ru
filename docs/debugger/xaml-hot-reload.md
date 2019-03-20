---
title: Разрабатывайте и отлаживайте XAML с помощью XAML "Горячий" перезагрузки
description: Перезагрузить "Горячий" XAML или XAML, изменением и продолжением, позволяет вносить изменения в код XAML во время выполнения приложения
ms.custom: ''
ms.date: 02/28/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a002c3876eecf0f31a8d104fa235b1208af90699
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57875262"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Создавать и отлаживать выполнение кода XAML с горячей перезагрузить XAML в Visual Studio

Visual Studio XAML "Горячий" перезагрузить построение приложения WPF или UWP пользовательского интерфейса, позволяя внести изменения в код XAML во время работы приложения. Эта функция позволяет поэтапно создавать и тестировать код XAML с помощью программы преимуществ запущенном приложении контекст данных, состояние проверки подлинности и другие сложности реальных трудно моделирование во время разработки.

"Горячий" перезагрузить XAML особенно полезна в следующих сценариях:

* Устранение проблем пользовательского интерфейса, найденных в коде XAML, после запуска приложения в режиме отладки.

* Сборку новый компонент пользовательского интерфейса для приложения, которое находится в стадии разработки, а использование преимуществ контекст среды выполнения приложения.

|Поддерживаемые типы приложений|Операционная система и средства|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+</br>Windows 7 и более поздних версий |
|Приложения универсальной Windows (UWP)|Windows 10 и более поздних версий, с помощью [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

> [!NOTE]
> Visual Studio XAML "Горячий" Перезагрузить сейчас поддерживается только при запуске приложения в Visual Studio с подключенным отладчиком (**F5** или **начать отладку**). Не удается включить эту функцию с помощью *присоединение к процессу*.

## <a name="known-limitations"></a>Известные ограничения

Ниже перечислены известные что ограничения XAML "Горячий" перезагрузить. Чтобы избежать возникновения каких-либо ограничений, в котором выполняется, только для остановки отладчика, а затем завершите операцию.

|Ограничение|WPF|UWP|Примечания|
|-|-|-|-|
|Привязки событий к элементам управления во время работы приложения|Не поддерживается|Не поддерживается|Ошибка: *обеспечить сбой события*|
|Создание объектов ресурса в словаре ресурсов, например, в окно страницы приложения или *App.xaml*|Не поддерживается|Поддерживается|Пример: добавление ```SolidColorBrush``` в словарь ресурсов для использования в качестве ```StaticResource```.</br>Примечание: Статические ресурсы, преобразователи стиля и других элементов, записанных в словарь ресурсов может быть применен/используется при использовании "Горячий" перезагрузить XAML. Создание ресурса не поддерживается.</br> Изменение словаря ресурсов ```Source``` свойство.| 
|Добавление новых элементов управления, классы, windows или другие файлы в проект во время работы приложения|Не поддерживается|Не поддерживается|Нет|
|Управление пакетами NuGet (Добавление/удаление и обновление пакетов)|Не поддерживается|Не поддерживается|Нет|
|Изменение данных, привязка, которая использует расширение разметки {x: Bind}|Н/Д|Поддерживается в Visual Studio 2019 г. и более поздних версий|Не поддерживается в Visual Studio 2018 г. или более ранних версий|

## <a name="error-messages"></a>Сообщения об ошибках

Вы можете столкнуться следующие ошибки при использовании "Горячий" перезагрузить XAML.

|Сообщение об ошибке|Описание|
|-|-|-|
|Убедитесь, событие не удалось|Ошибка означает, что вы пытаетесь связать один из элементов управления, которые не поддерживается, пока приложение запущено событие.|
|Функция "Изменить и продолжить" XAML не нашла элементы для обновления.|Ошибка возникает при редактировании XAML, "Горячий" перезагрузить не удается обновить в приложении.</br> Иногда эту ошибку можно исправить с помощью работающем приложении для перехода к представлению, в которых используется XAML.</br> В некоторых случаях эта ошибка означает, что конкретное изменение не может использоваться только после перезапуска сеанса отладки. |
|Это изменение не поддерживается во время сеанса отладки.|Ошибка указывает, что изменение, которое вы пытаетесь не поддерживается "Горячий" перезагрузить XAML. Остановить сеанс отладки, внесите изменения и перезапустите сеанс отладки.|