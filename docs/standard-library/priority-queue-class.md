---
title: "Класс priority_queue | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- queue/std::priority_queue::container_type
- queue/std::priority_queue::size_type
- queue/std::priority_queue::value_type
- queue/std::priority_queue::empty
- queue/std::priority_queue::pop
- queue/std::priority_queue::push
- queue/std::priority_queue::size
- queue/std::priority_queue::top
dev_langs: C++
helpviewer_keywords:
- std::priority_queue [C++], container_type
- std::priority_queue [C++], size_type
- std::priority_queue [C++], value_type
- std::priority_queue [C++], empty
- std::priority_queue [C++], pop
- std::priority_queue [C++], push
- std::priority_queue [C++], size
- std::priority_queue [C++], top
ms.assetid: 69fca9cc-a449-4be4-97b7-02ca5db9cbb2
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2e8768fa138da74761bc581f8b9f54a2fe432776
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="priorityqueue-class"></a>Класс priority_queue
Класс-шаблон адаптера контейнера, который предоставляет ограничение функциональности, ограничивая доступ к верхнему элементу некоторого базового типа контейнера, который всегда является самым большим или имеет высший приоритет. Новые элементы можно добавлять в priority_queue, а верхний элемент priority_queue можно просмотреть или удалить.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
template <class Type, class Container= vector <Type>, class Compare= less <typename Container ::value_type>>  
class priority_queue  
```  
  
#### <a name="parameters"></a>Параметры  
 *Тип*  
 Тип данных элемента для сохранения в priority_queue.  
  
 `Container`  
 Тип базового контейнера, используемый для реализации priority_queue.  
  
 *Compare*  
 Тип, предоставляющий объект-функцию, который может сравнить два значения элементов как ключи сортировки, чтобы определить их относительный порядок в priority_queue. Этот аргумент — необязательный, в качестве значения по умолчанию используется двоичный предикат **less***\<***typename** *Container***::value_type***>*.  
  
## <a name="remarks"></a>Примечания  
 Элементы класса **Type**, заданные в первом параметре-шаблоне объекта очереди, являются синонимами [value_type](#value_type) и должны соответствовать типу элемента в классе базового контейнера **Container**, заданного вторым параметром-шаблоном. Класс **Type** должен быть назначаемым, чтобы можно было копировать объекты этого типа и присваивать значения переменным этого типа.  
  
 Priority_queue упорядочивает последовательность, которой она управляет, путем обращения к сохраненному объекту-функции класса **Traits**. В целом, упорядочиваемые элементы должны лишь подлежать сравнению "меньше чем" для установления такого порядка, чтобы, имея любые два элемента, можно было определить, что они равны (ни один не меньше другого) или что один меньше другого. Это приводит к упорядочению неравнозначных элементов. С более технической точки зрения, функция сравнения является бинарным предикатом, который вызывает строгого слабое упорядочение в стандартном математически смысле.  
  
 Подходящие базовые классы контейнеров для priority_queue включают [класс deque](../standard-library/deque-class.md) и [класс vector](../standard-library/vector-class.md) (класс по умолчанию) или любой другой контейнер последовательности, который поддерживает операции `front`, `push_back` и `pop_back` и итератор произвольного доступа. Класс базового контейнера инкапсулирован в адаптер контейнера, который предоставляет только ограниченный набор функций-членов контейнера последовательностей в виде открытого интерфейса.  
  
 Добавление элементов в `priority_queue` и удаление элементов из него имеют логарифмическую сложность. Доступ к элементам в `priority_queue` имеет постоянную сложность.  
  
 В стандартной библиотеке C++ определено три типа адаптеров контейнера: стек (stack), очередь (queue) и очередь с приоритетом (priority_queue). Каждый ограничивает функциональность некоторого базового класса контейнеров для обеспечения точно управляемого интерфейса к стандартной структуре данных.  
  
-   [Класс стека](../standard-library/stack-class.md) поддерживает структуру данных "последним поступил — первым обслужен" (LIFO). Хороший аналог такого подхода — стопка тарелок. Элементы (тарелки) можно вставлять, проверять или удалять только из верхней части стека, которая является последним элементом в конце базового контейнера. Ограничение на доступ только к верхнему элементу является причиной использования класса стека.  
  
-   [Класс queue](../standard-library/queue-class.md) поддерживает структуру данных "первым поступил — первым обслужен" (FIFO). Хороший аналог такого подхода — очередь из людей к банковскому служащему. Элементы (люди) можно добавлять в конец очереди и удалять из начала очереди. Проверять можно как начало, так и конец очереди. Ограничение на доступ только к переднему и заднему элементам в таком подходе является причиной использования класса очереди.  
  
-   Класс priority_queue упорядочивает элементы, чтобы наибольший элемент всегда находился сверху. Он поддерживает вставку элемента, а также проверку и удаление верхнего элемента. Хороший аналог такого подхода — очередь из людей, упорядоченная по возрасту, росту или любому другому критерию.  
  
### <a name="constructors"></a>Конструкторы  
  
|||  
|-|-|  
|[priority_queue](#priority_queue)|Создает `priority_queue`, который является пустым или копией диапазона объекта базового контейнера или другого `priority_queue`.|  
  
### <a name="typedefs"></a>Определения типов  
  
|||  
|-|-|  
|[container_type](#container_type)|Тип, предоставляющий базовый контейнер для принятия `priority_queue`.|  
|[size_type](#size_type)|Целочисленный Typedef без знака, который может представлять число элементов в `priority_queue`.|  
|[value_type](#value_type)|Тип, представляющий тип объекта, который хранится в виде элемента в `priority_queue`.|  
  
### <a name="member-functions"></a>Функции-члены  
  
|||  
|-|-|  
|[empty](#empty)|Проверяет, является ли `priority_queue` пустым.|  
|[pop](#pop)|Удаляет самый большой элемент `priority_queue` с верхней позиции.|  
|[push](#push)|Добавляет элемент в очередь с приоритетом на основе приоритета элемента из оператора operator<.|  
|[size](#size)|Возвращает количество элементов в контейнере `priority_queue`.|  
|[top](#top)|Возвращает константную ссылку на наибольший элемент в верхней части `priority_queue`.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<queue>  
  
 **Пространство имен:** std  
  
##  <a name="container_type"></a>  priority_queue::container_type  
 Тип, предоставляющий базовый контейнер для изменения.  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>Примечания  
 Этот тип является синонимом для параметра шаблона `Container`. Класс контейнера последовательности `deque` и класс по умолчанию `vector` из стандартной библиотеки С++ соответствуют требованиям для использования в качестве базового контейнера для объекта priority_queue. Также можно использовать пользовательские типы, удовлетворяющие требованиям.  
  
 Дополнительные сведения о `Container` см. в разделе "Примечания" документации к [Класс priority_queue](../standard-library/priority-queue-class.md).  
  
### <a name="example"></a>Пример  
  См. пример для [priority_queue](#priority_queue) с примером объявления и использования `container_type`.  
  
##  <a name="empty"></a>  priority_queue::empty  
 Проверяет, что priority_queue пуста.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 **true**, если очередь пуста; в противном случае **false**.  
  
### <a name="example"></a>Пример  
  
```cpp  
// pqueue_empty.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares priority_queues with default deque base container  
   priority_queue <int> q1, s2;  
  
   q1.push( 1 );  
  
   if ( q1.empty( ) )  
      cout << "The priority_queue q1 is empty." << endl;  
   else  
      cout << "The priority_queue q1 is not empty." << endl;  
  
   if ( s2.empty( ) )  
      cout << "The priority_queue s2 is empty." << endl;  
   else  
      cout << "The priority_queue s2 is not empty." << endl;  
}  
```  
  
```Output  
The priority_queue q1 is not empty.  
The priority_queue s2 is empty.  
```  
  
##  <a name="pop"></a>  priority_queue::pop  
 Удаляет самый большой элемент в priority_queue с верхней позиции.  
  
```  
void pop();
```  
  
### <a name="remarks"></a>Примечания  
 Для применения функции-члена класс priority_queue не должен быть пустым. Вверху priority_queue всегда находится самый большой элемент в контейнере.  
  
### <a name="example"></a>Пример  
  
```cpp  
// pqueue_pop.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   priority_queue <int> q1, s2;  
  
   q1.push( 10 );  
   q1.push( 20 );  
   q1.push( 30 );  
  
   priority_queue <int>::size_type i, iii;  
   i = q1.size( );  
   cout << "The priority_queue length is " << i << "." << endl;  
  
   const int& ii = q1.top( );  
   cout << "The element at the top of the priority_queue is "  
        << ii << "." << endl;  
  
   q1.pop( );  
  
   iii = q1.size( );  
   cout << "After a pop, the priority_queue length is "   
        << iii << "." << endl;  
  
   const int& iv = q1.top( );  
   cout << "After a pop, the element at the top of the "  
        << "priority_queue is " << iv << "." << endl;  
}  
```  
  
```Output  
The priority_queue length is 3.  
The element at the top of the priority_queue is 30.  
After a pop, the priority_queue length is 2.  
After a pop, the element at the top of the priority_queue is 20.  
```  
  
##  <a name="priority_queue"></a>  priority_queue::priority_queue  
 Создает priority_queue, которая пуста или является копией диапазона объекта базового контейнера или другой priority_queue.  
  
```  
priority_queue();

