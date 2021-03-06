---
title: "Класс istreambuf_iterator | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- streambuf/std::istreambuf_iterator
- iterator/std::istreambuf_iterator::char_type
- iterator/std::istreambuf_iterator::int_type
- iterator/std::istreambuf_iterator::istream_type
- iterator/std::istreambuf_iterator::streambuf_type
- iterator/std::istreambuf_iterator::traits_type
- iterator/std::istreambuf_iterator::equal
dev_langs: C++
helpviewer_keywords:
- std::istreambuf_iterator [C++]
- std::istreambuf_iterator [C++], char_type
- std::istreambuf_iterator [C++], int_type
- std::istreambuf_iterator [C++], istream_type
- std::istreambuf_iterator [C++], streambuf_type
- std::istreambuf_iterator [C++], traits_type
- std::istreambuf_iterator [C++], equal
ms.assetid: 39002da2-61a6-48a5-9d0c-5df8271f6038
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2334ebd75d3a941c453950a6a99adfd99e6b1555
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="istreambufiterator-class"></a>Класс istreambuf_iterator
Класс-шаблон istreambuf_iterator описывает объект итератора ввода, который извлекает элементы из буфера входного потока, доступ к которому он получает через хранимый в нем объект типа pointer, указывающий на `basic_streambuf`\< **CharType**, **Traits**>.  
  
## <a name="syntax"></a>Синтаксис  
  
```
template <class CharType class Traits = char_traits <CharType>>  
class istreambuf_iterator 
: public iterator<input_iterator_tag, CharType, typename Traits ::off_type, CharType*, CharType&>
```  
  
#### <a name="parameters"></a>Параметры  
 `CharType`  
 Тип, представляющий тип символа для istreambuf_iterator.  
  
 `Traits`  
 Тип, представляющий тип символа для istreambuf_iterator. Этот аргумент является необязательным, значение по умолчанию — `char_traits`\< *CharType>.*  
  
## <a name="remarks"></a>Примечания  
 Класс istreambuf_iterator должен удовлетворять требованиям для итератора ввода.  
  
 После создания или приращения объекта класса istreambuf_iterator с помощью сохраненного указателя, не содержащего null, объект фактически пытается извлечь и сохранить объект типа **CharType** из соответствующего входного потока. Однако извлечение может быть отложено, пока не будет фактически удалена ссылка объекта или он не будет скопирован. Если извлечение завершается ошибкой, этот объект фактически заменяет сохраненный указатель указателем null, тем самым создавая индикатор конца последовательности.  
  
### <a name="constructors"></a>Конструкторы  
  
