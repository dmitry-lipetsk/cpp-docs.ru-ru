---
title: "List::push_back (STL/CLR) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::push_back
dev_langs: C++
helpviewer_keywords: push_back member [STL/CLR]
ms.assetid: f2c70470-a899-4e5f-8f3e-b55d6a8bff0e
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 87908a4b0e54f764d52308b24ce5c78d41c6f3f8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="listpushback-stlclr"></a>list::push_back (STL/CLR)
Добавляет новый последний элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
void push_back(value_type val);  
```  
  
## <a name="remarks"></a>Примечания  
 Функция-член вставляет элемент со значением `val` на конец управляемой последовательности. Используется для добавления другого элемента в список.  
  
## <a name="example"></a>Пример  
  
```  
// cliext_list_push_back.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<cliext/list >  
  
 **Пространство имен:** cliext  
  
## <a name="see-also"></a>См. также  
 [список (STL/CLR)](../dotnet/list-stl-clr.md)   
 [List::pop_back (STL/CLR)](../dotnet/list-pop-back-stl-clr.md)   
 [List::pop_front (STL/CLR)](../dotnet/list-pop-front-stl-clr.md)   
 [list::push_front (STL/CLR)](../dotnet/list-push-front-stl-clr.md)