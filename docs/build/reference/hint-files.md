---
title: Файлы подсказок
ms.date: 02/26/2019
f1_keywords:
- cpp.hint
- vc.hint.file
helpviewer_keywords:
- stop file
- cpp.hint
- hint file
- cpp.stop
- Class View, hint file
ms.assetid: 17194f66-cf62-4523-abec-77db0675ab65
ms.openlocfilehash: 3d8b3be76fea454ed3b3dd3fd2a44174f34c065c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826746"
---
# <a name="hint-files"></a>Файлы подсказок

*Файл указаний* содержит макрос, который в противном случае вызвал бы пропуск областей кода средством синтаксического анализа базы данных просмотра C++. При открытии проекта Visual C++ система синтаксического анализа анализирует код в каждом исходном файле проекта и создает базу данных с информацией обо всех идентификаторах. Затем интегрированная среда разработки использует эту информацию для поддержки таких функций просмотра кода как обозреватель **представления классов** и **панель навигации**.

Средство синтаксического анализа базы данных просмотра C++ — это средство нечеткого синтаксического анализа, которое может анализировать большие объемы кода за короткий промежуток времени. Высокая скорость его работы объясняется в том числе и тем, что оно пропускает содержимое блоков. Например, оно записывает только расположение и параметры функции и игнорирует ее содержимое. Определенные макросы могут вызвать проблемы для эвристических правил, используемых для определения начала и конца блока. Эти проблемы приводят к тому, что области кода записываются неправильно.

Пропущенные области кода могут проявляться несколькими способами:

- Отсутствуют типы и функции в **представлении классов**, в окне **Перейти к** и на **панели навигации**

- Неправильные области на **панели навигации**

- Предложения по **Созданию объявления или определения** функций, которые уже определены

Файл указаний содержит настраиваемые пользователем указания, которые имеют тот же синтаксис, что и определения макросов C/C++. В Visual C++ есть внутренний файл указаний, которого достаточно для большинства проектов. Однако вы можете создавать собственные файлы указаний, чтобы улучшить работу средства синтаксического анализа специально для вашего проекта.

> [!IMPORTANT]
> При изменении или добавлении файла указаний необходимо выполнить дополнительные действия для того, чтобы изменения вступили в силу:
> - В версиях ранее Visual Studio 2017 версии 15.6: Удалите SDF-файл и (или) файл VC.db в решении для всех изменений.
> - В Visual Studio 2017 версии с 15.6 по 15.9: После добавления новых файлов указаний закройте и повторно откройте решение.

## <a name="scenario"></a>Сценарий

```cpp
#define NOEXCEPT noexcept
void Function() NOEXCEPT
{
}
```

Без файла указаний `Function` не отображается в **представлении классов**, в окне **Перейти к** и на **панели навигации**. После добавления файла указаний с этим определением макроса средство синтаксического анализа может распознать и заменить макрос `NOEXCEPT`, что позволяет ему корректно проанализировать функцию:

```cpp.hint
#define NOEXCEPT
```

## <a name="disruptive-macros"></a>Макросы, нарушающие работу

Существует две категории макросов, нарушающие работу средства синтаксического анализа:

- Макросы, которые инкапсулируют ключевые слова, декорирующие функцию

   ```cpp
   #define NOEXCEPT noexcept
   #define STDMETHODCALLTYPE __stdcall
   ```

   Для следующих типов макросов в файле указаний необходимо указать только имя макроса:

   ```cpp.hint
   #define NOEXCEPT
   #define STDMETHODCALLTYPE
   ```

- Макросы, которые содержат несбалансированные скобки

   ```cpp
   #define BEGIN {
   ```

   Для следующих типов макросов в файле указаний необходимо указать имя макроса и его содержимое:

   ```cpp.hint
   #define BEGIN {
   ```

## <a name="editor-support"></a>Поддержка редактора

Начиная с Visual Studio 2017 версии 15.8 существуют несколько функций, которые позволяют определить макросы, нарушающие работу средства синтаксического анализа:

- Макросы, которые находятся внутри областей, пропущенных анализатором, выделяются.

- Существует быстрое действие для создания файла указаний, включающего выделенный макрос, или (при наличии существующего файла указаний) для добавления макроса в файл указаний.

![Выделенный макрос](media/hint-squiggle-and-actions.png "Выделение волнистой линией и быстрые действия")

После выполнения любого из быстрых действий средство анализа повторно анализирует файлы, на которые повлиял файл указаний.