|||  
|-|-|  
|[istreambuf_iterator](#istreambuf_iterator)|Создает объект `istreambuf_iterator`, инициализируемый для чтения символов из входного потока.|  
  
### <a name="typedefs"></a>Определения типов  
  
|||  
|-|-|  
|[char_type](#char_type)|Тип, обеспечивающий тип символа для `ostreambuf_iterator`.|  
|[int_type](#int_type)|Тип, предоставляющий целочисленный тип для `istreambuf_iterator`.|  
|[istream_type](#istream_type)|Тип, обеспечивающий тип потока для `istream_iterator`.|  
|[streambuf_type](#streambuf_type)|Тип, обеспечивающий тип потока для `istreambuf_iterator`.|  
|[traits_type](../standard-library/istream-iterator-class.md#traits_type)|Тип, обеспечивающий тип признаков символа для `istream_iterator`.|  
  
### <a name="member-functions"></a>Функции-члены  
  
|||  
|-|-|  
|[equal](#equal)|Тесты на равенство между двумя итераторами буфера входного потока.|  
  
### <a name="operators"></a>Операторы  
  
|||  
|-|-|  
|[оператор*](#op_star)|Оператор удаления ссылки возвращает следующий символ в потоке.|  
|[оператор++](#op_add_add)|Либо возвращает следующий символ из входного потока, либо копирует объект перед его увеличением и возвращает копию.|  
|[оператор>](#operator-_gt)|Возвращает значение члена при наличии.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<iterator>  
  
 **Пространство имен:** std  
  
##  <a name="char_type"></a>  istreambuf_iterator::char_type  
 Тип, обеспечивающий тип символа для `ostreambuf_iterator`.  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>Примечания  
 Тип является синонимом для параметра-шаблона **CharType**.  
  
### <a name="example"></a>Пример  
  
```cpp  
// istreambuf_iterator_char_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
  
   typedef istreambuf_iterator<char>::char_type CHT1;  
   typedef istreambuf_iterator<char>::traits_type CHTR1;  
  
   cout << "(Try the example: 'So many dots to be done'\n"  
        << " then an Enter key to insert into the output,\n"  
        << " & use a ctrl-Z Enter key combination to exit): ";  
  
   // istreambuf_iterator for input stream  
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );  
   ostreambuf_iterator<char> charOut ( cout );  
  
   // Used in conjunction with replace_copy algorithm  
   // to insert into output stream and replace spaces  
   // with dot-separators  
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),  
        charOut , ' ' , '.' );  
}  
```  
  
##  <a name="equal"></a>  istreambuf_iterator::equal  
 Тесты на равенство между двумя итераторами буфера входного потока.  
  
```
bool equal(const istreambuf_iterator<CharType, Traits>& right) const;
```  
  
### <a name="parameters"></a>Параметры  
 `right`  
 Итератор, для которого выполняется проверка на равенство.  
  
### <a name="return-value"></a>Возвращаемое значение  
 **true**, если оба `istreambuf_iterator` являются итераторами конца потока или если не один из них не является итератором конца потока; в противном случае **false**.  
  
### <a name="remarks"></a>Примечания  
 Диапазон определяется `istreambuf_iterator` до текущей позиции и итератора конца потока, но, так как все итераторы, не являющиеся итераторами конца потока, эквивалентны в рамках функции-члена **equal**, невозможно определить никакие поддиапазоны с помощью `istreambuf_iterator`. Операторы `==` и `!=` имеют одинаковую семантику.  
  
### <a name="example"></a>Пример  
  
```cpp  
// istreambuf_iterator_equal.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   cout << "(Try the example: 'Hello world!'\n"  
        << " then an Enter key to insert into the output,\n"  
        << " & use a ctrl-Z Enter key combination to exit): ";  
  
   istreambuf_iterator<char> charReadIn1 ( cin );  
   istreambuf_iterator<char> charReadIn2 ( cin );  
  
   bool b1 = charReadIn1.equal ( charReadIn2 );  
  
   if (b1)  
      cout << "The iterators are equal." << endl;  
   else  
      cout << "The iterators are not equal." << endl;  
}  
```  
  
##  <a name="int_type"></a>  istreambuf_iterator::int_type  
 Тип, предоставляющий целочисленный тип для `istreambuf_iterator`.  
  
```
typedef typename traits_type::int_type int_type;
```  
  
### <a name="remarks"></a>Примечания  
 Этот тип — синоним для **Traits::int_type**.  
  
### <a name="example"></a>Пример  
  
```cpp  
// istreambuf_iterator_int_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   istreambuf_iterator<char>::int_type inttype1 = 100;  
   cout << "The inttype1 = " << inttype1 << "." << endl;  
}  
\* Output:   
The inttype1 = 100.  
*\  
```  
  
##  <a name="istream_type"></a>  istreambuf_iterator::istream_type  
 Тип, обеспечивающий тип потока для `istreambuf_iterator`.  
  
```
typedef basic_istream<CharType, Traits> istream_type;
```  
  
### <a name="remarks"></a>Примечания  
 Тип является синонимом для `basic_istream`\< **CharType**, **Traits**>.  
  
### <a name="example"></a>Пример  
  См. раздел [istreambuf_iterator](#istreambuf_iterator) с примером объявления и использования `istream_type`.  
  
##  <a name="istreambuf_iterator"></a>  istreambuf_iterator::istreambuf_iterator  
 Создает istreambuf_iterator, инициализируемый для чтения символов из входного потока.  
  
```
istreambuf_iterator(streambuf_type* strbuf = 0) throw();
istreambuf_iterator(istream_type& _Istr) throw();
```  
  
### <a name="parameters"></a>Параметры  
 `strbuf`  
 Буфер входного потока, к которому присоединяется `istreambuf_iterator`.  
  
 `_Istr`  
 Входной поток, к которому присоединяется `istreambuf_iterator`.  
  
### <a name="remarks"></a>Примечания  
 Первый конструктор инициализирует указатель буфера входного потока значением `strbuf`. Второй конструктор инициализирует указатель буфера входного потока значением `_Istr`. `rdbuf`, а затем в конечном итоге пытается извлечь и сохранить объект типа **CharType**.  
  
### <a name="example"></a>Пример  
  
```cpp  
// istreambuf_iterator_istreambuf_iterator.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Following declarations will not compile:  
   istreambuf_iterator<char>::istream_type &istrm = cin;  
   istreambuf_iterator<char>::streambuf_type *strmbf = cin.rdbuf( );  
  
   cout << "(Try the example: 'Oh what a world!'\n"  
      << " then an Enter key to insert into the output,\n"  
      << " & use a ctrl-Z Enter key combination to exit): ";  
   istreambuf_iterator<char> charReadIn ( cin );  
   ostreambuf_iterator<char> charOut ( cout );  
  
   // Used in conjunction with replace_copy algorithm  
   // to insert into output stream and replace spaces  
   // with hyphen-separators  
   replace_copy ( charReadIn , istreambuf_iterator<char>( ),  
      charOut , ' ' , '-' );  
}  
```  
  
##  <a name="op_star"></a>  istreambuf_iterator::operator*  
 Оператор удаления ссылки возвращает следующий символ в потоке.  
  
```
CharType operator*() const;
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 Следующий символ в потоке.  
  
### <a name="example"></a>Пример  
  
```cpp  
// istreambuf_iterator_operator_deref.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   cout << "Type string of characters & enter to output it,\n"  
      << " with stream buffer iterators,(try: 'I'll be back.')\n"  
      << " repeat as many times as desired,\n"   
      << " then keystroke ctrl-Z Enter to exit program: ";  
   istreambuf_iterator<char> inpos ( cin );  
   istreambuf_iterator<char> endpos;  
   ostreambuf_iterator<char> outpos ( cout );  
   while ( inpos != endpos )  
   {  
 *outpos = *inpos;   //Put value of outpos equal to inpos  
      ++inpos;  
      ++outpos;  
   }  
}  
```  
  
##  <a name="op_add_add"></a>  istreambuf_iterator::operator++  
 Либо возвращает следующий символ из входного потока, либо копирует объект перед его увеличением и возвращает копию.  
  
```
istreambuf_iterator<CharType, Traits>& operator++();
istreambuf_iterator<CharType, Traits> operator++(int);
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 `istreambuf_iterator` или ссылка на `istreambuf_iterator`.  
  
### <a name="remarks"></a>Примечания  
 Первый оператор в конечном итоге пытается извлечь и сохранить объект типа **CharType** из соответствующего входного потока. Второй оператор создает копию объекта, выполняет приращение объекта, а затем возвращает копию.  
  
### <a name="example"></a>Пример  
  
```cpp  
// istreambuf_iterator_operator_incr.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   cout << "Type string of characters & enter to output it,\n"  
      << " with stream buffer iterators,(try: 'I'll be back.')\n"  
      << " repeat as many times as desired,\n"   
      << " then keystroke ctrl-Z Enter to exit program: ";  
   istreambuf_iterator<char> inpos ( cin );  
   istreambuf_iterator<char> endpos;  
   ostreambuf_iterator<char> outpos ( cout );  
   while ( inpos != endpos )  
   {  
 *outpos = *inpos;  
      ++inpos;   //Increment istreambuf_iterator  
      ++outpos;  
   }  
}  
```  
  
##  <a name="istreambuf_iterator__operator-_gt"></a>  istreambuf_iterator::operator-&gt;  
 Возвращает значение члена при наличии.  
  
```
const Elem* operator->() const;
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 Оператор возвращает **&\*\*this**.  
  
##  <a name="streambuf_type"></a>  istreambuf_iterator::streambuf_type  
 Тип, обеспечивающий тип потока для istreambuf_iterator.  
  
```
typedef basic_streambuf<CharType, Traits> streambuf_type;
```  
  
### <a name="remarks"></a>Примечания  
 Тип является синонимом для `basic_streambuf`\< **CharType**, **Traits**>.  
  
### <a name="example"></a>Пример  
  См. раздел [istreambuf_iterator](#istreambuf_iterator) с примером объявления и использования **istreambuf_type**.  
  
##  <a name="traits_type"></a>  istreambuf_iterator::traits_type  
 Тип, обеспечивающий тип признаков символа для `istream_iterator`.  
  
```
typedef Traits traits_type;
```  
  
### <a name="remarks"></a>Примечания  
 Этот тип является синонимом для параметра-шаблона **Traits**.  
  
### <a name="example"></a>Пример  
  
```cpp  
// istreambuf_iterator_traits_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
  
   typedef istreambuf_iterator<char>::char_type CHT1;  
   typedef istreambuf_iterator<char>::traits_type CHTR1;  
  
   cout << "(Try the example: 'So many dots to be done'\n"  
        << " then an Enter key to insert into the output,\n"  
        << " & use a ctrl-Z Enter key combination to exit): ";  
  
   // istreambuf_iterator for input stream  
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );  
   ostreambuf_iterator<char> charOut ( cout );  
  
   // Used in conjunction with replace_copy algorithm  
   // to insert into output stream and replace spaces  
   // with dot-separators  
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),  
        charOut , ' ' , '.' );  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Структура iterator](../standard-library/iterator-struct.md)   
 [\<iterator>](../standard-library/iterator.md)   
 [Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Справочник по стандартной библиотеке C++](../standard-library/cpp-standard-library-reference.md)



