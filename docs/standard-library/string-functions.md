---
title: "Функции &lt;string&gt; | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a4ffd11-dce5-4cc6-a043-b95de034c7c4
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 31a7a65ed759ec552e11f2eccc5d425c2b2b765d
ms.openlocfilehash: 854a186c41a5a48c11d94796f06ef8fb200413e6
ms.lasthandoff: 02/24/2017

---
# <a name="ltstringgt-functions"></a>Функции &lt;string&gt;
||||  
|-|-|-|  
|[getline](#getline)|[stod](#stod)|[stof](#stof)|  
|[stoi](#stoi)|[stol](#stol)|[stold](#stold)|  
|[stoll](#stoll)|[stoul](#stoul)|[stoull](#stoull)|  
|[swap](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|  
  
##  <a name="a-namegetlinea--getline"></a><a name="getline"></a>  getline  
 Извлекает строки из входного потока, последовательно по одной строке.  
  
```  
// (1) delimiter as parameter  
template <class CharType, class Traits, class Allocator>  
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& is,  
    basic_string<CharType, Traits, Allocator>& str, 
    CharType delim);

 
template <class CharType, class Traits, class Allocator>  
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>&& is,  
    basic_string<CharType, Traits, Allocator>& str, 
    const CharType delim);

 
// (2) default delimiter used  
template <class CharType, class Traits, class Allocator>  
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& is,  
    basic_string<CharType, Traits, Allocator>& str);

 
template <class Allocator, class Traits, class Allocator>  
basic_istream<Allocator, Traits>& getline(
    basic_istream<Allocator, Traits>&& is,  
    basic_string<Allocator, Traits, Allocator>& str);
```  
  
### <a name="parameters"></a>Параметры  
 `is`  
 Входной поток, из которого извлекается строка.  
  
 `str`  
 Строка, в которую считываются символы из входного потока.  
  
 `delim`  
 Разделитель строк.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Входной поток `is`.  
  
### <a name="remarks"></a>Примечания  
 Пара подписей функций, обозначенных как `(1)`, извлекает символы из `is` до обнаружения `delim` и сохраняет их в `str`.  
  
 Пара подписей функций, обозначенных как `(2)`, использует символ новой строки в качестве разделителя по умолчанию и работает как **getline**( `is`, `str`, `is`. `widen`(' `\n`')).  
  
 Вторая функция каждой пары аналогична первой и поддерживает [ссылки rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md).  
  
 Извлечение останавливается при возникновении одного из следующих условий.  
  
-   В конце файла, в этом случае внутренний флаг состояния `is` устанавливается равным `ios_base::eofbit`.  
  
-   После извлечения элемента функция сравнивает его с **delim**, и в этом случае элемент не откладывается и не присоединяется к управляемой последовательности.  
  
-   Затем функция извлекает `str.`[max_size](../standard-library/basic-string-class.md#basic_string__max_size) элементов, в этом случае для внутреннего флага состояния `is` устанавливается значение `ios_base::failbit`.  
  
-   Некоторые прочие ошибки, отличные от перечисленных ранее, вследствие которых внутренний флаг состояния `is` устанавливается равным `ios_base::badbit`.  
  
 Сведения о внутренних флагах состояния см. в разделе [ios_base::iostate](../standard-library/ios-base-class.md#ios_base__iostate).  
  
 Если функция не извлекает никаких элементов, для внутреннего флага `is` устанавливается значение `ios_base::failbit`. Во всех случаях `getline` возвращает `is`.  
  
 При возникновении исключения `is` и `str` остаются в допустимом состоянии.  
  
### <a name="example"></a>Пример  
  Следующий код демонстрирует `getline()` в двух режимах: в первом с разделителем — символом новой строки (по умолчанию), во втором с разделителем — пробелом. Символ конца файла (CTRL-Z на клавиатуре) используется для управления завершением циклов while. При этом внутренний флаг состояния `cin` устанавливается в значение `eofbit`, которое необходимо очистить с помощью [basic_ios::clear()](../standard-library/basic-ios-class.md#basic_ios__clear), чтобы второй цикл while мог правильно работать.  
  
```cpp  
// compile with: /EHsc /W4  
#include <string>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
int main()  
{  
    string str;  
    vector<string> v1;  
    cout << "Enter a sentence, press ENTER between sentences. (Ctrl-Z to stop): " << endl;  
    // Loop until end-of-file (Ctrl-Z) is input, store each sentence in a vector.  
    // Default delimiter is the newline character.  
    while (getline(cin, str)) {  
        v1.push_back(str);  
    }  
  
    cout << "The following input was stored with newline delimiter:" << endl;  
    for (const auto& p : v1) {  
        cout << p << endl;  
    }  
  
    cin.clear();  
  
    vector<string> v2;  
    // Now try it with a whitespace delimiter  
    while (getline(cin, str, ' ')) {  
        v2.push_back(str);  
    }  
  
    cout << "The following input was stored with whitespace as delimiter:" << endl;  
    for (const auto& p : v2) {  
        cout << p << endl;  
    }  
}  
  
```  
  
##  <a name="a-namestoda--stod"></a><a name="stod"></a>  stod  
 Преобразует последовательность символов в `double`.  
  
```  
double stod(
    const string& str,   
    size_t* Idx = 0);

double stod(
    const wstring& str,   
    size_t* Idx = 0  
;  
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|` str`|Последовательность символов для преобразования.|  
|`Idx`|Значение индекса первого непреобразованного символа.|  
  
### <a name="return-value"></a>Возвращаемое значение  
 Значение `double`.  
  
### <a name="remarks"></a>Примечания  
 Функция преобразует последовательность элементов в ` str` в значение ` val` типа `double`, как при вызове `strtod( str.c_str(), _Eptr)`, где `_Eptr` является объектов, внутренним по отношению к функции. Если ` str.c_str() == *_Eptr`, то создается объект типа `invalid_argument`. Если такой вызов задает `errno`, то создается объект типа `out_of_range`. В противном случае, если `Idx` не является пустым указателем, функция сохраняет `*_Eptr -  str.c_str()` в `*Idx` и возвращает ` val`.  
  
##  <a name="a-namestofa--stof"></a><a name="stof"></a>  stof  
 Преобразует последовательность символов в число с плавающей запятой.  
  
```  
float stof(
    const string& str,   
    size_t* Idx = 0);

float stof(
    const wstring& str,   
    size_t* Idx = 0);
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|` str`|Последовательность символов для преобразования.|  
|`Idx`|Значение индекса первого непреобразованного символа.|  
  
### <a name="return-value"></a>Возвращаемое значение  
 Значение с плавающей запятой.  
  
### <a name="remarks"></a>Примечания  
 Функция преобразует последовательность элементов в ` str` в значение ` val` типа `float`, как при вызове `strtof( str.c_str(), _Eptr)`, где `_Eptr` является объектов, внутренним по отношению к функции. Если ` str.c_str() == *_Eptr`, то создается объект типа `invalid_argument`. Если такой вызов задает `errno`, то создается объект типа `out_of_range`. В противном случае, если `Idx` не является пустым указателем, функция сохраняет `*_Eptr -  str.c_str()` в `*Idx` и возвращает ` val`.  
  
##  <a name="a-namestoia--stoi"></a><a name="stoi"></a>  stoi  
 Преобразует последовательность символов в целое число.  
  
```  
int stoi(
    const string& str,   
    size_t* Idx = 0,  
    int Idx = 10);

int stoi(
    const wstring& str,   
    size_t* Idx = 0,  
    int Idx = 10);
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 Целочисленное значение.  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|` str`|Последовательность символов для преобразования.|  
|`Idx`|Содержит индекс первого возвращенного непреобразованного символа.|  
|`Idx`|Используемое числовое основание.|  
  
### <a name="remarks"></a>Примечания  
 Функция `stoi` преобразует последовательность элементов в ` str` в значение типа `int` и возвращает это значение. Например, если передать последовательность символов "10", `stoi` возвращает целочисленное значение 10.  
  
 `stoi` работает аналогично функции `strtol` для однобайтовых символов при вызове `strtol( str.c_str(), _Eptr, Idx)`, где `_Eptr` — внутренний объект функции; или `wcstol` для двухбайтовых символов при вызове `wcstol(Str.c_str(), _Eptr, Idx)`. Дополнительные сведения см. в разделе [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md).  
  
 Если ` str.c_str() == *_Eptr,``stoi` создает объект типа `invalid_argument`. Если такой вызов задает `errno` или если возвращаемое значение не может быть представлено в виде объекта типа `int`, создается объект типа `out_of_range`. В противном случае, если `Idx` не является пустым указателем, функция сохраняет `*_Eptr - _ str.c_str()` в `*Idx`.  
  
##  <a name="a-namestola--stol"></a><a name="stol"></a>  stol  
 Преобразует последовательность символов в `long`.  
  
```  
long stol(
    const string& str,  
    size_t* Idx = 0,  
    int Idx = 10);

long stol(
    const wstring& str,   
    size_t* Idx = 0,  
    int Idx = 10);
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|` str`|Последовательность символов для преобразования.|  
|`Idx`|Значение индекса первого непреобразованного символа.|  
|`Idx`|Используемое числовое основание.|  
  
### <a name="return-value"></a>Возвращаемое значение  
 Длинное целое значение.  
  
### <a name="remarks"></a>Примечания  
 Функция преобразует последовательность элементов в ` str` в значение ` val` типа `long`, как при вызове `strtol( str.c_str(), _Eptr, Idx)`, где `_Eptr` является объектов, внутренним по отношению к функции. Если ` str.c_str() == *_Eptr`, то создается объект типа `invalid_argument`. Если такой вызов задает `errno`, то создается объект типа `out_of_range`. В противном случае, если `Idx` не является пустым указателем, функция сохраняет `*_Eptr -  str.c_str()` в `*Idx` и возвращает ` val`.  
  
##  <a name="a-namestolda--stold"></a><a name="stold"></a>  stold  
 Преобразует последовательность символов в `long double`.  
  
```  
double stold(
    const string& str,   
    size_t* Idx = 0);

double stold(
    const wstring& str,   
    size_t* Idx = 0);
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|` str`|Последовательность символов для преобразования.|  
|`Idx`|Значение индекса первого непреобразованного символа.|  
  
### <a name="return-value"></a>Возвращаемое значение  
 Значение `long double`.  
  
### <a name="remarks"></a>Примечания  
 Функция преобразует последовательность элементов в ` str` в значение ` val` типа `long double`, как при вызове `strtold( str.c_str(), _Eptr)`, где `_Eptr` является объектов, внутренним по отношению к функции. Если ` str.c_str() == *_Eptr`, то создается объект типа `invalid_argument`. Если такой вызов задает `errno`, то создается объект типа `out_of_range`. В противном случае, если `Idx` не является пустым указателем, функция сохраняет `*_Eptr -  str.c_str()` в `*Idx` и возвращает ` val`.  
  
##  <a name="a-namestolla--stoll"></a><a name="stoll"></a>  stoll  
 Преобразует последовательность символов в `long long`.  
  
```  
long long stoll(
    const string& str,   
    size_t* Idx = 0,  
    int Idx = 10);

long long stoll(
    const wstring& str,   
    size_t* Idx = 0,  
    int Idx = 10);
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|` str`|Последовательность символов для преобразования.|  
|`Idx`|Значение индекса первого непреобразованного символа.|  
|`Idx`|Используемое числовое основание.|  
  
### <a name="return-value"></a>Возвращаемое значение  
 Значение `long long`.  
  
### <a name="remarks"></a>Примечания  
 Функция преобразует последовательность элементов в ` str` в значение ` val` типа `long long`, как при вызове `strtoll( str.c_str(), _Eptr, Idx)`, где `_Eptr` является объектов, внутренним по отношению к функции. Если ` str.c_str() == *_Eptr`, то создается объект типа `invalid_argument`. Если такой вызов задает `errno`, то создается объект типа `out_of_range`. В противном случае, если `Idx` не является пустым указателем, функция сохраняет `*_Eptr -  str.c_str()` в `*Idx` и возвращает ` val`.  
  
##  <a name="a-namestoula--stoul"></a><a name="stoul"></a>  stoul  
 Преобразует последовательность символов в длинное целое без знака.  
  
```  
unsigned long stoul(
    const string& str,   
    size_t* Idx = 0,  
    int Idx = 10);

unsigned long stoul(
    const wstring& str,   
    size_t* Idx = 0,  
    int Idx = 10);
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|` str`|Последовательность символов для преобразования.|  
|`Idx`|Значение индекса первого непреобразованного символа.|  
|`Idx`|Используемое числовое основание.|  
  
### <a name="return-value"></a>Возвращаемое значение  
 Длинное целое значение без знака.  
  
### <a name="remarks"></a>Примечания  
 Функция преобразует последовательность элементов в ` str` в значение ` val` типа `unsigned long`, как при вызове `strtoul( str.c_str(), _Eptr, Idx)`, где `_Eptr` является объектов, внутренним по отношению к функции. Если ` str.c_str() == *_Eptr`, то создается объект типа `invalid_argument`. Если такой вызов задает `errno`, то создается объект типа `out_of_range`. В противном случае, если `Idx` не является пустым указателем, функция сохраняет `*_Eptr -  str.c_str()` в `*Idx` и возвращает ` val`.  
  
##  <a name="a-namestoulla--stoull"></a><a name="stoull"></a>  stoull  
 Преобразует последовательность символов в `unsigned long long`.  
  
```  
unsigned long long stoull(
    const string& str,   
    size_t* Idx = 0,  
    int Idx = 10);

unsigned long long stoull(
    const wstring& str,   
    size_t* Idx = 0,  
    int Idx = 10);
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|` str`|Последовательность символов для преобразования.|  
|`Idx`|Значение индекса первого непреобразованного символа.|  
|`Idx`|Используемое числовое основание.|  
  
### <a name="return-value"></a>Возвращаемое значение  
 Значение `unsigned long long`.  
  
### <a name="remarks"></a>Примечания  
 Функция преобразует последовательность элементов в ` str` в значение ` val` типа `unsigned long long`, как при вызове `strtoull( str.c_str(), _Eptr, Idx)`, где `_Eptr` является объектов, внутренним по отношению к функции. Если ` str.c_str() == *_Eptr`, то создается объект типа `invalid_argument`. Если такой вызов задает `errno`, то создается объект типа `out_of_range`. В противном случае, если `Idx` не является пустым указателем, функция сохраняет `*_Eptr -  str.c_str()` в `*Idx` и возвращает ` val`.  
  
##  <a name="a-nameswapa--swap"></a><a name="swap"></a>  swap  
 Меняет местами массивы символов двух строк.  
  
```  
template <class Traits, class Allocator>  
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Параметры  
 ` left`  
 Одна строка, элементы которой будут заменены на элементы другой строки.  
  
 ` right`  
 Другая строка, элементы которой будут заменены на элементы первой строки.  
  
### <a name="remarks"></a>Примечания  
 Функция шаблона выполняет указанную функцию-член _ *Left*. [swap](../standard-library/basic-string-class.md#basic_string__swap)(\_ *Right*) для строк, что гарантирует постоянную сложность.  
  
### <a name="example"></a>Пример  
  
```cpp  
// string_swap.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   // Declaring an object of type basic_string<char>  
   string s1 ( "Tweedledee" );  
   string s2 ( "Tweedledum" );  
   cout << "Before swapping string s1 and s2:" << endl;  
   cout << "The basic_string s1 = " << s1 << "." << endl;  
   cout << "The basic_string s2 = " << s2 << "." << endl;  
  
   swap ( s1 , s2 );  
   cout << "\nAfter swapping string s1 and s2:" << endl;  
   cout << "The basic_string s1 = " << s1 << "." << endl;  
   cout << "The basic_string s2 = " << s2 << "." << endl;  
}  
```  
  
```Output  
Before swapping string s1 and s2:  
The basic_string s1 = Tweedledee.  
The basic_string s2 = Tweedledum.  
  
After swapping string s1 and s2:  
The basic_string s1 = Tweedledum.  
The basic_string s2 = Tweedledee.  
```  
  
##  <a name="a-nametostringa--tostring"></a><a name="to_string"></a>  to_string  
 Преобразует значение в `string`.  
  
```  
string to_string(int Val);
string to_string(unsigned int Val);
string to_string(long Val);
string to_string(unsigned long Val);
string to_string(long long Val);
string to_string(unsigned long long Val);
string to_string(float Val);
string to_string(double Val);
string to_string(long double Val);
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`Val`|Преобразуемое значение.|  
  
### <a name="return-value"></a>Возвращаемое значение  
 Объект `string`, представляющий значение.  
  
### <a name="remarks"></a>Примечания  
 Эта функция преобразовывает `Val` в последовательность элементов, хранящихся в объекте массива `Buf`, размещенного внутри функции, как если бы выполнялся вызов `sprintf(Buf, Fmt, Val)`, где `Fmt` равняется  
  
- `"%d"`, если `Val` имеет тип `int`  
  
- `"%u"`, если `Val` имеет тип `unsigned int`  
  
- `"%ld"`, если `Val` имеет тип `long`  
  
- `"%lu"`, если `Val` имеет тип `unsigned long`  
  
- `"%lld"`, если `Val` имеет тип `long long`  
  
- `"%llu"`, если `Val` имеет тип `unsigned long long`  
  
- `"%f"`, если `Val` имеет тип `float` или `double`  
  
- `"%Lf"`, если `Val` имеет тип `long double`  
  
 Функция возвращает `string(Buf)`.  
  
##  <a name="a-nametowstringa--towstring"></a><a name="to_wstring"></a>  to_wstring  
 Преобразует значение в расширенную строку.  
  
```  
wstring to_wstring(int Val);
wstring to_wstring(unsigned int Val);
wstring to_wstring(long Val);
wstring to_wstring(unsigned long Val);
wstring to_wstring(long long Val);
wstring to_wstring(unsigned long long Val);
wstring to_wstring(float Val);
wstring to_wstring(double Val);
wstring to_wstring(long double Val);
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`Val`|Преобразуемое значение.|  
  
### <a name="return-value"></a>Возвращаемое значение  
 Расширенная строка, представляющая значение.  
  
### <a name="remarks"></a>Примечания  
 Эта функция преобразовывает `Val` в последовательность элементов, хранящихся в объекте массива `Buf`, размещенного внутри функции, как если бы выполнялся вызов `swprintf(Buf, Len, Fmt, Val)`, где `Fmt` равняется  
  
- `L"%d"`, если `Val` имеет тип `int`  
  
- `L"%u"`, если `Val` имеет тип `unsigned int`  
  
- `L"%ld"`, если `Val` имеет тип `long`  
  
- `L"%lu"`, если `Val` имеет тип `unsigned long`  
  
- `L"%lld"`, если `Val` имеет тип `long long`  
  
- `L"%llu"`, если `Val` имеет тип `unsigned long long`  
  
- `L"%f"`, если `Val` имеет тип `float` или `double`  
  
- `L"%Lf"`, если `Val` имеет тип `long double`  
  
 Функция возвращает `wstring(Buf)`.  
  
## <a name="see-also"></a>См. также  
 [\<string>](../standard-library/string.md)

