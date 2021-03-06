---
title: "MULTISET::to_array (STL/CLR) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multiset::to_array
dev_langs: C++
helpviewer_keywords: to_array member [STL/CLR]
ms.assetid: 3ca4482d-2584-4a93-89b9-33ea29692de2
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b46ce18ed3726e1cb109a7ddd86207acdfba8977
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="multisettoarray-stlclr"></a>multiset::to_array (STL/CLR)
Копирует управляемой последовательности в новый массив.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
cli::array<value_type>^ to_array();  
```  
  
## <a name="remarks"></a>Примечания  
 Функция-член возвращает массив, содержащий управляемой последовательности. Используется для получения копии управляемой последовательности в виде массива.  
  
## <a name="example"></a>Пример  
  
```  
// cliext_multiset_to_array.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.insert(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c d  
a b c  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<cliext и set >  
  
 **Пространство имен:** cliext  
  
## <a name="see-also"></a>См. также  
 [multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)