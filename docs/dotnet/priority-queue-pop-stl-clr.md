---
title: "priority_queue::POP (STL/CLR) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::priority_queue::pop
dev_langs: C++
helpviewer_keywords: pop member [STL/CLR]
ms.assetid: d363b3f1-247b-466a-a300-c5918b0dfd4e
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6894a4acff991b069f7c5b587fd8a90c5a3a40ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="priorityqueuepop-stlclr"></a>priority_queue::pop (STL/CLR)
Удаляет элемент с наибольшим proirity.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
void pop();  
```  
  
## <a name="remarks"></a>Примечания  
 Функция-член удаляет элемент управляемой последовательности, который должен быть непустой наивысший приоритет. Используется для сокращения очереди на один элемент в обратной.  
  
## <a name="example"></a>Пример  
  
```  
// cliext_priority_queue_pop.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop();   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c a b  
b a  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<cliext/очереди >  
  
 **Пространство имен:** cliext  
  
## <a name="see-also"></a>См. также  
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [priority_queue::push (STL/CLR)](../dotnet/priority-queue-push-stl-clr.md)