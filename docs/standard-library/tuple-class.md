---
title: "Класс tuple | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tuple/std::tuple
- tuple/std::tuple::operator=
dev_langs: C++
helpviewer_keywords: tuple class
ms.assetid: c38749be-ae4d-41f3-98ea-6aa3250de9a3
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8c7776a19a934a03809bfeb9e1cad9d7cb572672
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="tuple-class"></a>Класс tuple
Создает последовательность элементов фиксированной длины.  
  
## <a name="syntax"></a>Синтаксис  
```  
class tuple {  
public:  
   tuple();
   explicit tuple(P1, P2, ..., PN); // 0 < N  
   tuple(const tuple&);
   template <class U1, class U2, ..., class UN>  
      tuple(const tuple<U1, U2, ..., UN>&);
   template <class U1, class U2>  
      tuple(const pair<U1, U2>&); // N == 2  

   void swap(tuple& right);
   tuple& operator=(const tuple&);
   template <class U1, class U2, ..., class UN>  
      tuple& operator=(const tuple<U1, U2, ..., UN>&);
   template <class U1, class U2>  
      tuple& operator=(const pair<U1, U2>&); // N == 2  
   };  
  
#### Parameters  
 `TN`  
 The type of the Nth tuple element.  
  
## Remarks  
 The template class describes an object that stores N objects of types `T1`, `T2`, ..., `TN`, respectively, where where `0 <= N <= Nmax`. The extent of a tuple instance `tuple<T1, T2, ..., TN>` is the number `N` of its template arguments. The index of the template argument `Ti` and of the corresponding stored value of that type is `i - 1`. Thus, while we number the types from 1 to N in this documentation, the corresponding index values range from 0 to N - 1.  
  
## Example  
  
```cpp  
// tuple.cpp  
// compile with: /EHsc  
  
#include <vector>  
#include <iomanip>  
#include <iostream>  
#include <tuple>  
#include <string>  
  
using namespace std;  
  
typedef tuple <int, double, string> ids;  
  
void print_ids(const ids& i)  
{  
   cout << "( "  
        << get<0>(i) << ", "   
        << get<1>(i) << ", "   
        << get<2>(i) << " )." << endl;  
}  
  
int main( )  
{  
   // Using the constructor to declare and initialize a tuple  
   ids p1(10, 1.1e-2, "one");  
  
   // Compare using the helper function to declare and initialize a tuple  
   ids p2;  
   p2 = make_tuple(10, 2.22e-1, "two");  
  
   // Making a copy of a tuple  
   ids p3(p1);  
  
   cout.precision(3);  
   cout << "The tuple p1 is: ( ";  
   print_ids(p1);  
   cout << "The tuple p2 is: ( ";  
   print_ids(p2);  
   cout << "The tuple p3 is: ( ";  
   print_ids(p3);  
  
   vector<ids> v;  
  
   v.push_back(p1);  
   v.push_back(p2);  
   v.push_back(make_tuple(3, 3.3e-2, "three"));  
  
   cout << "The tuples in the vector are" << endl;  
   for(vector<ids>::const_iterator i = v.begin(); i != v.end(); ++i)  
   {  
      print_ids(*i);  
   }  
}  
```  
  
```Output  
The tuple p1 is: ( 10, 0.011, one ).  
The tuple p2 is: ( 10, 0.222, two ).  
The tuple p3 is: ( 10, 0.011, one ).  
The tuples in the vector are  
( 10, 0.011, one ).  
( 10, 0.222, two ).  
( 3, 0.033, three ).  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<tuple>  
  
 **Пространство имен:** std  
  
##  <a name="op_eq"></a>  tuple::operator=  
 Назначает объект `tuple`.  
  
```  
tuple& operator=(const tuple& right);

template <class U1, class U2, ..., class UN>  
   tuple& operator=(const tuple<U1, U2, ..., UN>& right);

template <class U1, class U2>  
   tuple& operator=(const pair<U1, U2>& right); // N == 2  

tuple& operator=(tuple&& right);
   
template <class U1, class U2>  
   tuple& operator=(pair<U1, U2>&& right);
```  
  
### <a name="parameters"></a>Параметры  
 `UN`  
 Тип n-го скопированного элемента кортежа.  
  
 `right`  
 Кортеж, из которого выполняется копирование.  
  
