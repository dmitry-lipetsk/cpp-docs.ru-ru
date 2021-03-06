---
title: "bind1st (STL/CLR) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::bind1st
dev_langs: C++
helpviewer_keywords: bind1st function [STL/CLR]
ms.assetid: 03a04cef-60fb-4667-b22a-22a387adb028
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b17a2bdcfee80b027423c24a7a430095eed6297d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="bind1st-stlclr"></a>bind1st (STL/CLR)
Приводит к возникновению ошибки `binder1st` функтор и аргумента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
template<typename Fun,  
    typename Arg>  
    binder1st<Fun> bind1st(Fun% functor,  
        Arg left);  
```  
  
## <a name="template-parameters"></a>Параметры шаблона  
 Arg  
 Тип аргумента.  
  
 Fun  
 Тип функтора.  
  
## <a name="function-parameters"></a>Параметры функции  
 функтор  
 Функтор программы-оболочки.  
  
 left  
 Первый аргумент программы-оболочки.  
  
## <a name="remarks"></a>Примечания  
 Функция шаблона возвращает [binder1st (STL/CLR)](../dotnet/binder1st-stl-clr.md)`<Fun>(functor, left)`. Используется в качестве удобный способ заключать функтор два аргумента и первым аргументом в функтор один аргумент, который вызывает ее в качестве второго аргумента.  
  
## <a name="example"></a>Пример  
  
```  
// cliext_bind1st.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::minus<int> sub_op;   
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        subfrom3);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind1st(sub_op, 3));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
-1 0  
-1 0  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<cliext и функционального >  
  
 **Пространство имен:** cliext  
  
## <a name="see-also"></a>См. также  
 [binder1st (STL/CLR)](../dotnet/binder1st-stl-clr.md)