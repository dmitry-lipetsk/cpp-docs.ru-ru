---
title: "__stdcall | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __stdcall_cpp
dev_langs: C++
helpviewer_keywords: __stdcall keyword [C++]
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ec45f93331178f62799fb826ff31dfb6e66c3337
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="stdcall"></a>__stdcall
**Блок, относящийся только к системам Microsoft**  
  
 Соглашение `__stdcall` используется для вызова функций API Win32. Вызываемый метод очищает стек, поэтому компилятор применяет **vararg** функции `__cdecl`. Для функций, использующих данное соглашение о вызовах, требуется прототип.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
return-type __stdcall function-name[(argument-list)]  
```  
  
## <a name="remarks"></a>Примечания  
 В следующем списке показана реализация этого соглашения о вызовах.  
  
|Элемент|Реализация|  
|-------------|--------------------|  
|Порядок передачи аргументов|Справа налево.|  
|Соглашение о передаче аргументов|По значению, кроме случаев передачи указателя или ссылочного типа.|  
|Обязанность по обслуживанию стека|Вызываемая функция извлекает свои аргументы из стека.|  
|Соглашение об оформлении имен|К имени добавляется префикс в виде символа подчеркивания (_). После имени добавляется знак @, за которым следует количество байтов (в десятичном представлении) в списке аргументов. Поэтому функция, объявленная как `int func( int a, double b )` декорируется следующим образом: `_func@12`|  
|Соглашение о преобразовании регистра|Нет|  
  
 [/Gz](../build/reference/gd-gr-gv-gz-calling-convention.md) указывает параметр компилятора `__stdcall` для всех функций, которые не были явно объявлены с разных соглашение о вызовах.  
  
 Функции, объявленные с помощью `__stdcall` модификатор возвращаемого значения так же, как функции, объявленные с помощью [__cdecl](../cpp/cdecl.md).  
  
 На процессорах ARM и 64-разрядных процессорах соглашение `__stdcall` принимается и игнорируется компилятором; по принятому соглашению в случае архитектуры ARM и 64-разрядной архитектуры аргументы по возможности передаются в регистрах, а остальные аргументы передаются в стеке.  
  
 Если используется внестрочное определение нестатической функции класса, то модификатор соглашения о вызовах не должен быть задан во внестрочном определении. То есть для нестатических методов-членов считается, что соглашение о вызовах, указанное во время объявления, было сделано в точке определения. Для приведенного ниже определения класса  
  
```cpp  
struct CMyClass {  
   void __stdcall mymethod();  
};  
```  
  
 this  
  
```cpp  
void CMyClass::mymethod() { return; }  
```  
  
 эквивалентно следующему  
  
```cpp  
void __stdcall CMyClass::mymethod() { return; }  
```  
  
## <a name="example"></a>Пример  
 В следующем примере использование __**stdcall** всех `WINAPI` типы функций, обрабатывается как стандартный вызов:  
  
```cpp  
// Example of the __stdcall keyword  
#define WINAPI __stdcall  
// Example of the __stdcall keyword on function pointer  
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
## <a name="see-also"></a>См. также  
 [Передача аргументов и соглашения об именовании](../cpp/argument-passing-and-naming-conventions.md)   
 [Ключевые слова](../cpp/keywords-cpp.md)