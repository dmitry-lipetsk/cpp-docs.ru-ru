---
title: "multimap::generic_reverse_iterator (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multimap::generic_reverse_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "generic_reverse_iterator - элемент [STL/CLR]"
ms.assetid: c84d2512-fb93-4dc6-bc24-5aaa4bbb04f0
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# multimap::generic_reverse_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Тип обратного итератора для использования с универсальным интерфейсом для контейнера.  
  
## Синтаксис  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseRandomAccessIterator<generic_value>  
    generic_reverse_iterator;  
```  
  
## Заметки  
 Описывает тип универсальный обратный итератор, который можно использовать с универсальным интерфейсом для этого класса контейнера шаблона.  
  
## Пример  
  
```  
// cliext_multimap_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymultimap::generic_container^ gc1 = %c1;   
    for each (Mymultimap::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Mymultimap::generic_reverse_iterator gcit = gc1->rbegin();   
    Mymultimap::generic_value gcval = *gcit;   
    System::Console::WriteLine(" [{0} {1}]", gcval->first, gcval->second);   
    return (0);   
    }  
  
```  
  
  **\[1\] \[2\] \[BC — 3\]**  
 **\[1\] \[2\] \[BC — 3\]**  
 **\[C — 3\]**   
## Требования  
 **Заголовок:**\<cliext\/map\>  
  
 **Пространство имен:** cliext  
  
## См. также  
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multimap::generic\_container](../dotnet/multimap-generic-container-stl-clr.md)   
 [multimap::generic\_iterator](../dotnet/multimap-generic-iterator-stl-clr.md)