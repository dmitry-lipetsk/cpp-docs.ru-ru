---
title: "Стандартные преобразования | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- standard conversions, categories of
- L-values [C++]
- conversions, standard
ms.assetid: ce7ac8d3-5c99-4674-8229-0672de05528d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 324fa54362098e2b7ffae6fdf368bf590846f9c1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="standard-conversions"></a>Стандартные преобразования
В языке C++ определены преобразования между его основными типами. Также определяются преобразования для указателей, ссылочных типов и типов указателей на члены. Эти преобразования называются "стандартными преобразованиями". (Дополнительные сведения о типах, стандартные типы и производные типы см. в разделе [типов](http://msdn.microsoft.com/en-us/6882ee83-ea32-4373-8d57-c3efbbc15af0).)  
  
 В этом разделе рассматриваются следующие стандартные преобразования:  
  
-   Восходящие приведения целочисленных типов  
  
-   Преобразования целочисленных типов  
  
-   Преобразования типов с плавающей запятой  
  
-   Преобразования типов с плавающей запятой и целочисленных типов  
  
-   Арифметические преобразования  
  
-   Преобразования указателей  
  
-   Преобразования ссылок  
  
-   Преобразования указателей на члены  
  
    > [!NOTE]
    >  Пользовательские типы могут определять собственные преобразования. Преобразование определяемых пользователем типов, описанные в [конструкторы](../cpp/constructors-cpp.md) и [преобразования](../cpp/user-defined-type-conversions-cpp.md).  
  
 Следующий код вызывает преобразования (в данном примере это восходящее приведение целочисленных типов).  
  
```  
long  long_num1, long_num2;  
int   int_num;  
  
// int_num promoted to type long prior to assignment.  
long_num1 = int_num;  
  
// int_num promoted to type long prior to multiplication.  
long_num2 = int_num * long_num2;  
```  
  
 Результат преобразования является L-значением только в том случае, если получается ссылочный тип. Например, определенное пользователем преобразование объявлен как `operator int&()` возвращает ссылку и является l значением. Однако преобразование, объявленное как `operator int()`возвращает объект и не является l значением.  
  
## <a name="integral-promotions"></a>Восходящие приведения целочисленных типов  
 Объекты целочисленного типа можно преобразовать в другой более широкий целочисленный тип (то есть тип, который может представлять более широкий набор значений). Этот расширенный тип преобразования называется восходящим приведением целого типа. Благодаря восходящему приведению целого типа в выражении, в котором можно использовать другой целочисленный тип, можно использовать следующие элементы.  
  
-   Объекты, литералы и константы типа `char` и `short int`.  
  
-   Типы перечисления.  
  
-   Битовые поля `int`.  
  
-   Перечислители  
  
 Во время повышения в C ++ значения сохраняются. То есть гарантируется, что значение после повышения будет таким же, как до него. Во время повышения с сохранением значений объекты более коротких целочисленных типов (например, битовые поля или объекты типа `char`) повышаются до типа `int`, если `int` может представить полный диапазон исходного типа. Если `int` не может представить полный диапазон значений, объект повышается до типа `unsigned int`. Хотя эта стратегия такая же, как в ANSI C, во время повышения с сохранением значений не сохраняется наличие знака у объекта.  
  
 Обычно при повышениях с сохранением значения и повышениях с сохранением наличия знака выдаются одинаковые результаты. Однако результаты могут отличаться, если повышенный объект является одним из следующих элементов.  
  
-   Операнд  **/** , `%`, `/=`, `%=`,  **<** ,  **\< =** ,  **>** , или**>=**  
  
     Эти операторы зависят от знака для определения результата. Поэтому, если используются эти операнды, при повышениях с сохранением значения и повышениях с сохранением наличия знака выдаются разные результаты.  
  
-   Левый операнд  **>>**  или**>>=**  
  
     Эти операторы обрабатывают количества со знаком и без знака по-разному при выполнении операции сдвига. В случае количеств со знаком сдвиг вправо приводит к перемещению знакового бита в освобожденные позиции битов. В случае количеств без знака освобожденные позиции битов заполняются нулями.  
  
-   Аргумент перегруженной функции или операнд перегруженного оператора, который зависит от наличия знака у типа данного операнда для сопоставления аргумента. (См. [перегруженные операторы](../cpp/operator-overloading.md) Дополнительные сведения об определении перегруженных операторов.)  
  
## <a name="integral-conversions"></a>Преобразования целочисленных типов  
 Целочисленные преобразования выполняются между целочисленными типами. Целочисленные типы имеют `char`, `int`, и **длинные** (и **короткие**, **подписан**, и `unsigned` версий этих типов).  
  
 **Подписи в числа без знака**  
  
 Объекты целочисленных типов со знаком можно преобразовывать в соответствующие типы без знака. При выполнении таких преобразований фактический битовый шаблон не изменяется; однако интерпретация данных изменяется. Рассмотрим этот код:  
  
```  
  
#include <iostream>  
  
using namespace std;  
int main()  
{  
    short  i = -3;  
    unsigned short u;  
  
    cout << (u = i) << "\n";  
}  
// Output: 65533  
  
```  
  
 В приведенном выше примере `signed short`, `i` определяется и инициализируется с отрицательным значением. Выражение `(u = i)` вызывает `i` должно быть преобразовано в **short без знака** до присваивания значения `u`.  
  
 **Без знака со знаком**  
  
 Объекты целочисленных типов без знака можно преобразовывать в соответствующие типы со знаком. Однако такое преобразование может приводить к неправильной интерпретации данных, если значение объекта без знака находится вне диапазона, представимого типом со знаком, как показано в следующем примере.  
  
```  
  
#include <iostream>  
  
using namespace std;  
int main()  
{  
 short  i;  
 unsigned short u = 65533;  
  
 cout << (i = u) << "\n";  
}  
//Output: -3  
```  
  
 В приведенном выше примере `u` — `unsigned` **короткие** целый объект, который необходимо преобразовать в количественное значение со знаком для вычисления выражения `(i = u)`. Поскольку его значение невозможно правильно представить в виде `signed short`, данные интерпретируются неверно.  
  
## <a name="floating-point-conversions"></a>Преобразование чисел с плавающей запятой  
 Объект типа с плавающей запятой можно безопасно преобразовать в более точный тип с плавающей запятой, то есть без потери значимости. Например, преобразования из **float** для **двойные** или из **двойные** для `long double` являются безопасно и значение не изменяется.  
  
 Объект типа с плавающей запятой также можно преобразовать в менее точный тип, если он находится в диапазоне, который может быть представлен этим типом. (См. [пределы с плавающей запятой](../cpp/floating-limits.md) диапазоны типов с плавающей запятой.) Если исходное значение невозможно представить точно, его можно преобразовать в следующее более высокое или низкое значение, которое может быть представлено. Если такого значения не существует, результат не определен. Рассмотрим следующий пример.  
  
```  
cout << (float)1E300 << endl;  
```  
  
 Максимальное значение может быть представлен по типу **float** — 3.402823466E38 — гораздо меньше, чем 1E300. Поэтому число преобразуется в бесконечность, а результат имеет вид 1,#INF.  
  
## <a name="conversions-between-integral-and-floating-point-types"></a>Преобразования между целочисленным типом и типом с плавающей запятой  
 Определенные выражения могут вызывать преобразование объектов плавающего типа в целочисленные типы, и наоборот. Если объект целочисленного типа преобразуется в тип с плавающей запятой и исходное значение невозможно представить точно, результатом будет следующее более высокое или следующее более низкое представимое значение.  
  
 При преобразовании объекта типа с плавающей запятой в целочисленный тип дробная часть усечена. Округление в процессе преобразования не происходит. Усечение означает, что число вроде 1,3 преобразуется в 1, а-1.3 преобразуется в значение -1.  
  
## <a name="arithmetic-conversions"></a>Арифметические преобразования  
 Многие бинарные операторы (описано в [выражения с бинарными операторами](../cpp/expressions-with-binary-operators.md)) приводят к преобразованиям операндов и выдают результаты таким же образом. Способ, посредством которого эти операторы вызывают преобразования, называется обычными арифметическими преобразованиями. Арифметические преобразования операндов различных собственных типов выполняются согласно описанию в следующей таблице. Типы typedef ведут себя в соответствии со своими базовыми собственными типами.  
  
### <a name="conditions-for-type-conversion"></a>Условия для преобразования типов  
  
|Выполненные условия|Преобразование|  
|--------------------|----------------|  
|Один из операндов имеет тип **long double**.|Другой операнд преобразуется в тип **long double**.|  
|Предыдущее условие не выполнено и один из операндов имеет тип **двойные**.|Другой операнд преобразуется в тип **двойные**.|  
|Предыдущие условия не выполнены и один из операндов имеет тип **float**.|Другой операнд преобразуется в тип **float**.|  
|Предыдущие условия не выполнены (ни один из операндов не является операндом с плавающей запятой).|Для операндов выполняются восходящие приведения целого типа следующим образом.<br /><br /> -Если один из операндов имеет тип `unsigned` **длинные**, то другой операнд преобразуется в тип `unsigned long`.<br />-Если предыдущее условие не выполнено и один из операндов имеет тип **длинные** и другой — тип `unsigned` `int`, оба операнда преобразуются в тип `unsigned long`.<br />-Если два предыдущих условия не выполняются, а если один из операндов имеет тип **длинные**, то другой операнд преобразуется в тип **длинные**.<br />-Если три предыдущих условия не выполняются, а если один из операндов имеет тип `unsigned int`, то другой операнд преобразуется в тип `unsigned int`.<br />— Если ни одно из предыдущих условий не выполнено, оба операнда преобразуются в тип `int`.|  
  
 В следующем коде демонстрируются правила преобразования, описанные в таблице.  
  
```  
  
double dVal;  
float fVal;  
int iVal;  
unsigned long ulVal;  
  
int main() {  
   // iVal converted to unsigned long  
   // result of multiplication converted to double  
   dVal = iVal * ulVal;  
  
   // ulVal converted to float  
   // result of addition converted to double  
   dVal = ulVal + fVal;  
}  
```  
  
 Первый оператор в приведенном выше примере представляет умножение двух целочисленных типов, `iVal` и `ulVal`. Условие выполнено, т. е. ни один из операндов не является операндом типа с плавающей запятой и один операнд имеет тип `unsigned int`. Следовательно, другой операнд, `iVal`, преобразуется в тип `unsigned int`. Результат присваивается переменной `dVal`. Условие выполнено — один из операндов имеет тип **двойные**, поэтому `unsigned int` результат умножения преобразуется в тип **двойные**.  
  
 Второй оператор в предыдущем примере показано добавление **float** и целочисленный тип, `fVal` и `ulVal`. `ulVal` Переменной преобразуется в тип **float** (третье условие в таблице). Результат сложения преобразуется в тип **двойные** (второе условие в таблице) и назначены `dVal`.  
  
## <a name="pointer-conversions"></a>Преобразования указателей  
 Указатели можно преобразовывать в ходе присваивания, инициализации, сравнения и выполнения других выражений.  
  
### <a name="pointer-to-classes"></a>Указатель на классы  
 Указатель на класс можно преобразовать в указатель на базовый класс в двух случаях.  
  
 Во-первых, когда указанный базовый класс доступен и преобразование однозначно. (См. [несколько базовых классов](../cpp/multiple-base-classes.md) Дополнительные сведения о неоднозначных ссылок базового класса.)  
  
 Доступность базового класса зависит от используемого типа наследования. Рассмотрим пример наследования на следующем рисунке.  
  
 ![Базовый отображение граф наследования &#45; доступность класса](../cpp/media/vc38xa1.gif "vc38XA1")  
Граф наследования, демонстрирующий доступность базового класса  
  
 В следующей таблице показана доступность базового класса для ситуации, представленной на рисунке.  
  
### <a name="base-class-accessibility"></a>Доступность базового класса  
  
|Тип функции|Наследование|Допустимо ли преобразование из<br /><br /> B * в A\* юридических?|  
|----------------------|----------------|-------------------------------------------|  
|Внешняя функция (без области видимости класса)|Private|Нет|  
||Защищенный|Нет|  
||Public|Да|  
|Функция-член B (в области B)|Private|Да|  
||Защищенный|Да|  
||Открытый|Да|  
|Функция-член C (в области C)|Private|Нет|  
||Защищенный|Да|  
||Открытый|Да|  
  
 Во-вторых, указатель на класс можно преобразовать в указатель на базовый класс при использовании явного преобразования типов. (См. [выражения с явными преобразованиями типов](http://msdn.microsoft.com/en-us/060ad6b4-9592-4f3e-8509-a20ac84a85ae) Дополнительные сведения о явных преобразованиях типов.)  
  
 Результатом такого преобразования является указатель на подчиненный объект — часть объекта, полностью описанная базовым классом.  
  
 В следующем примере кода определяется два класса: `A` и `B`, где `B` является производным от класса `A`. (Дополнительные сведения о наследовании см. в разделе [классы, производные от](../cpp/inheritance-cpp.md).) Затем он определяет `bObject`, объект типа `B` и два указателя (`pA` и `pB`), которые указывают на объект.  
  
```  
// C2039 expected  
class A  
{  
public:  
    int AComponent;  
    int AMemberFunc();  
};  
  
class B : public A  
{  
public:  
    int BComponent;  
    int BMemberFunc();  
};  
int main()  
{  
   B bObject;  
   A *pA = &bObject;  
   B *pB = &bObject;  
  
   pA->AMemberFunc();   // OK in class A  
   pB->AMemberFunc();   // OK: inherited from class A  
   pA->BMemberFunc();   // Error: not in class A  
}  
```  
  
 Указатель `pA` принадлежит типу `A *`, и это можно интерпретировать следующим образом: "указатель на объект типа `A`". Члены `bObject` `(`например `BComponent` и `BMemberFunc`) являются уникальными для типа `B` и, следовательно, недоступны через `pA`. Указатель `pA` предоставляет доступ только к тем характеристикам (функциям-членам и данным) объекта, которые определены в классе `A`.  
  
### <a name="pointer-to-function"></a>Указатель на функцию  
 Указатель на функцию можно преобразовать в тип **void \*** , если тип **void \***  достаточно велик для хранения этого указателя.  
  
### <a name="pointer-to-void"></a>Указатель на void  
 Указатели на тип `void` можно преобразовать в указатели на любой другой тип, но только с использованием явного приведения типа (в отличие от C). (См. [выражения с явными преобразованиями типов](http://msdn.microsoft.com/en-us/060ad6b4-9592-4f3e-8509-a20ac84a85ae) Дополнительные сведения о приведении типов.) Указатель на любой тип может быть неявно преобразован в указатель на тип `void`. Указатель на неполный объект типа можно преобразовать в указатель на `void` (неявно) и назад (явно). Результат такого преобразования равен значению исходного указателя. Объект считается неполным, если он объявлен, но имеется недостаточно сведений для определения его размера или базового класса.  
  
 Указатель на любой объект, который не является **const** или `volatile` может быть неявно преобразован в указатель типа **void \*** .  
  
### <a name="const-and-volatile-pointers"></a>Указатели с ключевыми словами const и volatile  
 C++ не предоставляет стандартного преобразования из **const** или `volatile` в тип, который не **const** или `volatile`. Однако можно указать любое преобразование с помощью явного приведения типов (включая небезопасные преобразования).  
  
> [!NOTE]
>  Указатели C++ на члены, за исключением указателей на статические члены, отличаются от обычных указателей и не имеют таких же стандартных преобразований. Указатели на статические члены являются обычными, и для них имеются такие же преобразования, как и для обычных указателей.   
  
### <a name="null-pointer-conversions"></a>Преобразование пустых (null) указателей  
 Константное целочисленное выражение, результатом которого является ноль, либо такое выражение, приведенное к типу указателя, преобразуется в указатель, который называется "пустой указатель". Такой указатель гарантированно не равен указателю на любой действительный объект или функцию (кроме указателей на базовые объекты, которые могут иметь одинаковое смещение, но при этом указывать на разные объекты).  
  
 В C ++ 11 [nullptr](../cpp/nullptr.md) тип должен быть предпочтительным в стиле C пустой указатель.  
  
### <a name="pointer-expression-conversions"></a>Преобразование выражений указателей  
 Любое выражение с типом массива можно преобразовать в указатель того же типа. Результатом преобразования будет указатель на первый элемент массива. В следующем примере показано такое преобразование.  
  
```  
char szPath[_MAX_PATH]; // Array of type char.  
char *pszPath = szPath; // Equals &szPath[0].  
```  
  
 Выражение, которое приводит к функции, возвращающей определенный тип, преобразуется в указатель на функцию, возвращающую этот тип, за исключением случая, когда:  
  
-   Выражение используется в качестве операнда для оператора взятия адреса (**&**).  
  
-   выражение используется в качестве операнда для оператора вызова функции.  
  
## <a name="reference-conversions"></a>Преобразования ссылок  
 Ссылку на класс можно преобразовать в ссылку на базовый класс в следующих случаях.  
  
-   Указанный базовый класс доступен.  
  
-   Преобразование является однозначным. (См. [несколько базовых классов](../cpp/multiple-base-classes.md) Дополнительные сведения о неоднозначных ссылок базового класса.)  
  
 Результат преобразования — это указатель на вложенный объект, представляющий базовый класс.  
  
## <a name="pointer-to-member"></a>Указатель на член  
 Указатели на члены класса можно преобразовать в ходе присвоения, инициализации, сравнения и выполнения других выражений. В этом разделе описаны следующие преобразования указателей в члены.  
  
## <a name="pointer-to-base-class-member"></a>Указатель на член базового класса  
 Указатель на член базового класса можно преобразовать в указатель на член производного от него класса при выполнении следующих условий:  
  
-   доступно обратное преобразование из указателя на производный класс в указатель базового класса;  
  
-   производный класс не наследуется виртуально от базового класса.  
  
 Если левый операнд является указателем на член, правый операнд должен иметь тип указателя на член или являться константным выражением со значением 0. Такое присваивание допустимо только в следующих случаях:  
  
-   правый операнд является указателем на член того же класса, что и левый операнд;  
  
-   левый операнд является указателем на член класса, открыто и однозначно производного от класса правого операнда.  
  
## <a name="integral-constant-conversions"></a>Преобразование целочисленных констант  
 Целочисленное константное выражение, равное нулю, преобразуется в указатель, который называется "пустым указателем". Такой указатель гарантированно не равен указателю на любой действительный объект или функцию (кроме указателей на базовые объекты, которые могут иметь одинаковое смещение, но при этом указывать на разные объекты).  
  
 В следующем примере кода демонстрируется определение указателя на член `i` в классе `A`. Указатель `pai` инициализируется со значением 0 и становится пустым указателем.  
  
```  
class A  
{  
public:  
 int i;  
};  
  
int A::*pai = 0;  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку C++](../cpp/cpp-language-reference.md)