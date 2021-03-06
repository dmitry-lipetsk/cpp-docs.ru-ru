---
title: "Класс ostreambuf_iterator | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- streambuf/std::ostreambuf_iterator
- iterator/std::ostreambuf_iterator::char_type
- iterator/std::ostreambuf_iterator::ostream_type
- iterator/std::ostreambuf_iterator::streambuf_type
- iterator/std::ostreambuf_iterator::traits_type
- iterator/std::ostreambuf_iterator::failed
dev_langs: C++
helpviewer_keywords:
- std::ostreambuf_iterator [C++]
- std::ostreambuf_iterator [C++], char_type
- std::ostreambuf_iterator [C++], ostream_type
- std::ostreambuf_iterator [C++], streambuf_type
- std::ostreambuf_iterator [C++], traits_type
- std::ostreambuf_iterator [C++], failed
ms.assetid: dad1e624-2f45-4e94-8887-a885e95f9071
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c94ed10a0b97820c5a787e4350d39dcf6286fee7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="ostreambufiterator-class"></a>Класс ostreambuf_iterator
Класс-шаблон ostreambuf_iterator описывает объект итератора вывода, записывающий последующие элементы символов в поток с оператором извлечения **operator>>**. `ostreambuf_iterator` отличаются от таковых [класса ostream_iterator](../standard-library/ostream-iterator-class.md) тем, что используют символы вместо универсального типа для типа объекта, вставляемого в поток вывода.  
  
## <a name="syntax"></a>Синтаксис  
  
```
template <class CharType = char class Traits = char_traits <CharType>>
```  
  
#### <a name="parameters"></a>Параметры  
 `CharType`  
 Тип, представляющий тип символа для ostreambuf_iterator. Этот аргумент является необязательным, и значением по умолчанию является `char`.  
  
 `Traits`  
 Тип, представляющий тип символа для ostreambuf_iterator. Этот аргумент является необязательным, значение по умолчанию — `char_traits`\< *CharType>.*  
  
## <a name="remarks"></a>Примечания  
 Класс ostreambuf_iterator должен удовлетворять требованиям для итератора вывода. Алгоритмы можно записывать непосредственно в потоки вывода с помощью `ostreambuf_iterator`. Данный класс предоставляет итератор потока низкого уровня, обеспечивающий доступ к необработанному (неотформатированному) потоку ввода-вывода в форме символов, а также возможность обхода буферизации и преобразования символов, связанных с итераторами потоков высокого уровня.  
  
### <a name="constructors"></a>Конструкторы  
  
|||  
|-|-|  
|[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)|Создает итератор `ostreambuf_iterator`, инициализированный для записи символов в поток вывода.|  
  
### <a name="typedefs"></a>Определения типов  
  
