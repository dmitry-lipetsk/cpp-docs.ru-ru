---
title: "hash_multiset::value_comp (STL/CLR) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_multiset::value_comp
dev_langs: C++
helpviewer_keywords: value_comp member [STL/CLR]
ms.assetid: c5b25ded-9b27-43d5-9821-3f6e17338919
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c02798f74554c5d8ef9693800822a3c1f207ec2e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="hashmultisetvaluecomp-stlclr"></a>hash_multiset::value_comp (STL/CLR)
Копирует делегат упорядочения для значения двух элементов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
value_compare^ value_comp();  
```  
  
## <a name="remarks"></a>Примечания  
 Функция-член возвращает упорядочивания делегат, используемый для упорядочения управляемой последовательности. Используется для сравнения двух значений элемента.  
  
## <a name="example"></a>Пример  
  
```  
// cliext_hash_multiset_value_comp.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = True  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<cliext/hash_set >  
  
 **Пространство имен:** cliext  
  
## <a name="see-also"></a>См. также  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset::value_compare (STL/CLR)](../dotnet/hash-multiset-value-compare-stl-clr.md)   
 [hash_multiset::value_type (STL/CLR)](../dotnet/hash-multiset-value-type-stl-clr.md)