explicit priority_queue(const Traits&_comp);

priority_queue(const Traits&_comp, const container_type& _Cont);

priority_queue(const priority_queue& right);

template <class InputIterator>  
priority_queue(InputIterator first, InputIterator last);

template <class InputIterator>  
priority_queue(InputIterator first, InputIterator last, const Traits&_comp);

template <class InputIterator>  
priority_queue(InputIterator first, InputIterator last, const Traits&_comp, const container_type& _Cont);
```  
  
### <a name="parameters"></a>Параметры  
 *_ comp*  
 Функция сравнения типа **constTraits** для упорядочивания элементов в priority_queue, по умолчанию используется функция сравнения базового контейнера.  
  
 `_Cont`  
 Базовый контейнер, из которого будет копироваться создаваемая priority_queue.  
  
 `right`  
 Priority_queue, для которой создаваемый набор станет копией.  
  
 `first`  
 Положение первого элемента в диапазоне копируемых элементов.  
  
 `last`  
 Положение первого элемента после диапазона копируемых элементов.  
  
### <a name="remarks"></a>Примечания  
 Каждый из первых трех конструкторов определяет пустую исходную priority_queue; второй также указывает тип функции сравнения (`comp`) для использования при установлении порядка элементов, а третий явно указывает `container_type` (`_Cont`) для использования. Ключевое слово **explicit** подавляет некоторые виды автоматического преобразования типов.  
  
 Четвертый конструктор задает копию priority_queue `right`.  
  
 Последние три конструктора копируют диапазон [* первой, последней *) некоторые контейнера и значения можно использовать для инициализации priority_queue с увеличением explicitness при указании типа функции сравнения класса **признаки** и `container_type`.  
  
### <a name="example"></a>Пример  
  
```cpp  
// pqueue_ctor.cpp  
// compile with: /EHsc  
#include <queue>  
#include <vector>  
#include <deque>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // The first member function declares priority_queue  
   // with a default vector base container  
   priority_queue <int> q1;  
   cout << "q1 = ( ";  
   while ( !q1.empty( ) )  
   {  
      cout << q1.top( ) << " ";  
      q1.pop( );  
   }  
   cout << ")" << endl;  
  
   // Explicitly declares a priority_queue with nondefault  
   // deque base container  
   priority_queue <int, deque <int> > q2;  
   q2.push( 5 );  
   q2.push( 15 );  
   q2.push( 10 );  
   cout << "q2 = ( ";  
   while ( !q2.empty( ) )  
   {  
      cout << q2.top( ) << " ";  
      q2.pop( );  
   }  
   cout << ")" << endl;  
  
   // This method of printing out the elements of a priority_queue  
   // removes the elements from the priority queue, leaving it empty  
   cout << "After printing, q2 has " << q2.size( ) << " elements." << endl;  
  
   // The third member function declares a priority_queue   
   // with a vector base container and specifies that the comparison   
   // function greater is to be used for ordering elements  
   priority_queue <int, vector<int>, greater<int> > q3;  
   q3.push( 2 );  
   q3.push( 1 );  
   q3.push( 3 );  
   cout << "q3 = ( ";  
   while ( !q3.empty( ) )  
   {  
      cout << q3.top( ) << " ";  
      q3.pop( );  
   }  
   cout << ")" << endl;  
  
   // The fourth member function declares a priority_queue and  
   // initializes it with elements copied from another container:  
   // first, inserting elements into q1, then copying q1 elements into q4  
   q1.push( 100 );  
   q1.push( 200 );  
   priority_queue <int> q4( q1 );  
   cout << "q4 = ( ";     
   while ( !q4.empty( ) )  
   {  
      cout << q4.top( ) << " ";  
      q4.pop( );  
   }  
   cout << ")" << endl;  
  
   // Creates an auxiliary vector object v5 to be used to initialize q5  
   vector <int> v5;  
   vector <int>::iterator v5_Iter;  
   v5.push_back( 10 );  
   v5.push_back( 30 );  
   v5.push_back( 20 );  
   cout << "v5 = ( " ;  
   for ( v5_Iter = v5.begin( ) ; v5_Iter != v5.end( ) ; v5_Iter++ )  
      cout << *v5_Iter << " ";  
   cout << ")" << endl;  
  
   // The fifth member function declares and  
   // initializes a priority_queue q5 by copying the  
   // range v5[ first,  last) from vector v5  
   priority_queue <int> q5( v5.begin( ), v5.begin( ) + 2 );  
   cout << "q5 = ( ";  
   while ( !q5.empty( ) )  
   {  
      cout << q5.top( ) << " ";  
      q5.pop( );  
   }  
   cout << ")" << endl;  
  
   // The sixth member function declares a priority_queue q6  
   // with a comparison function greater and initializes q6  
   // by copying the range v5[ first,  last) from vector v5  
   priority_queue <int, vector<int>, greater<int> >   
      q6( v5.begin( ), v5.begin( ) + 2 );  
   cout << "q6 = ( ";  
   while ( !q6.empty( ) )  
   {  
      cout << q6.top( ) << " ";  
      q6.pop( );  
   }  
   cout << ")" << endl;  
}  
```  
  
##  <a name="push"></a>  priority_queue::push  
 Добавляет элемент в очередь с приоритетом на основе приоритета элемента из оператора operator<.  
  
```  
void push(const Type& val);
```  
  
### <a name="parameters"></a>Параметры  
 `val`  
 Элемент, добавляемый в верхнюю часть priority_queue.  
  
### <a name="remarks"></a>Примечания  
 Верхняя часть priority_queue — это позиция, занятая самым большим элементом в контейнере.  
  
### <a name="example"></a>Пример  
  
```cpp  
// pqueue_push.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   priority_queue<int> q1;  
  
   q1.push( 10 );  
   q1.push( 30 );  
   q1.push( 20 );  
  
   priority_queue<int>::size_type i;  
   i = q1.size( );  
   cout << "The priority_queue length is " << i << "." << endl;  
  
   const int& ii = q1.top( );  
   cout << "The element at the top of the priority_queue is "  
        << ii << "." << endl;  
}  
```  
  
```Output  
The priority_queue length is 3.  
The element at the top of the priority_queue is 30.  
```  
  
##  <a name="size"></a>  priority_queue::size  
 Возвращает количество элементов в priority_queue.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 Текущая длина priority_queue.  
  
### <a name="example"></a>Пример  
  
```cpp  
// pqueue_size.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   priority_queue <int> q1, q2;  
   priority_queue <int>::size_type i;  
  
   q1.push( 1 );  
   i = q1.size( );  
   cout << "The priority_queue length is " << i << "." << endl;  
  
   q1.push( 2 );  
   i = q1.size( );  
   cout << "The priority_queue length is now " << i << "." << endl;  
}  
```  
  
```Output  
The priority_queue length is 1.  
The priority_queue length is now 2.  
```  
  
##  <a name="size_type"></a>  priority_queue::size_type  
 Тип целого числа без знака, который может представлять количество элементов в priority_queue.  
  
```  
typedef typename Container::size_type size_type;  
```  
  
### <a name="remarks"></a>Примечания  
 Тип является синонимом `size_type` базового контейнера, измененного priority_queue.  
  
### <a name="example"></a>Пример  
  См. пример объявления и использования `size_type` в разделе [size](#size).  
  
##  <a name="top"></a>  priority_queue::top  
 Возвращает константную ссылку на наибольший элемент в верхней части priority_queue.  
  
```  
const_reference top() const;
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 Ссылка на самый большой элемент, как определено функцией **Traits**, объектом priority_queue.  
  