По умолчанию проблемный макрос выделяется как предложение. Выделение можно изменить на более заметное, например, подчеркивание красной или зеленой волнистой линией. Используйте параметр **Макросы в пропущенных областях просмотра** в разделе **Подчеркивание кода**, который можно открыть, выбрав **Инструменты** > **Параметры** > **Текстовый редактор** > **C/C++** > **Представление**.

![Параметр "Макросы в пропущенных областях просмотра"](media/skipped-regions-squiggle-option.png "Вариант подчеркивания пропущенных областей волнистой линией")

## <a name="display-browsing-database-errors"></a>Отображение ошибок базы данных просмотра

При выборе пункта меню **Проект** > **Отображение ошибок базы данных просмотра** откроется **Список ошибок**, содержащий все области, которые не удалось проанализировать. Команда призвана упростить создание начального файла указаний. Тем не менее, средство синтаксического анализа не может определить, был ли причиной ошибки макрос, нарушающий работу средства синтаксического анализа, поэтому вам необходимо оценить каждую ошибку самостоятельно. Выполните команду **Показать ошибки базы данных просмотра** и перейдите к каждой ошибке, чтобы загрузить соответствующий файл в редакторе. После загрузки файла все макросы, входящие в область, будут выделены. Вы можете вызвать быстрые действия, чтобы добавить их в файл указаний. После обновления файла указаний список ошибок обновляется автоматически. Кроме того, если вы изменяете файл указаний вручную, можно использовать команду **Повторить сканирование решения**, чтобы запустить обновление.

## <a name="architecture"></a>Архитектура

Файлы указаний относятся к физическим каталогам, а не к логическим каталогам, отображаемым в **обозревателе решений**. Чтобы файл указаний был применен, добавлять его в проект не нужно. Система анализа использует файлы указаний только при анализе исходных файлов.

Каждый файл указаний называется **cpp.hint**. Файлы указаний могут размещаться в различных каталогах, но в отдельном каталоге может находиться лишь один такой файл.

В проекте может использоваться как один или несколько файлов указаний, так и ни одного. При отсутствии файлов указаний система анализа использует методики восстановления после ошибок, чтобы пропускать нераспознаваемый исходный код. В противном случае система анализа использует указанную ниже стратегию для обнаружения и сбора указаний.

### <a name="search-order"></a>Порядок поиска

Система анализа ищет файлы указаний в каталогах в следующем порядке.

- Каталог, содержащий пакет установки для Visual C++ (**vcpackages**). Этот каталог содержит встроенный файл указаний, описывающий символы в часто используемых системных файлах, таких как **windows.h**. Поэтому проект автоматически наследует основную часть нужных ему указаний.

- Путь из корневого каталога исходного файла к каталогу, содержащему сам исходный файл. В типичном проекте Visual C++ корневой каталог содержит файл проекта или решения.

   Исключением из этого правила является ситуация, когда *стоп-файл* находится в пути к исходному файлу. Стоп-файл — это любой файл с именем **cpp.stop**. Стоп-файл обеспечивает дополнительный уровень контроля над порядком поиска. Вместо того чтобы начать с корневого каталога, система анализа выполняет поиск из каталога, содержащего стоп-файл, по направлению к каталогу, содержащему исходный файл. В обычных проектах стоп-файлы не требуются.

### <a name="hint-gathering"></a>Сбор указаний

Файл указаний может не содержать ни одного указания или содержать более нуля *указаний*. Определение или удаление указания выполняется как и для макроса C/C++. То есть директива препроцессора `#define` создает или переопределяет указание, а директива `#undef` удаляет его.

Система анализа открывает каждый файл указаний в указанном выше порядке поиска. Она собирает указания из каждого файла в набор *полезных указаний*, а затем использует эти полезные указания для интерпретации идентификаторов в коде.

Система анализа использует эти правила для сбора указаний:

- Если новое указание задает имя, которое еще не было определено, новое указание добавляет имя в список полезных указаний.

- Если новое указание задает уже определенное имя, существующее имя переопределяется.

- Если новое указание является директивой `#undef`, указывающей имеющееся полезное указание, существующее указание удаляется.

Первое правило означает, что полезные указания наследуются от ранее открытых файлов указаний. Два последних правила означают, что более поздние указания в порядке поиска могут переопределять более ранние. Например, можно переопределить любые имеющиеся указания, создав файл указаний в каталоге с исходным файлом.

