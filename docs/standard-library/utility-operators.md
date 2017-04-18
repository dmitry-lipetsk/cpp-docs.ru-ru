---
title: "Операторы &lt;utility&gt; | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6617109-2cec-4a69-948f-6c87116eda5f
caps.latest.revision: 13
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: ff42eebac50a016990a26dc358684dd70a33af84
ms.lasthandoff: 02/24/2017

---
# <a name="ltutilitygt-operators"></a>Операторы &lt;utility&gt;
||||  
|-|-|-|  
|[оператор!=](#operator_neq)|[оператор&gt;](#operator_gt_)|[оператор&gt;=](#operator_gt__eq)|  
|[оператор&lt;](#operator_lt_)|[оператор&lt;=](#operator_lt__eq)|[оператор==](#operator_eq_eq)|  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a>  оператор!=  
 Проверяет неравенство объекта pair слева от оператора объекту pair справа от оператора.  
  
```  
template <class Type>  
constexpr bool operator!=(const Type& left, const Type& right);

template <class T, class U>  
constexpr bool operator!=(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>Параметры  
 ` left`  
 Объект типа **pair**.  
  
 ` right`  
 Объект типа `pair`.  
  
### <a name="return-value"></a>Возвращаемое значение  
 **true**, если объекты pair не равны; в противном случае **false**.  
  
### <a name="remarks"></a>Примечания  
 Один объект pair равен другому объекту pair, если все их соответствующие элементы равны. Два объекта pair не равны, если первый или второй элемент одного объекта не равен соответствующему элементу другого.  
  
### <a name="example"></a>Пример  
  
```cpp  
// utility_op_ne.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3;  
  
   p1 = make_pair ( 10, 1.11e-1 );  
   p2 = make_pair ( 1000, 1.11e-3 );  
   p3 = make_pair ( 10, 1.11e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl << endl;  
  
   if ( p1 != p2 )  
      cout << "The pairs p1 and p2 are not equal." << endl;  
   else  
      cout << "The pairs p1 and p2 are equal." << endl;  
  
   if ( p1 != p3 )  
      cout << "The pairs p1 and p3 are not equal." << endl;  
   else  
      cout << "The pairs p1 and p3 are equal." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.111 ).  
The pair p2 is: ( 1000, 0.00111 ).  
The pair p3 is: ( 10, 0.111 ).  
  
The pairs p1 and p2 are not equal.  
The pairs p1 and p3 are equal.  
```  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a>  оператор==  
 Проверяет равенство объекта pair слева от оператора объекту pair справа от оператора.  
  
```  
template <class T, class U>  
constexpr bool operator==(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>Параметры  
 ` left`  
 Объект типа **pair**.  
  
 ` right`  
 Объект типа `pair`.  
  
### <a name="return-value"></a>Возвращаемое значение  
 **true**, если объекты pair равны; **false**, если объекты `pair` не равны.  
  
### <a name="remarks"></a>Примечания  
 Один объект pair равен другому объекту pair, если все их соответствующие элементы равны. Функция возвращает ` left`. **first** == ` right`. **first** && ` left`. **second** == ` right`. **second**. Два объекта pair не равны, если первый или второй элемент одного объекта не равен соответствующему элементу другого.  
  
### <a name="example"></a>Пример  
  
```cpp  
// utility_op_eq.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3;  
  
   p1 = make_pair ( 10, 1.11e-1 );  
   p2 = make_pair ( 1000, 1.11e-3 );  
   p3 = make_pair ( 10, 1.11e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl << endl;  
  
   if ( p1 == p2 )  
      cout << "The pairs p1 and p2 are equal." << endl;  
   else  
      cout << "The pairs p1 and p2 are not equal." << endl;  
  
   if ( p1 == p3 )  
      cout << "The pairs p1 and p3 are equal." << endl;  
   else  
      cout << "The pairs p1 and p3 are not equal." << endl;  
}  
```  
  
##  <a name="a-nameoperatorlta--operatorlt"></a><a name="operator_lt_"></a>  оператор&lt;  
 Проверяет, меньше ли объект pair слева от оператора объекта pair справа от оператора.  
  
```  
template <class T, class U>  
constexpr bool operator<(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>Параметры  
 ` left`  
 Объект типа `pair` в левой части оператора.  
  
 ` right`  
 Объект типа `pair` в правой части оператора.  
  
### <a name="return-value"></a>Возвращаемое значение  
 **true**, если `pair` слева от оператора строго меньше `pair` справа от оператора; в противном случае **false**.  
  
### <a name="remarks"></a>Примечания  
 Объект ` left``pair` строго меньше объекта ` right``pair`, если ` left` меньше и не равно ` right.`.  
  
 При сравнении объектов pair первые элементы значений двух объектов имеют самый высокий приоритет. Если они отличаются, результат их сравнения рассматривается как результат сравнения объектов pair. Если значения первых элементов совпадают, сравниваются значения вторых элементов и результат их сравнения рассматривается как результат сравнения объектов pair.  
  
### <a name="example"></a>Пример  
  
```cpp  
// utility_op_lt.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3;  
  
   p1 = make_pair ( 10, 2.22e-1 );  
   p2 = make_pair ( 100, 1.11e-1 );  
   p3 = make_pair ( 10, 1.11e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl << endl;  
  
   if ( p1 < p2 )  
      cout << "The pair p1 is less than the pair p2." << endl;  
   else  
      cout << "The pair p1 is not less than the pair p2." << endl;  
  
   if ( p1 < p3 )  
      cout << "The pair p1 is less than the pair p3." << endl;  
   else  
      cout << "The pair p1 is not less than the pair p3." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.222 ).  
The pair p2 is: ( 100, 0.111 ).  
The pair p3 is: ( 10, 0.111 ).  
  
The pair p1 is less than the pair p2.  
The pair p1 is not less than the pair p3.  
```  
  
##  <a name="a-nameoperatorlteqa--operatorlt"></a><a name="operator_lt__eq"></a>  оператор&lt;=  
 Проверяет, что объект pair слева от оператора меньше или равен объекту pair справа от оператора.  
  
```  
template <class Type>  
constexpr bool operator<=(const Type& left, const Type& right);

template <class T, class U>  
constexpr bool operator<=(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>Параметры  
 ` left`  
 Объект типа `pair` в левой части оператора.  
  
 ` right`  
 Объект типа `pair` в правой части оператора.  
  
### <a name="return-value"></a>Возвращаемое значение  
 **true**, если объект `pair` слева от оператора меньше или равен объекту `pair` справа от оператора; в противном случае **false**.  
  
### <a name="remarks"></a>Примечания  
 При сравнении объектов pair первые элементы значений двух объектов имеют самый высокий приоритет. Если они отличаются, результат их сравнения рассматривается как результат сравнения объектов pair. Если значения первых элементов совпадают, сравниваются значения вторых элементов и результат их сравнения рассматривается как результат сравнения объектов pair.  
  
### <a name="example"></a>Пример  
  
```cpp  
// utility_op_le.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3, p4;  
  
   p1 = make_pair ( 10, 2.22e-1 );  
   p2 = make_pair ( 100, 1.11e-1 );  
   p3 = make_pair ( 10, 1.11e-1 );  
   p4 = make_pair ( 10, 2.22e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl;  
   cout << "The pair p4 is: ( " << p4.first << ", "   
        << p4.second << " )." << endl << endl;  
  
   if ( p1 <= p2 )  
      cout << "The pair p1 is less than or equal to the pair p2." << endl;  
   else  
      cout << "The pair p1 is greater than the pair p2." << endl;  
  
   if ( p1 <= p3 )  
      cout << "The pair p1 is less than or equal to the pair p3." << endl;  
   else  
      cout << "The pair p1 is greater than the pair p3." << endl;  
  
   if ( p1 <= p4 )  
      cout << "The pair p1 is less than or equal to the pair p4." << endl;  
   else  
      cout << "The pair p1 is greater than the pair p4." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.222 ).  
The pair p2 is: ( 100, 0.111 ).  
The pair p3 is: ( 10, 0.111 ).  
The pair p4 is: ( 10, 0.222 ).  
  
The pair p1 is less than or equal to the pair p2.  
The pair p1 is greater than the pair p3.  
The pair p1 is less than or equal to the pair p4.  
```  
  
##  <a name="a-nameoperatorgta--operatorgt"></a><a name="operator_gt_"></a>  оператор&gt;  
 Проверяет, больше ли объект pair слева от оператора объекта pair справа от оператора.  
  
```  
template <class Type>  
constexpr bool operator>(const Type& left, const Type& right);

template <class T, class U>  
constexpr bool operator>(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>Параметры  
 ` left`  
 Объект типа `pair` в левой части оператора.  
  
 ` right`  
 Объект типа `pair` в правой части оператора.  
  
### <a name="return-value"></a>Возвращаемое значение  
 **true**, если `pair` слева от оператора больше `pair` справа от оператора; в противном случае **false**.  
  
### <a name="remarks"></a>Примечания  
 Объект ` left``pair` строго больше объекта ` right``pair`, если ` left` больше и не равно ` right.`.  
  
 При сравнении объектов pair первые элементы значений двух объектов имеют самый высокий приоритет. Если они отличаются, результат их сравнения рассматривается как результат сравнения объектов pair. Если значения первых элементов совпадают, сравниваются значения вторых элементов и результат их сравнения рассматривается как результат сравнения объектов pair.  
  
### <a name="example"></a>Пример  
  
```cpp  
// utility_op_gt.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3, p4;  
  
   p1 = make_pair ( 10, 2.22e-1 );  
   p2 = make_pair ( 100, 1.11e-1 );  
   p3 = make_pair ( 10, 1.11e-1 );  
   p4 = make_pair ( 10, 2.22e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl;  
   cout << "The pair p4 is: ( " << p4.first << ", "   
        << p4.second << " )." << endl << endl;  
  
   if ( p1 > p2 )  
      cout << "The pair p1 is greater than the pair p2." << endl;  
   else  
      cout << "The pair p1 is not greater than the pair p2." << endl;  
  
   if ( p1 > p3 )  
      cout << "The pair p1 is greater than the pair p3." << endl;  
   else  
      cout << "The pair p1 is not greater than the pair p3." << endl;  
  
   if ( p1 > p4 )  
      cout << "The pair p1 is greater than the pair p4." << endl;  
   else  
      cout << "The pair p1 is not greater than the pair p4." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.222 ).  
The pair p2 is: ( 100, 0.111 ).  
The pair p3 is: ( 10, 0.111 ).  
The pair p4 is: ( 10, 0.222 ).  
  
The pair p1 is not greater than the pair p2.  
The pair p1 is greater than the pair p3.  
The pair p1 is not greater than the pair p4.  
```  
  
##  <a name="a-nameoperatorgteqa--operatorgt"></a><a name="operator_gt__eq"></a>  оператор&gt;=  
 Проверяет, больше или равен ли объект pair слева от оператора объекту pair справа от оператора.  
  
```  
template <class Type>  
constexpr bool operator>=(const Type& left, const Type& right);

template <class T, class U>  
constexpr bool operator>=(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>Параметры  
 ` left`  
 Объект типа `pair` в левой части оператора.  
  
 ` right`  
 Объект типа `pair` в правой части оператора.  
  
### <a name="return-value"></a>Возвращаемое значение  
 **true**, если `pair` слева от оператора больше или равен `pair` справа от оператора; в противном случае **false**.  
  
### <a name="remarks"></a>Примечания  
 При сравнении объектов pair первые элементы значений двух объектов имеют самый высокий приоритет. Если они отличаются, результат их сравнения рассматривается как результат сравнения объектов pair. Если значения первых элементов совпадают, сравниваются значения вторых элементов и результат их сравнения рассматривается как результат сравнения объектов pair.  
  
### <a name="example"></a>Пример  
  
```cpp  
// utility_op_ge.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3, p4;  
  
   p1 = make_pair ( 10, 2.22e-1 );  
   p2 = make_pair ( 100, 1.11e-1 );  
   p3 = make_pair ( 10, 1.11e-1 );  
   p4 = make_pair ( 10, 2.22e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl;  
   cout << "The pair p4 is: ( " << p4.first << ", "   
        << p4.second << " )." << endl << endl;  
  
   if ( p1 >= p2 )  
      cout << "Pair p1 is greater than or equal to pair p2." << endl;  
   else  
      cout << "The pair p1 is less than the pair p2." << endl;  
  
   if ( p1 >= p3 )  
      cout << "Pair p1 is greater than or equal to pair p3." << endl;  
   else  
      cout << "The pair p1 is less than the pair p3." << endl;  
  
   if ( p1 >= p4 )  
      cout << "Pair p1 is greater than or equal to pair p4." << endl;  
   else  
      cout << "The pair p1 is less than the pair p4." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.222 ).  
The pair p2 is: ( 100, 0.111 ).  
The pair p3 is: ( 10, 0.111 ).  
The pair p4 is: ( 10, 0.222 ).  
  
The pair p1 is less than the pair p2.  
Pair p1 is greater than or equal to pair p3.  
Pair p1 is greater than or equal to pair p4.  
```  
  
## <a name="see-also"></a>См. также  
 [\<utility>](../standard-library/utility.md)

