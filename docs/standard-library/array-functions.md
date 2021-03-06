---
title: "Функции &lt;array&gt; | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- array/std::array::get
- array/std::get
- array/std::swap
dev_langs: C++
ms.assetid: e0700a33-a833-4655-8735-16e71175efc8
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::array [C++], get
- std::get [C++]
- std::swap [C++]
ms.workload: cplusplus
ms.openlocfilehash: 7116d8bd3517bb412eecf4c0ba9040ce3fe0f7b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="ltarraygt-functions"></a>Функции &lt;array&gt;
Заголовок \<array> содержит две функции, не являющиеся членами, `get` и `swap`, которые работают с объектами `array`.  
  
|||  
|-|-|  
|[get](#get)|[swap](#swap)|  
  
##  <a name="get"></a>  get  
Возвращает ссылку на указанный элемент массива.  
  
```  
template <int Index, class T, size_t N>  
constexpr T& get(array<T, N>& arr) noexcept;  
 
template <int Index, class T, size_t N>  
constexpr const T& get(const array<T, N>& arr) noexcept;  
 
template <int Index, class T, size_t N>  
constexpr T&& get(array<T, N>&& arr) noexcept;  
```  
  
### <a name="parameters"></a>Параметры  
 `Index`  
 Смещение элемента.  
  
 `T`  
 Тип элемента.  
  
 `N`  
 Количество элементов в массиве.  
  
 `arr`  
 Массив для выбора элемента.  
  
### <a name="example"></a>Пример  
  
```cpp  
#include <array>   
#include <iostream>   
  
using namespace std;  
  
typedef array<int, 4> MyArray;  
  
int main()  
{  
    MyArray c0 { 0, 1, 2, 3 };  
  
    // display contents " 0 1 2 3"   
    for (const auto& e : c0)  
    {  
        cout << " " << e;  
    }  
    cout << endl;  
  
    // display odd elements " 1 3"   
    cout << " " << get<1>(c0);  
    cout << " " << get<3>(c0) << endl;  
}  
```  
  
```Output  
0 1 2 3  
1 3  
```  
  
##  <a name="swap"></a>  swap  
Не являющаяся членом специализация шаблона `std::swap`, которая меняет местами два объекта `array`.  
  
```  
template <class Ty, std::size_t N>  
void swap(array<Ty, N>& left, array<Ty, N>& right);
```  
  
### <a name="parameters"></a>Параметры  
 `Ty`  
 Тип элемента.  
  
 `N`  
 Размер массива.  
  
 `left`  
 Первый массив для обмена.  
  
 `right`  
 Второй массив для обмена.  
  
### <a name="remarks"></a>Примечания  
 Эта функция шаблона выполняет `left.swap(right)`.  
  
### <a name="example"></a>Пример  
  
```cpp  
// std__array__swap.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = { 4, 5, 6, 7 };
    c0.swap(c1);

    // display swapped contents " 4 5 6 7"   
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    swap(c0, c1);

    // display swapped contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
}
```  
  
```Output  
0 1 2 3  
4 5 6 7  
0 1 2 3  
```  
  
## <a name="see-also"></a>См. также  
 [\<array>](../standard-library/array.md)