Описание сбора указаний см. в разделе [Пример](#example) ниже.

### <a name="syntax"></a>Синтаксис

Указания создаются и удаляются с использованием такого же синтаксиса, что и у директив препроцессора, создающих и удаляющих макросы. На самом деле система анализа использует препроцессор C/C++ для оценки указаний. Дополнительные сведения о директивах препроцессора см. в разделах [Директива #define (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md) и [Директива #undef (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md).

Единственными необычными элементами синтаксиса являются строки замены `@<`, `@=` и `@>`. Эти строки замены для конкретного файла указаний используются только в макросах *схемы*. Схема — это набор макросов, связывающих данные, функции и события с другими данными, функциями и обработчиками событий. Например, `MFC` использует схемы для создания [схем сообщений](../../mfc/reference/message-maps-mfc.md), а `ATL` — [схем объектов](../../atl/reference/object-map-macros.md). Строки замены для конкретного файла указаний задают начальный, промежуточные и конечный элементы схемы. Важно только имя макроса схемы. Таким образом, каждая строка замены намеренно скрывает реализацию макроса.

В указаниях используется следующий синтаксис:

|Синтаксис|Значение|
|------------|-------------|
|`#define` *имя_указания* *строка_замены*<br /><br /> `#define` *имя_указания* `(` *параметр*, ...`)`*строка_замены*|Директива препроцессора, которая определяет новое указание или переопределяет существующее. После директивы препроцессор заменяет каждый экземпляр *имени_указания* в исходном коде на *строку_замены*.<br /><br /> Вторая форма синтаксиса определяет указание, подобное функции. Если в исходном коде находится подобное функции указание, препроцессор сначала заменяет каждый экземпляр *параметра* в *строке_замены* на соответствующий аргумент в исходном коде, а затем заменяет *имя_указания* на *строку_замены*.|
|`@<`|*Строка_замены* для конкретного файла указаний задает начало набора элементов схемы.|
|`@=`|*Строка_замены* для конкретного файла указаний задает промежуточный элемент схемы. Схема может содержать несколько элементов схемы.|
|`@>`|*Строка_замены* для конкретного файла указаний задает конец набора элементов схемы.|
|`#undef` *имя_указания*|Директива препроцессора, удаляющая имеющее указание. Имя указания предоставляется идентификатором *имя_указания*.|
|`//` *комментарий*|Однострочный комментарий.|
|`/*` *комментарий* `*/`|Многострочный комментарий.|

## <a name="example"></a>Пример

В этом примере показано, как выполняется сбор указаний из соответствующих файлов. Стоп-файлы в этом примере не используются.

На рисунке показаны некоторые физические каталоги в проекте Visual C++. Файлы указаний находятся в каталогах `vcpackages`, `Debug`, `A1` и `A2`.

### <a name="hint-file-directories"></a>Каталоги файлов указаний

![Общие и зависящие от проекта каталоги файлов указаний.](media/hintfile.png "HintFile")

### <a name="directories-and-hint-file-contents"></a>Каталоги и содержимое файлов указаний

В списке ниже приведены каталоги в этом проекте, содержащие файлы указаний, и содержимое этих файлов. Приведены лишь некоторые из указаний в файле указаний каталога `vcpackages`:

- vcpackages

    ```cpp.hint
    // vcpackages (partial list)
    #define _In_
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)
    ```

- Отладка

    ```cpp.hint
    // Debug
    #undef _In_
    #define OBRACE {
    #define CBRACE }
    #define RAISE_EXCEPTION(x) throw (x)
    #define START_NAMESPACE namespace MyProject {
    #define END_NAMESPACE }
    ```

- A1

    ```cpp.hint
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    ```

- A2

    ```cpp.hint
    // A2
    #undef OBRACE
    #undef CBRACE
    ```

### <a name="effective-hints"></a>Полезные указания

В следующей таблице приведены полезные указания для исходных файлов в этом проекте:

- Исходный файл: A1_A2_B.cpp

- Полезные указания:

    ```cpp.hint
    // vcpackages (partial list)
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)
    // Debug...
    #define RAISE_EXCEPTION(x) throw (x)
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    // ...Debug
    #define END_NAMESPACE }
    ```

Эти замечания применяются к предыдущему списку:

- Эти полезные указания получены из каталогов `vcpackages`, `Debug`, `A1` и `A2`.

- Директива **#undef** в файле указаний `Debug` удалила указание `#define _In_` в файле из каталога `vcpackages`.

- Файл указаний в каталоге `A1` переопределяет `START_NAMESPACE`.

- Указание `#undef` в каталоге `A2` удалило указания для `OBRACE` и `CBRACE` в файле из каталога `Debug`.

## <a name="see-also"></a>См. также

[Типы файлов, создаваемых для проектов Visual C++](file-types-created-for-visual-cpp-projects.md)<br>
[Директива #define (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)<br>
[Директива #undef (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)<br>
[Заметки SAL](../../c-runtime-library/sal-annotations.md)<br>
