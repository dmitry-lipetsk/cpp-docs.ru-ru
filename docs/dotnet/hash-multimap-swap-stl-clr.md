---
title: "hash_multimap::Swap (STL/CLR) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_multimap::swap
dev_langs: C++
helpviewer_keywords: swap member [STL/CLR]
ms.assetid: 4baa60c2-865a-4e17-acd5-01b7c3c5cd44
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 56dde93cc7a2a2f18c26656e445a4b5b68f589bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="hashmultimapswap-stlclr"></a>hash_multimap::swap (STL/CLR)
Меняет местами содержимое двух контейнеров.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
void swap(hash_multimap<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Параметры  
 right  
 Контейнер для обмена содержимым.  
  
## <a name="remarks"></a>Примечания  
 Функция-член меняет местами управляемые последовательности между `this` и `right`. Она делает это в константном времени, и он не создает исключений. Используется в качестве быстро меняет местами содержимое двух контейнеров.  
  
## <a name="example"></a>Пример  
  
```  
// cliext_hash_multimap_swap.cpp   
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
  
// construct another container with repetition of values   
    Myhash_multimap c2;   
    c2.insert(Myhash_multimap::make_value(L'd', 4));   
    c2.insert(Myhash_multimap::make_value(L'e', 5));   
    c2.insert(Myhash_multimap::make_value(L'f', 6));   
    for each (Myhash_multimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    for each (Myhash_multimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[d 4] [e 5] [f 6]  
[d 4] [e 5] [f 6]  
[a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<cliext/hash_map >  
  
 **Пространство имен:** cliext  
  
## <a name="see-also"></a>См. также  
 [hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)   
 [hash_multimap::operator= (STL/CLR)](../dotnet/hash-multimap-operator-assign-stl-clr.md)