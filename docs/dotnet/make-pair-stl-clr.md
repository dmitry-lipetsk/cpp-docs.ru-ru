---
title: "make_pair (STL/CLR) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::make_pair
dev_langs: C++
helpviewer_keywords: make_pair function [STL/CLR]
ms.assetid: 74733f2c-97b0-4d69-b431-5ab8f0de9e3e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 34f86aefd9a7bad7b3b1f03f98d3df8965020e48
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="makepair-stlclr"></a>make_pair (STL/CLR)
Сделать `pair` из пары значений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
template<typename Value1,  
    typename Value2>  
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);  
```  
  
#### <a name="parameters"></a>Параметры  
 `Value1`  
 Тип упакованного значения первой.  
  
 `Value2`  
 Тип упакованного значение второго.  
  
 `first`  
 Первое значение программы-оболочки.  
  
 `second`  
 Второе значение для упаковки.  
  
## <a name="remarks"></a>Примечания  
 Эта функция шаблона возвращает `pair<Value1, Value2>(first, second)`. Можно использовать для создания `pair<Value1, Value2>` объекта из пары значений.  
  
## <a name="example"></a>Пример  
  
```cpp  
// cliext_make_pair.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    c1 = cliext::make_pair(L'y', 4);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[y, 4]  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<cliext/программа >  
  
 **Пространство имен:** cliext  
  
## <a name="see-also"></a>См. также  
 [range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)