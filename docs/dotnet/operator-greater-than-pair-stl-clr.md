---
title: "оператор&gt; (пару) (STL/CLR) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::pair::operator>
dev_langs: C++
helpviewer_keywords: operator> member [STL/CLR]
ms.assetid: c392a696-3425-49c8-9ddf-be2f2d2dd42e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 32301bdb518b9bcf22f10d76de9a810d2d61ae6f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="operatorgt-pair-stlclr"></a>оператор&gt; (пару) (STL/CLR)
Пара больше сравнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator>(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Параметры  
 left  
 Левый пара для сравнения.  
  
 right  
 Правый пара для сравнения.  
  
## <a name="remarks"></a>Примечания  
 Функция оператор возвращает `right` `<` `left`. Можно использовать для тестирования ли `left` упорядочен после `right` при две пары, сравниваемые элемент элемент.  
  
## <a name="example"></a>Пример  
  
```  
// cliext_pair_operator_gt.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] > [x 3] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[x 4] > [x 3] is {0}",   
        c2 > c1);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] > [x 3] is False  
[x 4] > [x 3] is True  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<cliext/программа >  
  
 **Пространство имен:** cliext  
  
## <a name="see-also"></a>См. также  
 [пара (STL/CLR)](../dotnet/pair-stl-clr.md)   
 [оператор == (пару) (STL/CLR)](../dotnet/operator-equality-pair-stl-clr.md)   
 [оператор! = (пару) (STL/CLR)](../dotnet/operator-inequality-pair-stl-clr.md)   
 [оператор\< (пару) (STL/CLR)](../dotnet/operator-less-than-pair-stl-clr.md)   
 [оператор > = (пару) (STL/CLR)](../dotnet/operator-greater-or-equal-pair-stl-clr.md)   
 [operator<= (pair) (STL/CLR)](../dotnet/operator-less-or-equal-pair-stl-clr.md)