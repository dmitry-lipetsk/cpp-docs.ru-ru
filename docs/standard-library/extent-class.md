---
title: "Класс extent | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::extent
dev_langs: C++
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f7e6f8af90f3c31e2b72524ac2c31a9884e82448
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="extent-class"></a>Класс extent
Получает измерение массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
template <class Ty, unsigned I = 0>  
struct extent;  
```  
  
#### <a name="parameters"></a>Параметры  
 `Ty`  
 Запрашиваемый тип.  
  
 `I`  
 Массив, привязанный к запросу.  
  
## <a name="remarks"></a>Примечания  
 Если `Ty` является типом массива, который имеет по крайней мере `I` измерений, запрос типа содержит число элементов в измерении, заданное `I`. Если `Ty` не является типом массива или его ранг меньше `I` или если `I` равно нулю и `Ty` имеет тип "массив с неизвестной границей `U`, запрос типа содержит значение 0.  
  
## <a name="example"></a>Пример  
  
```cpp  
// std__type_traits__extent.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "extent 0 == "   
        << std::extent<int[5][10]>::value << std::endl;   
    std::cout << "extent 1 == "   
        << std::extent<int[5][10], 1>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
extent 0 == 5  
extent 1 == 10  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<type_traits>  
  
 **Пространство имен:** std  
  
## <a name="see-also"></a>См. также  
 [<type_traits>](../standard-library/type-traits.md)   
 [Класс remove_all_extents](../standard-library/remove-all-extents-class.md)   
 [Класс remove_extent](../standard-library/remove-extent-class.md)
