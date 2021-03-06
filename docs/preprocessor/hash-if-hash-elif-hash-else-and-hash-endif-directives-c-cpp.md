---
title: "#Если #elif, #else и #endif (C/C++) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- '#else'
- '#endif'
- '#if'
- '#elif'
- defined
- __has_include
dev_langs: C++
helpviewer_keywords:
- '#elif directive'
- conditional compilation, directives
- endif directive (#endif)
- preprocessor, directives
- '#else directive'
- '#endif directive'
- if directive (#if)
- else directive (#else)
- '#if directive'
- elif directive (#elif)
- defined directive
ms.assetid: c77a175f-6ca8-47d4-8df9-7bac5943d01b
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8acd8444295175e6aa9fe329e7851456fcd5f7c4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="if-elif-else-and-endif-directives-cc"></a>Директивы #if, #elif, #else и #endif (C/C++)
Директива `#if` вместе с директивами `#elif`, `#else` и `#endif` управляет компиляцией частей исходного файла. Если указанное выражение (после `#if`) имеет ненулевое значение, в записи преобразования сохраняется группа строк, следующая сразу за директивой `#if`.  
  
## <a name="grammar"></a>Грамматика  
 *Условное* :  
 *IF часть elif части*необ*else часть*необ*endif строка*  
  
 *IF часть* :  
 *текст строки If*  
  
 *Если строка* :  
 **#if***константное выражение*   
  
 **#ifdef***идентификатор*   
  
 **#ifndef***идентификатор*   
  
 *elif части* :  
 *текст elif строки*  
  
 *elif части elif строки текста*  
  
 *elif строки* :  
 **#elif***константное выражение*   
  
 *Else часть* :  
 *текст строки else*  
  
 *строки Else* :  
 `#else`  
  
 *ENDIF строка* :  
 `#endif`  
  
 У каждой директивы `#if` в исходном файле должна быть соответствующая закрывающая директива `#endif`. Между директивами `#elif` и `#if` может располагаться любое количество директив `#endif`, однако допускается не более одной директивы `#else`. Директива `#else`, если присутствует, должна быть последней перед директивой `#endif`.  
  
 Директивы `#if`, `#elif`, `#else` и `#endif` могут быть вложены в другие текстовые части директив `#if`. Каждая вложенная директива `#else`, `#elif` или `#endif` относится к ближайшей предшествующей директиве `#if`.  
  
 Всех директив условной компиляции, таких как `#if` и **#ifdef**, должны быть соответствующие закрывающие `#endif` директивы до конца файла; в противном случае выдается сообщение об ошибке. Если директивы условной компиляции содержатся во включаемых файлах, они должны удовлетворять одинаковым условиям: в конце включаемого файла не должно оставаться непарных директив условной компиляции.  
  
 Внутри той части командной строки, которая следует за выполняется подстановка макросов `#elif` команду, чтобы можно было использовать на вызов макроса в *константное выражение*.  
  
 Препроцессор выбирает одно из заданных вхождений параметра *текст* для дальнейшей обработки. Блок, указанный в *текст* может представлять собой любую последовательность текста. Он может занимать несколько строк. Обычно *текст* — это текст, понятный для компилятора или препроцессора.  
  
 Препроцессор обрабатывает выделенный *текст* и передает его в компилятор. Если *текст* содержит директивы препроцессора, препроцессор выполняет эти директивы. Компилируются только текстовые блоки, выбранные препроцессором.  
  
 Препроцессор выбирает один *текст* элемента, оценивая константные выражения, следующие за каждой `#if` или `#elif` директивы, пока не найдет true (ненулевое) константное выражение. Выделяется весь текст (включая другие директивы препроцессора, начиная с версии  **#** ) до соответствующей `#elif`, `#else`, или `#endif`.  
  
 Если все вхождения *константное выражение* имеют значение false, или если ни один `#elif` отображается директивы, препроцессор выбирает блок текста после `#else` предложения. Если `#else` предложение опущено и все экземпляры *константное выражение* в `#if` блок имеют значение false, выбран ни один текстовый блок.  
  
 *Константное выражение* целочисленное константное выражение со следующими дополнительными ограничениями:  
  
-   Выражения должны иметь целочисленный тип и могут содержать только целочисленные константы, символьные константы и **определенные** оператор.  
  
-   В выражении не допускается использование оператора `sizeof` или оператора приведения типа.  
  
-   Целевая среда может быть не в состоянии представлять все диапазоны целых чисел.  
  
-   Преобразование представляет тип `int` совпадает с типом **длинные**, и `unsigned int` таким же, как `unsigned long`.  
  
-   Транслятор может преобразовывать символьные константы в набор кодовых значений, отличающийся от набора для целевой среды. Для определения свойств целевой среды проверьте значения макросов из файла LIMITS.H в приложении, собранном для целевой среды.  
  
-   Выражение не должно выполнять никаких запросов среды и не должно зависеть от конкретной реализации на целевом компьютере.  

## <a name="defined"></a>определенный  
 Оператор препроцессора **определенные** можно использовать в специальных константных выражениях, как показано в следующем синтаксисе:  
  
 defined( `identifier` )  
  
 defined `identifier`  
  
 Это константное выражение считается равным true (ненулевое), если *идентификатор* в настоящее время установлен; в противном случае условие равно false (0). Идентификатор, определенный как пустой текст, считается определенным. **Определенные** директива может использоваться в `#if` и `#elif` директива, но нигде больше.  
  
 В следующем примере директивы `#if` и `#endif` управляют компиляцией вызова одной из 3 функций:  
  
```  
#if defined(CREDIT)  
    credit();  
#elif defined(DEBIT)  
    debit();  
#else  
    printerror();  
#endif  
```  
  
 Вызов функции `credit` компилируется, если определен идентификатор `CREDIT`. Если определен идентификатор `DEBIT`, компилируется вызов функции `debit`. Если ни один из этих идентификаторов не определен, компилируется вызов функции `printerror`. Обратите внимание, что в C и C++ идентификаторы `CREDIT` и `credit` — это разные идентификаторы из-за различного регистра символов.  
  
 В следующем примере в операторах условной компиляции используется ранее определенная символьная константа с именем `DLEVEL`.  
  
```  
#if DLEVEL > 5  
    #define SIGNAL  1  
    #if STACKUSE == 1  
        #define STACK   200  
    #else  
        #define STACK   100  
    #endif  
#else  
    #define SIGNAL  0  
    #if STACKUSE == 1  
        #define STACK   100  
    #else  
        #define STACK   50  
    #endif  
#endif  
#if DLEVEL == 0  
    #define STACK 0  
#elif DLEVEL == 1  
    #define STACK 100  
#elif DLEVEL > 5  
    display( debugptr );  
#else  
    #define STACK 200  
#endif  
```  
  
 Первый блок `#if` содержит 2 набора вложенных директив `#if`, `#else` и `#endif`. Первый набор директив обрабатывается только в том случае, если выполняется условие `DLEVEL > 5`. В противном случае инструкции после #**else** обрабатываются.  
  
 Директивы `#elif` и `#else` во втором примере используются для выбора одного из четырех вариантов в зависимости от значения константы `DLEVEL`. Константе `STACK` присваивается значение 0, 100 или 200 в зависимости от определения константы `DLEVEL`. Если `DLEVEL` больше 5, то компилируется оператор  
  
```  
#elif DLEVEL > 5  
display(debugptr);  
```  
  
 и константа `STACK` остается неопределенной.  
  
 Условная компиляция обычно используется для предотвращения нескольких включений одного и того же файла заголовка. В языке C++, в котором классы часто определяются в файлах заголовков, конструкции, подобные приведенным ниже, можно использовать для исключения многократных определений.  
  
```  
/*  EXAMPLE.H - Example header file  */  
#if !defined( EXAMPLE_H )  
#define EXAMPLE_H  
  
class Example  
{  
...  
};  
  
#endif // !defined( EXAMPLE_H )  
```  
  
 Предыдущий код проверяет, определена ли символьная константа `EXAMPLE_H`. Если определена, файл уже включен и его повторная обработка не требуется. Если нет, константа `EXAMPLE_H` определяется, чтобы пометить файл EXAMPLE.H как уже обработанный.  

## <a name="hasinclude"></a>__has_include
**Visual Studio 2017 г 15,3 и более поздних версий**: Определяет, доступен ли заголовок библиотеки для включения:  

```cpp
#ifdef __has_include
#  if __has_include(<filesystem>)
#    include <filesystem>
#    define have_filesystem 1
#  elif __has_include(<experimental/filesystem>)
#    include <experimental/filesystem>
#    define have_filesystem 1
#    define experimental_filesystem
#  else
#    define have_filesystem 0
#  endif
#endif
```
  
## <a name="see-also"></a>См. также  
 [Директивы препроцессора](../preprocessor/preprocessor-directives.md)