### <a name="remarks"></a>Примечания  
 Первые два оператора-члена назначают элементы `right` соответствующим элементам `*this`. Третий оператор-член назначает `right.first` элементу с индексом 0 в `*this` и `right.second` — элементу с индексом 1. Все три оператора-члена возвращают значение `*this`.  
  
 Остальные операторы-члены являются аналогами более ранних версий, но с [деклараторами ссылок rvalue: &&](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
### <a name="example"></a>Пример  
  
```cpp  
// std__tuple__tuple_operator_as.cpp   
// compile with: /EHsc   
#include <tuple>   
#include <iostream>   
#include <utility>   
  
typedef std::tuple<int, double, int, double> Mytuple;   
int main()   
    {   
    Mytuple c0(0, 1, 2, 3);   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
    Mytuple c1;   
    c1 = c0;   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c1);   
    std::cout << " " << std::get<1>(c1);   
    std::cout << " " << std::get<2>(c1);   
    std::cout << " " << std::get<3>(c1);   
    std::cout << std::endl;   
  
    std::tuple<char, int> c2;   
    c2 = std::make_pair('x', 4);   
  
// display contents " x 4"   
    std::cout << " " << std::get<0>(c2);   
    std::cout << " " << std::get<1>(c2);   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
x 4  
```  
  
##  <a name="tuple_swap"></a>  tuple:swap  
 Обмен элементами между двумя кортежами.  
  
```  
template <class... Types>  
   void swap(tuple<Types...&> left, tuple<Types...&> right);
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`left`|Кортеж, элементы которого должны быть заменены элементами кортежа `right`.|  
|`right`|Кортеж, элементы которого должны быть заменены элементами кортежа `left`.|  
  
### <a name="remarks"></a>Примечания  
 Функция выполняет `left.swap(right)`.  
  
##  <a name="tuple"></a>  tuple::tuple  
 Создает объект `tuple`.  
  
```  
constexpr tuple();
explicit constexpr tuple(const Types&...); 
template <class... UTypes>   
   explicit constexpr tuple(UTypes&&...);
  
tuple(const tuple&) = default;  
tuple(tuple&&) = default;  
  
template <class... UTypes>  
   constexpr tuple(const tuple<UTypes...>&);
template <class... UTypes>  
   constexpr tuple(tuple<UTypes...>&&);
  
// only if sizeof...(Types) == 2  
template <class U1, class U2>   
   constexpr tuple(const pair<U1, U2>&);
template <class U1, class U2>  
   constexpr tuple(pair<U1, U2>&&);
```  
  
### <a name="parameters"></a>Параметры  
 `UN`  
 Тип n-го скопированного элемента кортежа.  
  
 `right`  
 Кортеж, из которого выполняется копирование.  
  
### <a name="remarks"></a>Примечания  
 Первый конструктор создает объект, элементы которого создаются по умолчанию.  
  
 Второй конструктор создает объект, элементы которого представляют собой копии, созданные из аргументов `P1`, `P2`, ..., `PN`, при этом каждый `Pi` инициализирует элемент с индексом `i - 1`.  
  
 Третий и четвертый конструкторы создают объект, элементы которого представляют собой копии, созданные на основе соответствующего элемента `right`.  
  
 Пятый конструктор создает объект, элемент которого с индексом 0 создан с копированием на основе `right.first`, а элемент с индексом 1 — создан копированием из `right.second`.  
  
 Остальные конструкторы являются аналогами более ранних версий, но с [декларатором ссылок Rvalue: &&](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
### <a name="example"></a>Пример  
  
```cpp  
// std__tuple__tuple_tuple.cpp   
// compile with: /EHsc   
#include <tuple>   
#include <iostream>   
#include <utility>   
  
typedef std::tuple<int, double, int, double> Mytuple;   
int main()   
    {   
    Mytuple c0(0, 1, 2, 3);   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
    Mytuple c1;   
    c1 = c0;   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c1);   
    std::cout << " " << std::get<1>(c1);   
    std::cout << " " << std::get<2>(c1);   
    std::cout << " " << std::get<3>(c1);   
    std::cout << std::endl;   
  
    std::tuple<char, int> c2(std::make_pair('x', 4));   
  
// display contents " x 4"   
    std::cout << " " << std::get<0>(c2);   
    std::cout << " " << std::get<1>(c2);   
    std::cout << std::endl;   
  
    Mytuple c3(c0);   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c3);   
    std::cout << " " << std::get<1>(c3);   
    std::cout << " " << std::get<2>(c3);   
    std::cout << " " << std::get<3>(c3);   
    std::cout << std::endl;   
  
    typedef std::tuple<int, float, int, float> Mytuple2;   
    Mytuple c4(Mytuple2(4, 5, 6, 7));   
  
// display contents " 4 5 6 7"   
    std::cout << " " << std::get<0>(c4);   
    std::cout << " " << std::get<1>(c4);   
    std::cout << " " << std::get<2>(c4);   
    std::cout << " " << std::get<3>(c4);   
    std::cout << std::endl;   
  
    return (0);   
    }  
```  
  
```Output  
 0 1 2 3  
 0 1 2 3  
 x 4  
 0 1 2 3  
 4 5 6 7  
```  
  
## <a name="see-also"></a>См. также  
 [\<tuple>](../standard-library/tuple.md)   
 [make_tuple](../standard-library/tuple-functions.md#make_tuple)

