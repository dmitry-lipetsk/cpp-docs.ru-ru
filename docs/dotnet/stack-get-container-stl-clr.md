---
title: "STACK::get_container (STL/CLR) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::stack::get_container
dev_langs: C++
helpviewer_keywords: get_container member [STL/CLR]
ms.assetid: ba6fc541-fc18-4d1c-8e3f-6baaed427cbb
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 721cd51a268a487e9fe18f988e98bfcf5e9d714b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="stackgetcontainer-stlclr"></a>stack::get_container (STL/CLR)
Обращается к базового контейнера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
container_type^ get_container();  
```  
  
## <a name="remarks"></a>Примечания  
 Функция-член возвращает дескриптор для базового контейнера. Используется для обхода ограничений, накладываемых на оболочку контейнера.  
  
## <a name="example"></a>Пример  
  
```  
// cliext_stack_get_container.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c" using container_type   
    Mystack::container_type wc1 = c1.get_container();   
    for each (wchar_t elem in wc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<cliext/stack >  
  
 **Пространство имен:** cliext  
  
## <a name="see-also"></a>См. также  
 [стек (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [stack::container_type (STL/CLR)](../dotnet/stack-container-type-stl-clr.md)