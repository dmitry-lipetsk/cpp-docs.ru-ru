---
title: "deque::Clear (STL/CLR) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::deque::clear
dev_langs: C++
helpviewer_keywords: clear member [STL/CLR]
ms.assetid: 1d9a3d11-b3fa-43a7-a508-7a05cbcd91bf
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 74ab0cb7bc84a5d6959989bacd52509d6eb639ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="dequeclear-stlclr"></a>deque::clear (STL/CLR)
Удаляет все элементы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
void clear();  
```  
  
## <a name="remarks"></a>Примечания  
 Функция-член вызывает [deque::erase (STL/CLR)](../dotnet/deque-erase-stl-clr.md) `(` [deque::begin (STL/CLR)](../dotnet/deque-begin-stl-clr.md) `(),` [deque::end (STL/CLR)](../dotnet/deque-end-stl-clr.md) `())`. Используется, чтобы обеспечить пустой управляемой последовательности.  
  
## <a name="example"></a>Пример  
  
```  
// cliext_deque_clear.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 0  
 a b  
size() = 0  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<cliext/deque >  
  
 **Пространство имен:** cliext  
  
## <a name="see-also"></a>См. также  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::erase (STL/CLR)](../dotnet/deque-erase-stl-clr.md)