---
title: "оператор = (deque) (STL/CLR) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::deque::operator=
dev_langs: C++
helpviewer_keywords: operator= member [STL/CLR]
ms.assetid: 0851c6e2-29a2-45da-8c5a-e0b2f5357fb6
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 86b4038011be918fe524536f83c96716a6656929
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="operator-deque-stlclr"></a>operator= (deque) (STL/CLR)
Заменяет управляемую последовательность.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
deque<Value>% operator=(deque<Value>% right);  
```  
  
#### <a name="parameters"></a>Параметры  
 right  
 Контейнер для копирования.  
  
## <a name="remarks"></a>Примечания  
 Копирует оператор член `right` объекту, затем возвращает `*this`. Он позволяет заменить управляемую последовательность копией управляемой последовательности в `right`.  
  
## <a name="example"></a>Пример  
  
```  
// cliext_deque_operator_as.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::deque<wchar_t> c2;   
    c2 = c1;   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<cliext/deque >  
  
 **Пространство имен:** cliext  
  
## <a name="see-also"></a>См. также  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::assign (STL/CLR)](../dotnet/deque-assign-stl-clr.md)