---
title: Чтение и понимание кода C++ в Visual Studio
description: Узнайте, как использовать редактор кода C++ в Visual Studio для форматирования и понимания кода.
ms.date: 05/28/2019
ms.openlocfilehash: c5e4d7f3e53ef37649e3635d11cf99b10cb8a7ee
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66742030"
---
# <a name="read-and-understand-c-code-in-visual-studio"></a>Чтение и понимание кода C++ в Visual Studio

Редактор кода C++ и Visual Studio IDE предоставляют различные вспомогательные средства кодирования. Одни уникальны для C++, а другие фактически одинаковы для всех языков Visual Studio. Дополнительные сведения об общих функциях см. в разделе [Написание кода в редакторе кода и текста](/visualstudio/ide/writing-code-in-the-code-and-text-editor).  

## <a name="colorization"></a>Выделение цветом

Visual Studio выделяет цветом элементы синтаксиса, чтобы вы могли различать типы символов, такие как ключевые слова языка, имена типов, имена переменных, параметры функций, строковые литералы и т. д.

![Выделение кода цветом](../ide/media/code-outline-colorization.png "Выделение цветом в С++")

 Неиспользуемый код (например код в разделе #if 0) имеет более приглушенный цвет.

 ![Неактивный код](../ide/media/inactive-code-cpp.png "Неактивный код в С++")

Вы можете настраивать цвета. Для этого введите "шрифты" в поле **быстрого запуска** и выберите **Шрифты и цвета**. В диалоговом окне **Шрифты и цвета** прокрутите вниз до параметров C/C++, а затем выберите пользовательский шрифт и цвет.

## <a name="outlining"></a>Структуризация

Щелкните правой кнопкой мыши в любом месте файла исходного кода и выберите **Структура**, чтобы свернуть или развернуть блоки кода и (или) настраиваемые области. Так вы упростите просмотр, отображая только нужный вам код. Дополнительные сведения см. в разделе [Структура](/visualstudio/ide/outlining).

![Структурирование в С++](../ide/media/vs2015_cpp_outlining.png "Структурирование")

Если вы поместите курсор перед фигурной скобкой ({ или }), редактор выделит ее парную часть.

Другие параметры структурирования можно настроить, выбрав **Изменить** > **Структура** в главном меню.

## <a name="line-numbers"></a>Номера строк

Вы можете добавлять номера строк в проект. Для этого выберите **Средства** > **Параметры** > **Текстовый редактор** > **Все языки** > **Общие** или введите "номер строки" в поле **быстрого запуска (CTRL+Q)** . Номера строк можно задать для всех языков или определенных языков, включая C++.

## <a name="scroll-and-zoom"></a>Прокрутка и изменение масштаба

Вы можете увеличивать или уменьшать масштаб в редакторе. Для этого прокрутите колесико мыши, удерживая клавишу **CTRL**. Кроме того, изменить масштаб можно с помощью параметров масштабирования в левом нижнем углу.

![Элемент управления масштабом в С++](../ide/media/zoom-control.png "Элемент управления масштабом")

**Режим карты** для полосы прокрутки позволяет быстро прокручивать и просматривать файл кода, не покидая текущего расположения. Чтобы перейти непосредственно в это расположение, можно также щелкнуть в любом месте на карте кода.

![Карта кода в C++](../ide/media/vs2015-cpp-code-map.png "Карта кода")

Чтобы включить **режим карты**, введите "карта" в поле **быстрого запуска** на главной панели инструментов и выберите **Использовать режим карты прокрутки**. Дополнительные сведения см. в разделе [Практическое руководство. Отслеживание кода путем настройки полосы прокрутки](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar).

При включенном **режиме карты** полоса прокрутки выделяет изменения, внесенные в файл. Зеленый цвет означает, что изменения сохранены, а желтый — не сохранены.

## <a name="quick-info-and-parameter-info"></a>Краткие сведения и сведения о параметрах

Наведите указатель на любую переменную, функцию или другой символ, чтобы просмотреть сведения, включая объявление и комментарии.

::: moniker range="vs-2019"

![Краткие сведения в С++](../ide/media/quick-info-vs2019.png "Краткие сведения")

Подсказки с **краткими сведениями** включают ссылку для **поиска в Интернете**. Выберите **Средства** > **Параметры** > **Текстовый редактор** > **C++**  > **Представление**, чтобы указать поставщик поиска. 

Если в коде есть ошибка, можно навести указатель мыши на нее, чтобы в окне с **краткими сведениями** просмотреть сообщение об ошибке. Сообщение об ошибке также можно просмотреть в окне со списком ошибок.

![Краткие сведения об ошибке](../ide/media/quickinfo-on-error.png "Краткие сведения об ошибке")

::: moniker-end

::: moniker range="<=vs-2017"

![Краткие сведения в С++](../ide/media/quick-info.png "Краткие сведения")

Если в коде есть ошибка, можно навести указатель мыши на нее, чтобы в окне с **краткими сведениями** просмотреть сообщение об ошибке. Сообщение об ошибке также можно просмотреть в окне со **списком ошибок**.

![Краткие сведения об ошибке](../ide/media/quickinfo-on-error.png "Краткие сведения об ошибке")

::: moniker-end

При вызове функции в окне со **сведениями о параметрах** отображаются типы параметров и порядок их ввода.

![Сведения о параметрах в C++](../ide/media/parameter-info.png "Сведения о параметрах")

## <a name="peek-definition"></a>Показать определение

Наведите указатель мыши на объявление переменной или функции, щелкните правой кнопкой мыши, а затем выберите **Показать определение**, чтобы увидеть встроенное представление определения, не покидая текущее расположение. Дополнительные сведения см. в разделе [Команда "Показать определение" (ALT+F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).

![Просмотр определения в С++](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

##  <a name="f1-help"></a>Справка F1

Чтобы перейти непосредственно к соответствующему справочному разделу на сайте docs.microsoft.com, поместите курсор на любой тип, ключевое слово или функцию (либо сразу за ними) и нажмите клавишу **F1**. Клавиша **F1** также работает с элементами в списке ошибок и в некоторых диалоговых окнах.

## <a name="class-view"></a>Представление классов

**Представление классов** отображает доступный для поиска набор деревьев всех символов кода, а также их области и иерархий (родительских и дочерних), упорядоченных по проектам. Вы можете настроить отображаемое в **представлении классов** содержимое с помощью **параметров представления классов** (значок с шестеренкой в верхней части окна).

![Представление классов в C++](../ide/media/class-view.png "Представление классов")

## <a name="generate-graph-of-include-files"></a>Создать диаграмму включаемых файлов

Щелкните правой кнопкой мыши файл кода в проекте и выберите **Создать диаграмму включаемых файлов** для просмотра диаграммы файлов, которые являются включаемыми (из других файлов).

![Диаграмма включенных файлов в С++](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="view-call-hierarchy"></a>Просмотр иерархии вызовов

Щелкните правой кнопкой мыши любой вызов функции и просмотрите рекурсивный список всех функций, которые он вызывает, а также все функции, которые вызывают его. Каждую функцию в списке можно развернуть одинаковым образом. Дополнительные сведения см. в разделе [Иерархия вызовов](/visualstudio/ide/reference/call-hierarchy).

![Иерархия вызовов в С++](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="see-also"></a>См. также раздел

[Редактирование и рефакторинг кода C++](writing-and-refactoring-code-cpp.md)</br>
[Перемещение по базе кода С++ в Visual Studio](navigate-code-cpp.md)</br>
[Совместная работа с использованием Live Share для C++](live-share-cpp.md)