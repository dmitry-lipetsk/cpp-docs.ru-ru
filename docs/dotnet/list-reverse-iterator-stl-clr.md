---
title: "List::reverse_iterator (STL/CLR) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::reverse_iterator
dev_langs: C++
helpviewer_keywords: reverse_iterator member [STL/CLR]
ms.assetid: 56853ed8-cb12-41d7-98b2-c511cd77945d
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 27d78fbd1679e025dedd3a6fbbde3631e00a67eb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="listreverseiterator-stlclr"></a>list::reverse_iterator (STL/CLR)
Тип обратного итератора для управляемой последовательности.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef T3 reverse_iterator;  
```  
  
## <a name="remarks"></a>Примечания  
 Тип описывает объект незаданного типа `T3` , можно использовать в качестве обратного итератора для управляемой последовательности.  
  
## <a name="example"></a>Пример  
  
```  
// cliext_list_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    rit = c1.rbegin();   
    *rit = L'x';   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
x b a  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<cliext/list >  
  
 **Пространство имен:** cliext  
  
## <a name="see-also"></a>См. также  
 [список (STL/CLR)](../dotnet/list-stl-clr.md)   
 [List::const_iterator (STL/CLR)](../dotnet/list-const-iterator-stl-clr.md)   
 [List::const_reverse_iterator (STL/CLR)](../dotnet/list-const-reverse-iterator-stl-clr.md)   
 [list::iterator (STL/CLR)](../dotnet/list-iterator-stl-clr.md)