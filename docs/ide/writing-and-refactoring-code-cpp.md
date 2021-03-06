---
title: "Написание и рефакторинг кода (C++) | Документы Microsoft"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b68d4190d8e3fc5040879eba4f8888467a07adf5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="writing-and-refactoring-code-c"></a>Написание и рефакторинг кода (C++)

Редактор кода Visual C++ и IDE предоставляют различные вспомогательные средства кодирования. Одни уникальны для C++, а другие фактически одинаковы для всех языков Visual Studio. Дополнительные сведения об общих функциях см. в разделе [написание кода в редакторе кода и текста](/visualstudio/ide/writing-code-in-the-code-and-text-editor). Параметры для включения и настройки функции C++ находятся в [текстовый редактор, C++, Дополнительно](/visualstudio/ide/reference/options-text-editor-c-cpp-advanced) диалогового окна (**средства &#124; Параметры &#124; Текстовый редактор &#124; C/C++ &#124; Расширенный** или введите «C++ Дополнительно» в **быстрого запуска**). После выбора параметра, который нужно задать, чтобы получить дополнительную справку, нажав клавишу **F1** Если диалоговое окно находится в фокусе. Для общих параметров форматирования кода введите `Editor C++` в **быстрого запуска**.

Экспериментальные функции, которые могут или не могут быть включены в будущих версиях Visual Studio, можно найти на [текстовый редактор C++ экспериментальный](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental) диалогового окна. В Visual Studio 2017 г. Вы можете включить **прогнозной Intellisense** в этом диалоговом окне.

## <a name="adding-new-code"></a>Добавление нового кода

После создания проекта можно начать кодирование в созданных файлах. Чтобы добавить новые файлы, щелкните правой кнопкой мыши узел проекта в обозревателе решений и выберите **Добавить &#124; Новый**.

Для задания параметров форматирования, например отступы, завершение скобок и раскраску, введите `C++ Formatting` в **быстрого запуска** окна.

### <a name="intellisense"></a>IntelliSense

IntelliSense — это название набора возможностей, предоставляющих встроенные сведения о членах, типах и перегрузке возможностей. На следующем рисунке показан раскрывающийся список членов, отображаемый при вводе данных на клавиатуре. Для ввода выбранного текста элемента в файл кода можно нажать клавишу TAB.

![C# 43; &#43; раскрывающийся список элементов](../ide/media/vs2015_cpp_statement_completion.png "vs2015_cpp_statement_completion")

Дополнительные сведения в разделе [Intellisense для Visual C++](/visualstudio/ide/visual-cpp-intellisense).

### <a name="insert-snippets"></a>Вставка фрагментов

Фрагмент — это предварительно определенная часть исходного кода. Щелкните правой кнопкой мыши одну точку или выбранный текст для вставки фрагмента или размещения выбранного текста внутри фрагмента. На следующем рисунке показана процедура размещения выбранного оператора в цикле for. На последнем изображении желтым цветом выделены редактируемые поля, доступ к которым осуществляется с помощью клавиши TAB. Дополнительные сведения см. в статье [Фрагменты кода](/visualstudio/ide/code-snippets).

![Visual C# 43; &#43; Вставить фрагмент Drop &#45; вниз](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")

### <a name="add-class"></a>Добавить класс

Добавьте новый класс из **проекта** меню с помощью мастера классов.

![Добавьте новый класс в Visual C# 43; &#43; ] (../ide/media/vs2015_cpp_add_class.png "vs2015_cpp_add_class")

### <a name="class-wizard"></a>Мастер классов

Изменение или проверка существующего класса либо добавление нового класса с помощью мастера классов. Дополнительные сведения см. в разделе [Добавление функциональных возможностей с помощью мастеров кода (C++)](../ide/adding-functionality-with-code-wizards-cpp.md).

![Visual C# 43; &#43; Класс мастер](../ide/media/vs2015_cpp_class_wizard.png "vs2015_cpp_class_wizard")

## <a name="refactoring"></a>Рефакторинг

Рефакторинг доступны в контекстном меню быстрое действие или щелкнув [лампочки](/visualstudio/ide/perform-quick-actions-with-light-bulbs) в редакторе.  Некоторые находятся в **Правка > рефакторинг** меню.  Эти функции включают перечисленные ниже.

* [Переименование](refactoring/rename.md)
* [Извлечение функции](refactoring/extract-function.md)
* [Реализация чистых виртуальных функций](refactoring/implement-pure-virtuals.md)
* [Создание объявления или определения](refactoring/create-declaration-definition.md)
* [Перемещение определения функции](refactoring/move-definition-location.md)
* [Преобразование в необработанный строковый литерал](refactoring/convert-to-raw-string-literal.md)
* [Изменение сигнатуры](refactoring/change-signature.md)

## <a name="navigate-and-understand"></a>Перейти и понять

Visual C++ использует многие возможности навигации кода с другими языками. Дополнительные сведения см. в разделе [перемещение по коду](/visualstudio/ide/navigating-code) и [Просмотр структуры кода](/visualstudio/ide/viewing-the-structure-of-code).

### <a name="quickinfo"></a>Краткие сведения

Наведите указатель мыши на переменную для просмотра сведений о ее типе.

![Краткие сведения Visual C&#43;&#43;](../ide/media/vs2015_cpp_quickinfo.png "vs2015_cpp_quickInfo")

### <a name="open-document-navigate-to-header"></a>Открыть документ (Перейти к заголовку)

Щелкните правой кнопкой мыши имя заголовка в директиве `#include` и откройте файл заголовка.

![Visual C# 43; &#43; Откройте пункт меню документа](../ide/media/vs2015_cpp_open_document.png "vs2015_cpp_open_document")

### <a name="peek-definition"></a>Показать определение

Наведите указатель мыши на объявление переменной или функции, щелкните правой кнопкой мыши, затем выберите **Показать определение** чтобы увидеть встроенное представление его определения. Дополнительные сведения см. в разделе [Показать определение (Alt + F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).

![Visual C# 43; &#43; Показать определение](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

### <a name="go-to-definition"></a>Перейти к определению

Наведите указатель мыши на объявление переменной или функции, щелкните правой кнопкой мыши, затем выберите **перейти к определению** открыть документ, в котором определен объект.

### <a name="view-call-hierarchy"></a>Просмотр иерархии вызовов

Щелкните правой кнопкой мыши любой вызов функции и просмотрите рекурсивный список всех функций, которые он вызывает, а также все функции, которые вызывают его. Каждую функцию в списке можно развернуть одинаковым образом. Дополнительные сведения см. в разделе [иерархии вызовов](/visualstudio/ide/reference/call-hierarchy).

![Visual C# 43; &#43; Иерархия вызовов](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

### <a name="toggle-header--code-file"></a>Переключение между файлами заголовков и кода

Щелкните правой кнопкой мыши и выберите **заголовок переключателя / файл кода** для переключения между файлом заголовка и связанным файлом кода.

### <a name="outlining"></a>структуризация

Щелкните правой кнопкой мыши файл исходного кода и выберите **структура** Чтобы свернуть или развернуть определения и (или) настраиваемые области для упрощения просмотра только нужных вам частей интерес. Дополнительные сведения см. в разделе [Структура](/visualstudio/ide/outlining).

![Visual C# 43; &#43; Структурирование](../ide/media/vs2015_cpp_outlining.png "vs2015_cpp_outlining")

### <a name="scroll-bar-map-mode"></a>Режим карты для полосы прокрутки

Режим карты для полосы прокрутки позволяет быстро прокручивать и просматривать файл кода, фактически не покидая текущего расположения. Чтобы перейти непосредственно в это расположение, можно также щелкнуть в любом месте на карте кода.

![Карта кода в Visual C# 43; &#43; ] (../ide/media/vs2015_cpp_code_map.png "vs2015_cpp_code_map")

### <a name="generate-graph-of-include-files"></a>Создать диаграмму включаемых файлов

Щелкните правой кнопкой мыши файл кода в проекте и выберите **создать диаграмму включаемых файлов** для просмотра диаграммы, из которых входят другие файлы.

![Visual C# 43; &#43; граф включаемых файлов](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

### <a name="f1-help"></a>Справка F1

Для перехода непосредственно к соответствующему справочному разделу MSDN поместите курсор на любой тип, ключевое слово или функцию (либо сразу за ними) и нажмите клавишу F1. Клавиша F1 также работает для элементов в списке ошибок и в некоторых диалоговых окнах.

### <a name="quick-launch"></a>Быстрый запуск

Для быстрого перехода к любому окну или инструменту в среде Visual Studio просто введите его имя в окне «Быстрый запуск» в правом верхнем углу пользовательского интерфейса. Список автоматического завершения будет предлагать варианты при вводе данных на клавиатуре.

![Быстрый запуск Visual Studio](../ide/media/vs2015_cpp_quick_launch.png "vs2015_cpp_quick_launch")
