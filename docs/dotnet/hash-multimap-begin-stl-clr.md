---
title: "hash_multimap::begin (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multimap::begin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "begin - член [STL/CLR]"
ms.assetid: 7f8d51c1-8183-4dc1-9dfc-f58dbf594c42
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# hash_multimap::begin (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Задает начало управляемой последовательности.  
  
## Синтаксис  
  
```  
iterator begin();  
```  
  
## Заметки  
 Функция\-член возвращает двунаправленный итератор, обозначает первый элемент контролируемой последовательности или только за пределы пустой последовательности.  Используется для получения итератора, который задает начало управляемой последовательности с параметром `current`, однако в случае изменения длины управляемой последовательности его состояние может измениться.  
  
## Пример  
  
```  
// cliext_hash_multimap_begin.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
    Myhash_multimap c1;   
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myhash_multimap::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = [{0} {1}]",   
        it->first, it->second);   
    ++it;   
    System::Console::WriteLine("*++begin() = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
  **\[1\] \[2\] \[BC — 3\]**  
**\*begin\(\) \= \[1\]**  
**\*\+\+begin\(\) \= \[B 2\]**   
## Требования  
 **Заголовок:**\<cliext\/hash\_map\>  
  
 **Пространство имен:** cliext  
  
## См. также  
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multimap::end](../dotnet/hash-multimap-end-stl-clr.md)