|||  
|-|-|  
|[char_type](#char_type)|Тип, обеспечивающий тип символа для `ostreambuf_iterator`.|  
|[ostream_type](#ostreambuf_iterator_ostream_type)|Тип, обеспечивающий тип потока для `ostream_iterator`.|  
|[streambuf_type](#streambuf_type)|Тип, обеспечивающий тип потока для `ostreambuf_iterator`.|  
|[traits_type](#traits_type)|Тип, обеспечивающий тип признаков символа для `ostream_iterator`.|  
  
### <a name="member-functions"></a>Функции-члены  
  
|||  
|-|-|  
|[failed](#failed)|Проверяет наличие ошибок вставки в буфер потока вывода.|  
  
### <a name="operators"></a>Операторы  
  
|||  
|-|-|  
|[оператор*](#op_star)|Оператор разыменования, используемый для реализации выражения итератора вывода * `i` = `x`.|  
|[оператор++](#op_add_add)|Нефункциональный оператор инкремента, возвращающий `ostreambuf_iterator`, обращающийся к тому же объекту, к которому он обращался до вызова операции.|  
|[оператор=](#op_eq)|Данный оператор вставляет символ в соответствующий буфер потока.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<iterator>  
  
 **Пространство имен:** std  
  
##  <a name="char_type"></a>  ostreambuf_iterator::char_type  
 Тип, обеспечивающий тип символа для `ostreambuf_iterator`.  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>Примечания  
 Тип является синонимом для параметра-шаблона **CharType**.  
  
### <a name="example"></a>Пример  
  
```cpp  
// ostreambuf_iterator_char_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   typedef ostreambuf_iterator<char>::char_type CHT1;  
   typedef ostreambuf_iterator<char>::traits_type CHTR1;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter:  
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output streambuf:  
   cout << "The characters written to the output stream\n"  
        << " by charOutBuf are: ";  
 *charOutBuf = 'O';  
   charOutBuf++;  
 *charOutBuf = 'U';  
   charOutBuf++;  
 *charOutBuf = 'T';  
   charOutBuf++;  
   cout << "." << endl;  
}  
\* Output:   
The characters written to the output stream  
 by charOutBuf are: OUT.  
*\  
```  
  
##  <a name="failed"></a>  ostreambuf_iterator::failed  
 Проверяет наличие ошибок вставки в буфер потока вывода.  
  
```
bool failed() const throw();
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 **true**, если ранее вставка в буфер потока вывода закончилась неудачно; в противном случае **false**.  
  
### <a name="remarks"></a>Примечания  
 Функция-член возвращает **true**, если в любом предыдущем использовании члена `operator=` вызов **subf**_-> `sputc` вернул **eof**.  
  
### <a name="example"></a>Пример  
  
```cpp  
// ostreambuf_iterator_failed.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   ostreambuf_iterator<char> charOut ( cout );  
  
 *charOut = 'a';  
   charOut ++;  
 *charOut  = 'b';  
   charOut ++;     
 *charOut = 'c';  
   cout << " are characters output individually." << endl;  
  
   bool b1 = charOut.failed ( );  
   if (b1)   
       cout << "At least one insertion failed." << endl;  
   else  
       cout << "No insertions failed." << endl;  
}  
\* Output:   
abc are characters output individually.  
No insertions failed.  
*\  
```  
  
##  <a name="op_star"></a>  ostreambuf_iterator::operator*  
 Нефункциональный оператор разыменования, используемый для реализации выражения итератора вывода \* *i* = *x*.  
  
```
ostreambuf_iterator<CharType, Traits>& operator*();
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 Объект-итератор ostreambuf.  
  
### <a name="remarks"></a>Примечания  
 Этот оператор работает только в выражении итератора вывода \* *i* = *x* для вывода символов в буфер потока. Применяется к итератору ostreambuf. Он возвращает итератор; **\*iter** возвращает **iter**,  
  
### <a name="example"></a>Пример  
  
```cpp  
// ostreambuf_iterator_op_deref.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter  
   ostreambuf_iterator<char> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output stream  
   cout << "Elements written to output stream:" << endl;  
 *charOutBuf = 'O';  
   charOutBuf++;   // no effect on iterator position  
 *charOutBuf = 'U';  
 *charOutBuf = 'T';  
}  
\* Output:   
Elements written to output stream:  
OUT  
*\  
```  
  
##  <a name="op_add_add"></a>  ostreambuf_iterator::operator++  
 Нефункциональный оператор приращения, который возвращает итератор ostream, обращающийся к тому же символу, к которому он обращался до вызова операции.  
  
```
ostreambuf_iterator<CharType, Traits>& operator++();
ostreambuf_iterator<CharType, Traits>& operator++(int);
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 Ссылка на изначально адресованный символ или на определенный в реализации объект, который можно преобразовать в `ostreambuf_iterator`\< **CharType**, **Traits**>.  
  
### <a name="remarks"></a>Примечания  
 Оператор используется для реализации выражения итератора вывода \* *i* = *x*.  
  
### <a name="example"></a>Пример  
  
```cpp  
// ostreambuf_iterator_op_incr.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter  
   ostreambuf_iterator<char> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output stream  
   cout << "Elements written to output stream:" << endl;  
 *charOutBuf = 'O';  
   charOutBuf++;      // No effect on iterator position  
 *charOutBuf = 'U';  
 *charOutBuf = 'T';     
}  
\* Output:   
Elements written to output stream:  
OUT  
*\  
```  
  
##  <a name="op_eq"></a>  ostreambuf_iterator::operator=  
 Данный оператор вставляет символ в соответствующий буфер потока.  
  
```
ostreambuf_iterator<CharType, Traits>& operator=(CharType _Char);
```  
  
### <a name="parameters"></a>Параметры  
 `_Char`  
 Символ для вставки в буфер потока.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Ссылка на символ, вставленный в буфер потока.  
  
### <a name="remarks"></a>Примечания  
 Оператор присваивания, используемый для реализации выражения итератора вывода \* *i* = *x* для записи в поток вывода.  
  
### <a name="example"></a>Пример  
  
```cpp  
// ostreambuf_iterator_op_assign.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter  
   ostreambuf_iterator<char> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output stream  
   cout << "Elements written to output stream:" << endl;  
 *charOutBuf = 'O';  
   charOutBuf++;      // No effect on iterator position  
 *charOutBuf = 'U';  
 *charOutBuf = 'T';     
}  
\* Output:   
Elements written to output stream:  
OUT  
*\  
```  
  
##  <a name="ostreambuf_iterator_ostreambuf_iterator"></a>  ostreambuf_iterator::ostreambuf_iterator  
 Создает итератор `ostreambuf_iterator`, инициализированный для записи символов в поток вывода.  
  
```
ostreambuf_iterator(streambuf_type* strbuf) throw();
ostreambuf_iterator(ostream_type& Ostr) throw();
```  
  
### <a name="parameters"></a>Параметры  
 `strbuf`  
 Выходной объект streambuf, используемый для инициализации указателя буфера потока вывода.  
  
 `Ostr`  
 Выходной объект stream, используемый для инициализации указателя буфера потока вывода.  
  
### <a name="remarks"></a>Примечания  
 Первый конструктор инициализирует указатель буфера потока вывода значением `strbuf`.  
  
 Второй конструктор инициализирует указатель буфера потока вывода значением `Ostr`. `rdbuf`. Сохраненный указатель не должен быть пустым указателем (NULL).  
  
### <a name="example"></a>Пример  
  
```cpp  
// ostreambuf_iteratorOstreambuf_iterator.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   ostreambuf_iterator<char> charOut ( cout );  
  
 *charOut = 'O';  
   charOut ++;  
 *charOut  = 'U';  
   charOut ++;     
 *charOut = 'T';  
   cout << " are characters output individually." << endl;  
  
   ostreambuf_iterator<char> strOut ( cout );  
   string str = "These characters are being written to the output stream.\n ";  
   copy ( str.begin ( ), str. end ( ), strOut );  
}  
\* Output:   
OUT are characters output individually.  
These characters are being written to the output stream.  
*\  
```  
  
##  <a name="ostreambuf_iterator_ostream_type"></a>  ostreambuf_iterator::ostream_type  
 Тип, обеспечивающий тип потока для `ostream_iterator`.  
  
```
typedef basicOstream<CharType, Traits> ostream_type;
```  
  
### <a name="remarks"></a>Примечания  
 Тип является синонимом для `basicOstream`\< **CharType**, **Traits**>  
  
### <a name="example"></a>Пример  
  См. раздел [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) с примером объявления и использования `ostream_type`.  
  
##  <a name="streambuf_type"></a>  ostreambuf_iterator::streambuf_type  
 Тип, обеспечивающий тип потока для `ostreambuf_iterator`.  
  
```
typedef basic_streambuf<CharType, Traits> streambuf_type;
```  
  
### <a name="remarks"></a>Примечания  
 Тип является синонимом`basic_streambuf`\< **CharType**, **Traits**>, класса потока для буферов ввода-вывода, который становится `streambuf` при специализации до символьного типа `char`.  
  
### <a name="example"></a>Пример  
  См. раздел [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) с примером объявления и использования `streambuf_type`.  
  
##  <a name="traits_type"></a>  ostreambuf_iterator::traits_type  
 Тип, обеспечивающий тип признаков символа для `ostream_iterator`.  
  
```
typedef Traits traits_type;
```  
  
### <a name="remarks"></a>Примечания  
 Этот тип является синонимом для параметра-шаблона **Traits**.  
  
### <a name="example"></a>Пример  
  
```cpp  
// ostreambuf_iterator_traits_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   typedef ostreambuf_iterator<char>::char_type CHT1;  
   typedef ostreambuf_iterator<char>::traits_type CHTR1;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter:  
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output streambuf:  
   cout << "The characters written to the output stream\n"  
        << " by charOutBuf are: ";  
 *charOutBuf = 'O';  
   charOutBuf++;  
 *charOutBuf = 'U';  
   charOutBuf++;  
 *charOutBuf = 'T';  
   charOutBuf++;  
   cout << "." << endl;  
}  
\* Output:   
The characters written to the output stream  
 by charOutBuf are: OUT.  
*\  
```  
  
## <a name="see-also"></a>См. также  
 [\<iterator>](../standard-library/iterator.md)   
 [Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Справочник по стандартной библиотеке C++](../standard-library/cpp-standard-library-reference.md)