### <a name="remarks"></a>Примечания  
 Для применения функции-члена класс priority_queue не должен быть пустым.  
  
### <a name="example"></a>Пример  
  
```cpp  
// pqueue_top.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   priority_queue<int> q1;  
  
   q1.push( 10 );  
   q1.push( 30 );  
   q1.push( 20 );  
  
   priority_queue<int>::size_type i;  
   i = q1.size( );  
   cout << "The priority_queue length is " << i << "." << endl;  
  
   const int& ii = q1.top( );  
   cout << "The element at the top of the priority_queue is "  
        << ii << "." << endl;  
}  
```  
  
```Output  
The priority_queue length is 3.  
The element at the top of the priority_queue is 30.  
```  
  
##  <a name="value_type"></a>  priority_queue::value_type  
 Тип, представляющий тип объекта, который хранится в виде элемента в priority_queue.  
  
```  
typedef typename Container::value_type value_type;  
```  
  
### <a name="remarks"></a>Примечания  
 Тип является синонимом `value_type` базового контейнера, измененного priority_queue.  
  
### <a name="example"></a>Пример  
  
```cpp  
// pqueue_value_type.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares priority_queues with default deque base container  
   priority_queue<int>::value_type AnInt;  
  
   AnInt = 69;  
   cout << "The value_type is AnInt = " << AnInt << endl;  
  
   priority_queue<int> q1;  
   q1.push( AnInt );  
   cout << "The element at the top of the priority_queue is "  
        << q1.top( ) << "." << endl;  
}  
```  
  
```Output  
The value_type is AnInt = 69  
The element at the top of the priority_queue is 69.  
```  
  
## <a name="see-also"></a>См. также  
 [Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Справочник по стандартной библиотеке C++](../standard-library/cpp-standard-library-reference.md)

