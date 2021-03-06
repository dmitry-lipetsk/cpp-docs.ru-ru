---
title: "Предупреждение (уровень 4) C4471 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 04/24/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4471
dev_langs: C++
helpviewer_keywords: C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5e7429a458c90c30fdf57b985cda88ca85c6d29c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4471"></a>Компилятор C4471 предупреждение (уровень 4)
"*перечисления*": у прямого объявления неограниченного перечисления должен иметь базовый тип (предполагается int.)  
  
У прямого объявления неограниченного перечисления обнаружен без спецификатора для базового типа. По умолчанию Visual C++ предполагает `int` является базовым типом для перечисления. Это может вызвать проблемы, если другой тип используется в определении перечисления, например, если указан другой явный тип, или другой тип неявно устанавливается с помощью инициализатора. Также могут возникнуть проблемы переносимости; Другие компиляторы не следует считать `int` является базовым типом перечисления.  
  
Это предупреждение отключено по умолчанию. можно использовать/Wall или /w*N*4471, чтобы включить его в командной строке, или используйте #pragma [предупреждение](../../preprocessor/warning.md) в файле исходного кода.  
  
В некоторых случаях это предупреждение является случайной. Если после определения опережающего объявления перечисления, это предупреждение может активироваться. Например этот код является допустимым, несмотря на то, что может привести к C4471:  
  
```cpp  
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```  
  
## <a name="example"></a>Пример  
Как правило можно безопасно использовать полное определение для вместо прямого объявления неограниченного перечисления. Можно поместить определение в файле заголовка и включить его в исходных файлах, которые ссылаются на него. Это работает в код, написанный для С ++ 98 и более поздних версий. Мы рекомендуем это решение для обеспечения переносимости и простоту обслуживания.  
  
```cpp  
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```  
  
## <a name="example"></a>Пример  
В C ++ 11 можно добавить явный тип для неограниченного перечисления и его опережающего объявления. Это решение рекомендуется только в том случае, если логика включения сложных заголовок запрещено использование определение вместо опережающего объявления. Это решение может привести к проблема обслуживания: Если изменить базовый тип, который используется для определения перечисления, необходимо также изменить все декларации вперед в соответствии или возможны автоматической ошибки в коде. Вы можете поместить опережающего объявления в файле заголовка, чтобы свести к минимуму эту проблему.  
  
```cpp  
// C4471c.cpp
// Client code for enumeration defined in C4471d.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example;    // C4471, int assumed
// To fix, replace the lines above with the forward declarations:
// enum Example : unsigned;
// ...
```  
  
```cpp  
// C4471d.cpp
// Definition for enumeration used in C4471c.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example : unsigned { item = 0x80000000 }; // explicit type
// ...
```  
  
Если указать явный тип перечисления, рекомендуется также включить предупреждение [C4369](compiler-warning-level-1-C4369.md), который включен по умолчанию. Это определяется случаев, в которых требует элемента перечисления, тип которого отличается от явно указанного типа.
  
## <a name="example"></a>Пример  
Можно изменить код, чтобы использовать перечисление с областью видимости, что новые возможности C ++ 11. Определение и код клиента, использующий тип перечисления, который необходимо изменить для использования перечисление с ограниченной областью. Мы рекомендуем использовать перечисление с областью видимости при возникновении проблем с загрязнение пространства имен, как имена элементов определенное перечисление ограничены области перечисления. Еще одна возможность перечисление с областью видимости —, его члены нельзя неявно преобразовать в другой целочисленный тип или тип перечисления, которой может быть источником незначительные ошибки.

```cpp  
// C4471e.cpp
// Client code for scoped enumeration defined in C4471f.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum Example;    // C4471
// To fix, replace the line above with the forward declaration:
// enum class Example;
// ...
```  
  
```cpp  
// C4471f.cpp
// Definition for scoped enumeration used in C4471e.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum class Example { item = 0 };
// ...
```  
  
