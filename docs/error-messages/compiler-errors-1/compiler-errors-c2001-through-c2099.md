---
title: "C2000 ошибки компилятора через C2099 | Документы Microsoft"
ms.custom: 
ms.date: 11/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2000
- C2016
- C2023
- C2024
- C2025
- C2029
- C2031
- C2035
- C2037
- C2038
- C2049
- C2068
- C2076
- C2080
- C2096
- C2098
helpviewer_keywords:
- C2000
- C2016
- C2023
- C2024
- C2025
- C2029
- C2031
- C2035
- C2037
- C2038
- C2049
- C2068
- C2076
- C2080
- C2096
- C2098
dev_langs: C++
ms.assetid: d99a19eb-eeeb-4181-9b33-9cbe4459767b
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8575e067f376f98c8312496b74bd05ba3d9bfce1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-errors-c2000-through-c2099"></a>C2000 ошибки компилятора через C2099

Статьи в этом разделе документации объясняется подмножество сообщения об ошибках, которые создаются компилятором.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Сообщения об ошибках

|Error|Сообщение|
|-----------|-------------|
|C2000 ошибки компилятора|НЕИЗВЕСТНАЯ ошибка выберите команду технической поддержки, в меню справки Visual C++ или откройте Справочный файл технической поддержки для получения дополнительной информации|
|[Ошибка компилятора C2001](compiler-error-c2001.md)|символ новой строки в константе|
|[Ошибка компилятора C2002](compiler-error-c2002.md)|Недопустимая константа Юникода|
|[Ошибка компилятора C2003](compiler-error-c2003.md)|Ожидается «идентификатор определения»|
|[Ошибка компилятора C2004](compiler-error-c2004.md)|требуется "defined(id)"|
|[Ошибка компилятора C2005](compiler-error-c2005.md)|#line требуется номер строки, найден "*маркера*"|
|[Ошибка компилятора C2006](compiler-error-c2006.md)|"*директивы*": требуется имя файла, найден "*маркера*"|
|[Ошибка компилятора C2007](compiler-error-c2007.md)|#define синтаксиса|
|[Ошибка компилятора C2008](compiler-error-c2008.md)|"*символ*": требуется в макроопределении|
|[Ошибка компилятора C2009](compiler-error-c2009.md)|повторное использование формального макроса "*идентификатор*"|
|[Ошибка компилятора C2010](compiler-error-c2010.md)|"*символ*": непредвиденная в списке формальных параметров макроса|
|[Ошибка компилятора C2011](compiler-error-c2011.md)|"*идентификатор*": "*типа*" повторное определение типа|
|[Ошибка компилятора C2012](compiler-error-c2012.md)|отсутствует имя после "<"|
|[Ошибка компилятора C2013](compiler-error-c2013.md)|отсутствует ">"|
|[Ошибка компилятора C2014](compiler-error-c2014.md)|команда препроцессора не должна начинаться с пробела|
|[Ошибка компилятора C2015](compiler-error-c2015.md)|слишком много знаков в константе|
|C2016 ошибки компилятора|C требуется наличие по крайней мере один член структуры или объединения|
|[Ошибка компилятора C2017](compiler-error-c2017.md)|Недопустимая escape-последовательность|
|[Ошибка компилятора C2018](compiler-error-c2018.md)|неизвестный символ "0 x*значение*"|
|[Ошибка компилятора C2019](compiler-error-c2019.md)|ожидается директива препроцессора, найден "*символ*"|
|[Ошибка компилятора C2020](compiler-error-c2020.md)|"*член*": "*класс*" переопределение члена|
|[Ошибка компилятора C2021](compiler-error-c2021.md)|не требуется экспоненциальное значение "*символ*"|
|[Ошибка компилятора C2022](compiler-error-c2022.md)|"*номер*": слишком большой для знака|
|C2023 ошибки компилятора|"*идентификатор*": выравнивание (*Число1*) отличается от предшествующего объявления (*число2*)|
|C2024 ошибки компилятора|атрибут «alignas» относится к переменным, элементам данных и только к типам тегов|
|C2025 ошибки компилятора|файл интерфейса двоичного модуля недопустим или поврежден: "*filename*"|
|[Ошибка компилятора C2026](compiler-error-c2026.md)|слишком большая строка, замыкающие знаки сокращены|
|[Ошибка компилятора C2027](compiler-error-c2027.md)|Использование неопределенного типа "*типа*"|
|[Ошибка компилятора C2028](compiler-error-c2028.md)|член структуры (объединения) должен находиться в ее (его) пределах|
|C2029 ошибки компилятора|выражение слева от "*маркера*«указывает, не определен класс, структура или интерфейс»*идентификатор*"|
|[Ошибка компилятора C2030](compiler-error-c2030.md)|деструктор с модификатором доступа protected private не может быть членом класса, объявленного как sealed|
|C2031 ошибки компилятора|виртуальный деструктор с "*специальных возможностей*" специальные возможности для этого типа не допускается|
|[Ошибка компилятора C2032](compiler-error-c2032.md)|"*идентификатор*": функция не может быть членом структуры или объединения "*типа*"|
|[Ошибка компилятора C2033](compiler-error-c2033.md)|"*идентификатор*": битовое поле не может иметь косвенное обращение|
|[Ошибка компилятора C2034](compiler-error-c2034.md)|"*идентификатор*": тип битового поля слишком мал для заданного числа битов|
|C2035 ошибки компилятора|Невиртуальный деструктор с "*специальных возможностей*" специальные возможности для этого типа не допускается|
|[Ошибка компилятора C2036](compiler-error-c2036.md)|"*идентификатор*": Неизвестный размер|
|C2037 ошибки компилятора|выражение слева от "*идентификатор*«определяет не определено структуры или объединения»*типа*"|
|C2038 ошибки компилятора|пространство имен std не может быть встроенной|
|[Ошибка компилятора C2039](compiler-error-c2039.md)|"*идентификатор1*": не является членом "*идентификатор2*"|
|[Ошибка компилятора C2040](compiler-error-c2040.md)|"*оператор*": "*идентификатор1*«отличается по уровням косвенного обращения от»*идентификатор2*"|
|[Ошибка компилятора C2041](compiler-error-c2041.md)|Недопустимая цифра "*символ*«для базового»*номер*"|
|[Ошибка компилятора C2042](compiler-error-c2042.md)|зарезервированные слова signed и unsigned являются взаимоисключающими|
|[Ошибка компилятора C2043](compiler-error-c2043.md)|недопустимый break|
|[Ошибка компилятора C2044](compiler-error-c2044.md)|недопустимый continue|
|[Ошибка компилятора C2045](compiler-error-c2045.md)|"*идентификатор*": Метка переопределена|
|[Ошибка компилятора C2046](compiler-error-c2046.md)|недопустимый вариант выбора|
|[Ошибка компилятора C2047](compiler-error-c2047.md)|недопустимый вариант, используемый по умолчанию|
|[Ошибка компилятора C2048](compiler-error-c2048.md)|несколько вариантов, используемых по умолчанию|
|C2049 ошибки компилятора|"*идентификатор*": не встроенное пространство имен нельзя открыть повторно как встроенное|
|[Ошибка компилятора C2050](compiler-error-c2050.md)|switch-выражения не является целым|
|[Ошибка компилятора C2051](compiler-error-c2051.md)|Выражение CASE не является константой|
|[Ошибка компилятора C2052](compiler-error-c2052.md)|"*типа*": недопустимый тип для выражения case|
|[Ошибка компилятора C2053](compiler-error-c2053.md)|"*идентификатор*": несоответствие двухбайтовых строк|
|[Ошибка компилятора C2054](compiler-error-c2054.md)|Ожидалось "(" Выполнить "*идентификатор*"|
|[Ошибка компилятора C2055](compiler-error-c2055.md)|требуется список формальных параметров, а не список типов|
|[Ошибка компилятора C2056](compiler-error-c2056.md)|Недопустимое выражение|
|[Ошибка компилятора C2057](compiler-error-c2057.md)|требуется константное выражение|
|[Ошибка компилятора C2058](compiler-error-c2058.md)|неполное константное выражение|
|[Ошибка компилятора C2059](compiler-error-c2059.md)|Синтаксическая ошибка: "*маркера*"|
|[Ошибка компилятора C2060](compiler-error-c2060.md)|Синтаксическая ошибка: обнаружен конец файла|
|[Ошибка компилятора C2061](compiler-error-c2061.md)|Синтаксическая ошибка: идентификатор "*идентификатор*"|
|[Ошибка компилятора C2062](compiler-error-c2062.md)|Тип "*типа*" Непредвиденная|
|[Ошибка компилятора C2063](compiler-error-c2063.md)|"*идентификатор*": не является функцией|
|[Ошибка компилятора C2064](compiler-error-c2064.md)|результатом вычисления фрагмента ведения функция *номер* аргументов|
|[Ошибка компилятора C2065](compiler-error-c2065.md)|"*идентификатор*": необъявленный идентификатор|
|[Ошибка компилятора C2066](compiler-error-c2066.md)|Недопустимое приведение к типу функции|
|[Ошибка компилятора C2067](compiler-error-c2067.md)|недопустимое приведение к типу массива|
|C2068 ошибки компилятора|Недопустимое использование перегруженной функции. Отсутствует список аргументов?|
|[Ошибка компилятора C2069](compiler-error-c2069.md)|приведение типа с "void" к типу без "void"|
|[Ошибка компилятора C2070](compiler-error-c2070.md)|"*типа*": недопустимый оператор sizeof|
|[Ошибка компилятора C2071](compiler-error-c2071.md)|"*идентификатор*": недопустимый класс хранения|
|[Ошибка компилятора C2072](compiler-error-c2072.md)|"*идентификатор*": инициализация функции|
|[Ошибка компилятора C2073](compiler-error-c2073.md)|"*идентификатор*": элементы частично инициализированного массива должны иметь конструктор по умолчанию|
|[Ошибка компилятора C2074](compiler-error-c2074.md)|"*идентификатор*": "*типа*" инициализации требуется список инициализаторов, заключенный в скобки|
|[Ошибка компилятора C2075](compiler-error-c2075.md)|"*идентификатор*": для инициализации массива требуется список инициализаторов, заключенный в скобки|
|C2076 ошибки компилятора|Список инициализаторов, заключенный в скобки, не может использоваться в выражении new, тип которого содержит "*типа*"|
|[Ошибка компилятора C2077](compiler-error-c2077.md)|инициализатор поля нескалярные "*идентификатор*"|
|[Ошибка компилятора C2078](compiler-error-c2078.md)|слишком много инициализаторов|
|[Ошибка компилятора C2079](compiler-error-c2079.md)|"*идентификатор*«использует неопределенный структуры, класса или объединения»*типа*"|
|C2080 ошибки компилятора|"*идентификатор*": тип для "*типа*" можно вывести только из выражения с одним инициализатором|
|[Ошибка компилятора C2081](compiler-error-c2081.md)|"*идентификатор*": имя в недопустимый список формальных параметров|
|[Ошибка компилятора C2082](compiler-error-c2082.md)|переопределение формального параметра "*идентификатор*"|
|[Ошибка компилятора C2083](compiler-error-c2083.md)|Недопустимое сравнение структуры или объединения|
|[Ошибка компилятора C2084](compiler-error-c2084.md)|функция "*идентификатор*" уже имеет тело|
|[Ошибка компилятора C2085](compiler-error-c2085.md)|"*идентификатор*": нет в списке формальных параметров|
|[Ошибка компилятора C2086](compiler-error-c2086.md)|"*идентификатор*": переопределение|
|[Ошибка компилятора C2087](compiler-error-c2087.md)|"*идентификатор*": отсутствует индекс|
|[Ошибка компилятора C2088](compiler-error-c2088.md)|"*оператор*": недопустимый для структуры, класса или объединения|
|[Ошибка компилятора C2089](compiler-error-c2089.md)|"*идентификатор*": "*типа*" слишком велик|
|[Ошибка компилятора C2090](compiler-error-c2090.md)|функция возвращает массив|
|[Ошибка компилятора C2091](compiler-error-c2091.md)|функция возвращает функцию|
|[Ошибка компилятора C2092](compiler-error-c2092.md)|"*идентификатор*" тип элемента массива не может быть функцией|
|[Ошибка компилятора C2093](compiler-error-c2093.md)|"*идентификатор1*": не удается инициализировать с помощью адреса автоматической переменной "*идентификатор2*"|
|[Ошибка компилятора C2094](compiler-error-c2094.md)|Метка "*идентификатор*" не был определен|
|[Ошибка компилятора C2095](compiler-error-c2095.md)|"*функция*": фактический параметр имеет тип «void»: параметр *номер*|
|C2096 ошибки компилятора|"*идентификатор*": не удается инициализировать член данных с помощью инициализатора в скобках|
|[Ошибка компилятора C2097](compiler-error-c2097.md)|Недопустимая инициализация|
|C2098 ошибки компилятора|Непредвиденная лексема после элемента данных "*идентификатор*"|
|[Ошибка компилятора C2099](compiler-error-c2099.md)|инициализатор не является константой|
