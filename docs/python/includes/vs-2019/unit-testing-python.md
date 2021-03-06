---
title: Модульное тестирование кода Python
description: Настройте модульное тестирование кода Python в Visual Studio и воспользуйтесь всеми преимуществами функций обнаружения, выполнения и отладки тестов в обозревателе тестов.
ms.date: 09/18/2019
ms.topic: include
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8adce700524c4ade6c627aa91480460f8f2571f2
ms.sourcegitcommit: 9f6f63a2d76c6e579b4b67a96ec86faba99ad1df
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2019
ms.locfileid: "71933490"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Выбор платформы тестирования для проекта Python

Visual Studio поддерживает две платформы тестирования для Python — [unittest](https://docs.python.org/3/library/unittest.html) и [pytest](https://pytest.org/en/latest/) (доступна в Visual Studio 2019, начиная с версии 16.3). По умолчанию при создании проекта Python платформа не выбрана. Чтобы указать платформу, щелкните правой кнопкой мыши имя проекта в обозреватель решений и выберите параметр **Свойства**. Открывается конструктор проектов, позволяющий настраивать тесты с помощью вкладки **Тест**. На этой вкладке можно выбрать платформу тестирования, используемую для вашего проекта. 

* Для платформы **unittest** корневой каталог проекта используется для обнаружения тестов. На вкладке **Тест** это расположение, а также текстовый шаблон для идентификации тестов можно изменить на значения, заданные пользователем.
* Для платформы **pytest** параметры тестирования, такие как расположение тестов и шаблоны имен файлов, указываются с помощью стандартного INI-файла конфигурации pytest. Дополнительные сведения см. в [справочной документации для pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref).

После сохранения выбранных параметров и платформы в обозревателе тестов инициируется обнаружение тестов. Если окно обозревателя тестов еще не открыто, перейдите на панель инструментов и выберите **Тест** > **Обозреватель тестов**.

## <a name="configure-testing-for-python-without-a-project"></a>Настройка тестирования для Python без проекта
Visual Studio позволяет запускать и тестировать существующий код Python без проекта, [открыв папку](../../quickstart-05-python-visual-studio-open-folder.md) с кодом Python. В этих случаях для настройки тестирования потребуется файл **PythonSettings.json**. 
1. Откройте существующий код Python с помощью параметра **Открыть локальную папку**. 

   ![Экран запуска Visual Studio](../../media/quickstart-open-folder/01-open-local-folder.png)

1. В окне обозревателя решений щелкните значок **Показать все файлы**, чтобы отобразить все файлы в текущей папке.

   ![Кнопка "Показать все файлы"](../../media/unit-test-show-files.png)

1. Перейдите к файлу **PythonSettings.json** в папке **Локальные параметры**. Если этот файл отсутствует в папке **Локальные параметры**, создайте его вручную.
   
1. Добавьте поле **TestFramework** в файл параметров и задайте для него значение **pytest** или **unittest** в зависимости от требуемой платформы тестирования.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > Если для платформы **unittest** в файле PythonSettings.json не указаны поля **UnitTestRootDirectory** and **UnitTestPattern**, они добавляются и получают значения по умолчанию "." и "test*.py", соответственно.

1. Если папка содержит каталог **src**, отличный от папки с вашими тестами, укажите путь к папке **src** с помощью поля **SearchPaths** в файле **PythonSettings.json**.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Сохраните изменения в файле PythonSettings.json, чтобы начать обнаружение тестов для указанной платформы. 
   > [!Note]
   > Если окно обозревателя тестов уже открыто нажатие клавиш **CTRL** + **R,A** также активирует обнаружение.

## <a name="discover-and-view-tests"></a>Обнаружение и просмотр тестов

По умолчанию Visual Studio определяет тесты **unittest** и **pytest** как методы, имена которых начинаются с `test`. Чтобы просмотреть обнаружение тестов, сделайте следующее:

1. Откройте [проект Python](../../managing-python-projects-in-visual-studio.md).

1. После загрузки проекта в Visual Studio щелкните проект правой кнопкой мыши в обозревателе решений и выберите платформу **unittest** или **pytest** на вкладке **Тест** в области свойств.
   > [!Note]
   > При использовании платформы pytest можно указать расположение тестов и шаблоны имен файлов с помощью стандартного INI-файла конфигурации pytest. По умолчанию используется папка рабочей области или проекта с шаблоном `test_*py` и `*_test.py`. Дополнительные сведения см. в [справочной документации для pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref).

1. Выбрав платформу, снова щелкните проект правой кнопкой мыши и выберите **Добавить** > **Новый Элемент**, затем **Модульный тест Python** и нажмите кнопку **Добавить**.

1. Это действие создает файл *test_1.py* с кодом, который импортирует стандартный модуль `unittest`, производный от тестового класса `unittest.TestCase`, и вызывает метод `unittest.main()` при запуске скрипта напрямую:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Если нужно, сохраните этот файл, а затем откройте **обозреватель тестов**, последовательно выбрав команды **Тест** > **Обозреватель тестов**.

1. **Обозреватель тестов** ищет тесты в проекте и отображает результаты, как показано ниже. Дважды щелкните тест, чтобы открыть его исходный файл.

    ![Обозреватель тестов со стандартным тестом test_A](../../media/unit-test-a-2.png) 

1. Когда тестов в проекте будет больше, их можно упорядочить в **обозревателе тестов**, используя команду **Группировать** на панели инструментов:

    ![Группировка на панели инструментов в меню обозревателя тестов](../../media/unit-test-group-menu-2.png) 

1. Также вы можете ввести текст в поле **Поиск**, чтобы отфильтровать тесты по именам.

Дополнительные сведения о модуле `unittest` и создании тестов можно получить в [документации по Python 2.7](https://docs.python.org/2/library/unittest.html) или в [документации по Python 3.7](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="run-tests"></a>Выполнить тесты

В **обозревателе тестов** можно запустить тесты несколькими способами:

- Команда **Запустить все** явно выполняет все тесты из списка (с учетом фильтров).
- Команда меню **Запуск** позволяет одновременно выполнить все тесты, которые завершились успешно, завершились неудачно или еще не выполнялись.
- Также можно выбрать один или несколько тестов, щелкнуть их правой кнопкой мыши и выбрать команду **Запустить выбранные тесты**.

Тесты выполняются в фоновом режиме, а **обозреватель тестов** обновляет их состояние по мере завершения:

- Успешно выполненные тесты обозначаются зеленым флажком, и для них указывается затраченное время:

    ![Состояние успешного выполнения для теста test_A](../../media/unit-test-A-pass.png)

- Неудачные тесты обозначаются красным крестом и дополняются ссылкой **Output** (Вывод), которая позволяет изучить выходные данные на консоли и выходные данные `unittest`, полученные по результатам этого теста:

    ![Состояние неудачного выполнения для теста test_A](../../media/unit-test-A-fail.png)

    ![Описание причин неудачи для теста test_A](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Отладка тестов

Модульные тесты являются частью кода проекта, и в них могут встречаться ошибки, как и в любом другом коде. Периодически тест следует запускать в отладчике, где можно установить точки останова, просмотреть переменные или выполнить код пошагово. Также Visual Studio предоставляет средства диагностики для модульных тестов.

> [!Note]
> По умолчанию для тестовой отладки использует отладчик ptvsd 4. Если вы хотите использовать вместо него ptvsd 3, можно выбрать параметр **Использовать устаревший отладчик** в меню **Сервис** > **Параметры** > **Python** > **Отладка**. 

Чтобы начать отладку, установите в коде начальную точку останова, а затем щелкните в **обозревателе тестов** правой кнопкой мыши этот тест (или выделенный набор тестов) и выберите **Отладить выбранные тесты**. Visual Studio запускает отладчик Python, как для обычного кода приложения.

![Отладка теста](../../media/unit-test-debugging.png)

Вы также можете использовать команду **Анализ покрытия кода для выбранных тестов**. Дополнительные сведения см. в разделе [Использование покрытия кода для определения объема протестированного кода](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).
