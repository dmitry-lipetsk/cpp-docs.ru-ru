---
title: "STACK::generic_container (STL/CLR) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::stack::generic_container
dev_langs: C++
helpviewer_keywords: generic_container member [STL/CLR]
ms.assetid: 00f106c4-2a02-41cd-80de-f413c9355c74
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bf2611401b60341bedf15fd38f85e1701482c9d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="stackgenericcontainer-stlclr"></a>stack::generic_container (STL/CLR)
Тип универсального интерфейса для адаптера контейнера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef Microsoft::VisualC::StlClr::IStack<Value>  
    generic_container;  
```  
  
## <a name="remarks"></a>Примечания  
 Тип, описывающий универсальный интерфейс для класса адаптера контейнера шаблона.  
  
## <a name="example"></a>Пример  
  
```  
// cliext_stack_generic_container.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get interface to container   
    Mystack::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->push(L'd');   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.push(L'e');   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a b c d  
a b c d e  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<cliext/stack >  
  
 **Пространство имен:** cliext  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualC.StlClr.IStack%602>   
 [стек (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [stack::generic_value (STL/CLR)](../dotnet/stack-generic-value-stl-clr.md)